# Minimal PostHog Tracking Plan

## Goal
Page views, tab navigation, and contact form submissions — deployed securely via GitHub Actions secrets.

## What Is Tracked
- **Page views** — automatic via PostHog `capture_pageview: true`
- **Page leaves** — automatic via PostHog `capture_pageleave: true`
- **Contact form submissions** — custom event `Contact Form Submitted` on `#contact-form` submit

## Architecture

### PostHog Script
`_includes/posthog.html` — included in `_layouts/default.html`. Initializes PostHog and attaches a submit listener to the contact form.

### Configuration
- `_config.yml` — PostHog defaults (disabled, empty API key)
- `_config_posthog.yml` — template for local development, git-tracked
- `_config_posthog_local.yml` — real credentials for local dev, git-ignored

### Local Development
```bash
cp _config_posthog.yml _config_posthog_local.yml
# Edit _config_posthog_local.yml with real credentials
bundle exec jekyll serve --config _config.yml,_config_posthog_local.yml
```

### Production Deployment
`.github/workflows/jekyll_deploy.yml` generates `_config_posthog.yml` from GitHub Actions secrets at build time.

### CI Validation
`.github/workflows/jekyll_build.yml` builds with a placeholder API key and verifies `posthog.init` appears in the output HTML.

## Setting Up GitHub Actions Secrets

### 1. Get PostHog Credentials
1. Log in to [PostHog](https://app.posthog.com)
2. Go to **Project Settings** (gear icon in the left sidebar)
3. Copy the **Project API Key** (starts with `phc_`)
4. Note the **Host URL** (typically `https://app.posthog.com`, or your self-hosted instance URL)

### 2. Add Secrets to GitHub Repository
1. Go to your repository on GitHub: `github.com/<org>/<repo>`
2. Navigate to **Settings** > **Secrets and variables** > **Actions**
3. Click **New repository secret** and add:

| Secret Name | Value |
|---|---|
| `POSTHOG_API_KEY` | Your project API key (e.g. `phc_abc123...`) |
| `POSTHOG_HOST` | Your PostHog host (e.g. `https://app.posthog.com`) |

4. Both secrets are referenced in `.github/workflows/jekyll_deploy.yml` during the build step

### 3. Verify
Push to `main` and confirm the deploy workflow succeeds. Check PostHog for incoming `$pageview` events from the production domain.

## Verification
1. **Local:** Run with local config, open dev tools, confirm `$pageview` events fire on navigation
2. **Form:** Submit contact form, confirm `Contact Form Submitted` event in PostHog
3. **CI:** Push to branch, verify build workflow passes including PostHog validation step
4. **Production:** After merge to main, verify events appear in PostHog dashboard
