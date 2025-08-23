# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Professional Jekyll website for **Mediationskanzlei Moltmann-Willisch**, a German mediation law firm run by Anne-Ruth Moltmann-Willisch, LL.M. (former Regional Court Judge turned mediator).

## Development Commands

### Local Development
```bash
# Install dependencies
bundle install

# Start development server
bundle exec jekyll serve

# Build for production
bundle exec jekyll build
```

### Content Management
- Blog posts: Add to `_posts/` with format `YYYY-MM-DD-title.md`
- Pages: Edit `.md` files in root directory
- Styles: Customize in `_sass/custom.scss`

## Architecture

### Tech Stack
- **Jekyll 4.3.2** - Static site generator
- **Minima theme** - Customized with brand colors
- **GitHub Pages** - Deployment via GitHub Actions
- **Netlify Forms** - Contact form handling
- **SCSS** - Custom responsive styling

### File Structure
```
├── _config.yml          # Jekyll configuration
├── _posts/              # Blog posts (Markdown)
├── _sass/custom.scss    # Brand styling (sage green/orange)
├── assets/css/style.scss # Main stylesheet
├── index.md             # Homepage with hero section
├── about.md             # Professional background
├── services.md          # Mediation services offered
├── contact.md           # Contact form + info
├── blog.html            # Blog listing page
└── privacy.md           # GDPR-compliant privacy policy
```

### Key Features
- **Professional design** with custom brand colors (PANTONE 4179 C sage green, PANTONE 804 C orange)
- **Responsive layout** for all devices
- **Contact form** with spam protection
- **Blog system** for sharing expertise
- **SEO optimization** with proper meta tags
- **Privacy compliance** for German market

### Brand Guidelines
- **Primary color**: `--brand-sage` (#9CAF88) - professional, trustworthy
- **Accent color**: `--brand-orange` (#E67E22) - warm, approachable  
- **Content**: German language, professional but accessible tone
- **Target audience**: Potential mediation clients (corporate, family, construction disputes)

### Specialization Areas
The website covers these practice areas:
- Gesellschaftsrecht (Corporate law)
- Bauen & Immobilien (Construction & Real Estate)
- Familie & Partnerschaft (Family & Partnership)
- Organisationen & Vereine (Organizations & Associations)
- Nachbarschaftsstreitigkeiten (Neighborhood Disputes)

## Deployment

- **GitHub Pages** with custom GitHub Actions workflow
- **Domain**: Configured for www.moltmann-willisch.de
- **SSL**: Automatically provided by GitHub Pages
- **Contact Forms**: Handled by Netlify (form endpoint in contact.md)

## Content Guidelines

When adding content:
- Use professional German language
- Focus on benefits of mediation over litigation
- Emphasize the lawyer's judicial background for credibility
- Include calls-to-action for consultations
- Maintain GDPR compliance in all forms and policies