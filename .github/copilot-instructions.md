# GitHub Copilot Instructions for China Travel Itinerary Website

## Project Context
This repository hosts a Jekyll-based website for a China travel itinerary. The website is deployed via GitHub Pages at: https://xyzopowa.github.io/china/

## Purpose
- Document travel itinerary for China 2026
- Main pages for major cities (Beijing, Xi'an, Chongqing, Yichang, etc.)
- Sub-pages for modular and optional activities in each city
- Allow flexible planning with optional/alternative activities

## Technical Stack
- **Framework**: Jekyll (latest version)
- **Theme**: Jekyll Documentation Theme (https://github.com/tomjoht/documentation-theme-jekyll)
- **Deployment**: GitHub Pages
- **Repository**: https://github.com/xyzopowa/china/

## Theme Information
The site uses the Jekyll Documentation Theme which provides:
- Multi-level sidebar navigation
- Professional documentation layout
- Search functionality
- Responsive design
- PDF generation capabilities (optional)

## Content Structure
- **Preparation**: Travel planning, visas, packing guides
- **Beijing**: Dongcheng District, Gubei Water Town, Mutianyu Great Wall, Chaoyang District
- **Xi'an**: Terracotta Army, Mt Huashan, Xi'an City attractions
- **Chongqing**: City exploration, hot pot, Yangtze cruises
- **Yichang**: Three Gorges Dam, river cruises
- Additional destinations can be added following the same pattern

## Navigation Structure
The sidebar navigation is controlled by `_data/sidebars/china_sidebar.yml`. Each destination has:
- An overview page
- Multiple sub-pages for specific attractions/activities
- Modular content that can be mixed and matched

## Development Guidelines
- Use Jekyll best practices for content organization
- Keep content modular and reusable
- All content pages are in `/pages/china/` directory
- Follow the page frontmatter template (see existing pages)
- Use relative links within content
- Maintain clear navigation between cities and activities
- Use front matter for metadata (dates, durations, costs, etc.)

## Build Commands
```bash
# Install dependencies
bundle install

# Serve locally (required for GitHub Pages compatibility)
bundle exec jekyll serve

# Build for production
JEKYLL_ENV=production bundle exec jekyll build
```

## Adding New Content
1. Create new page in `/pages/china/` with proper frontmatter
2. Add entry to `_data/sidebars/china_sidebar.yml`
3. Test locally before pushing
4. GitHub Pages auto-builds after push to main branch

## Important Files
- `_config.yml`: Site configuration
- `_data/sidebars/china_sidebar.yml`: Navigation structure
- `/pages/china/`: All destination content
- `index.md`: Homepage
- `Gemfile`: Ruby dependencies

## Content Guidelines
- Use descriptive page titles
- Include practical information (hours, prices, duration)
- Add tips and recommendations
- Use consistent formatting across pages
- Include internal links to related pages using `[text](permalink.html)` format
