# Mediationskanzlei Moltmann-Willisch Website

Professional website for Anne-Ruth Moltmann-Willisch's mediation practice, built with Jekyll and deployed on GitHub Pages.

## Tech Stack

- **Jekyll 4.3.2** - Static site generator
- **Minima theme** - Customized with brand styling
- **GitHub Pages** - Hosting via GitHub Actions
- **Netlify Forms** - Contact form handling
- **SCSS** - Custom responsive styling

## Local Development

Prerequisites: Ruby 3.1+, Bundler

```bash
bundle install
bundle exec jekyll serve
# Visit http://localhost:4000
```

## File Structure

```
├── _config.yml          # Jekyll configuration
├── _posts/              # Blog posts (YYYY-MM-DD-title.md)
├── _sass/custom.scss    # Brand styling
├── assets/css/style.scss # Main stylesheet
├── index.md             # Homepage
├── about.md             # About page
├── services.md          # Services page
├── contact.md           # Contact page with form
├── blog.html            # Blog listing
└── privacy.md           # Privacy policy (GDPR)
```

## Deployment

Automatically deployed to GitHub Pages on push to main via GitHub Actions. Domain: www.moltmann-willisch.de
