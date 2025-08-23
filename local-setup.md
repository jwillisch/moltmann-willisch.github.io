# Local Development Setup

## Prerequisites

The system currently has Ruby 2.6.10 installed. For optimal Jekyll development, we recommend:

### Option 1: Use rbenv (Recommended)
```bash
# Install rbenv
brew install rbenv

# Install Ruby 3.1
rbenv install 3.1.0
rbenv local 3.1.0

# Install dependencies
bundle install

# Run development server
bundle exec jekyll serve
```

### Option 2: Use Docker
```bash
# Create docker-compose.yml
cat > docker-compose.yml << 'EOF'
version: '3'
services:
  jekyll:
    image: jekyll/jekyll:4
    command: jekyll serve --watch --force_polling --host 0.0.0.0
    ports:
      - 4000:4000
    volumes:
      - .:/srv/jekyll
    environment:
      - JEKYLL_ENV=development
EOF

# Run with Docker
docker-compose up
```

## Verification

Once setup is complete, the website should be available at:
- Local: http://localhost:4000
- Network: http://0.0.0.0:4000 (if using Docker)

## File Watching

The development server will automatically rebuild when files change:
- Markdown content (pages and posts)
- SCSS files in `_sass/`
- Configuration in `_config.yml` (requires server restart)

## Common Issues

1. **Permission errors**: Use rbenv or Docker instead of system Ruby
2. **Port conflicts**: Change port with `--port 4001`
3. **Slow rebuilds**: Jekyll 4.0+ includes incremental builds by default

## GitHub Pages Testing

To test the exact GitHub Pages environment:
```bash
# Install github-pages gem
gem install github-pages

# Serve with GitHub Pages gem
github-pages serve
```