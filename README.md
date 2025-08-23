# Mediationskanzlei Moltmann-Willisch Website

This is the official website for Anne-Ruth Moltmann-Willisch's mediation practice, built with Jekyll and deployed on GitHub Pages.

## About the Practice

**Anne-Ruth Moltmann-Willisch, LL.M.**  
*Richterin am Landgericht a.D., Mediatorin*

Professional mediation and conflict resolution services specializing in:
- Corporate law disputes (Gesellschaftsrecht)
- Construction and real estate conflicts (Bauen & Immobilien)
- Family and partnership mediation (Familie & Partnerschaft)
- Organizational conflicts (Organisationen & Vereine)
- Neighborhood disputes (Nachbarschaftsstreitigkeiten)

## Website Features

- **Professional design** with custom brand colors (sage green & orange)
- **Responsive layout** optimized for all devices  
- **Contact form** with Netlify integration
- **Blog functionality** for sharing insights and expertise
- **SEO optimized** with proper meta tags and structured data
- **Privacy compliant** with GDPR-compliant privacy policy

## Technical Stack

- **Jekyll 4.3.2** - Static site generator
- **Minima theme** - Customized with brand colors and professional styling
- **GitHub Pages** - Hosting and deployment
- **Netlify Forms** - Contact form handling
- **SCSS** - Custom styling and responsive design

## Local Development

### Prerequisites
- Ruby 3.1 or higher
- Bundler gem

### Setup
1. Clone the repository
2. Install dependencies: `bundle install`
3. Run the development server: `bundle exec jekyll serve`
4. Visit `http://localhost:4000`

### File Structure
```
├── _config.yml          # Jekyll configuration
├── _posts/              # Blog posts
├── _sass/               # SCSS stylesheets
├── assets/css/          # Compiled CSS
├── external_resources/  # Project documentation
├── index.md             # Homepage
├── about.md             # About page
├── services.md          # Services page
├── contact.md           # Contact page with form
├── blog.html            # Blog listing page
└── privacy.md           # Privacy policy
```

## Deployment

The site is automatically deployed to GitHub Pages when changes are pushed to the main branch using GitHub Actions.

## Content Management

### Adding Blog Posts
Create new files in `_posts/` with the format: `YYYY-MM-DD-title.md`

Front matter example:
```yaml
---
layout: post
title: "Your Post Title"
date: 2024-11-01 10:00:00 +0100
categories: [mediation, recht]
tags: [mediation, konfliktlösung]
excerpt: "Brief description of the post..."
---
```

### Customizing Styles
Main styles are in `_sass/custom.scss` using CSS custom properties for easy brand color management:
- `--brand-sage`: #9CAF88 (primary brand color)
- `--brand-orange`: #E67E22 (accent color)

## Contact Information

**Anne-Ruth Moltmann-Willisch, LL.M.**  
E-Mail: ar.moltmannwillisch@gmail.com  
Telefon: +49 (0) 172 65 29 460  
Web: www.moltmann-willisch.de

## License

This website is created for a professional mediation practice. Please respect the privacy and professional nature of the content.