# GitHub Copilot Instructions for China Travel Itinerary Website

## Project Context
This repository hosts a Jekyll-based website for a China travel itinerary. The website is deployed via GitHub Pages at: https://xyzopowa.github.io/china/

## Purpose
- Document travel itinerary for China 2026
- Main pages for major regions/cities (Beijing, Xi'an, Shanghai, Chengdu, Chongqing, Guilin, Pingyao, Datong, Yichang)
- Sub-pages for modular and optional activities in each region
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

## Content Structure & Terminology

### Regions (First Level)
A "**region**" or "**big step**" refers to the first level of the site structure - major destinations in the travel itinerary:
- Beijing
- Pingyao
- Datong
- Xi'an
- Chengdu
- Chongqing
- Yichang
- Shanghai
- Guilin

### Destinations/Spots (Second Level)
"**Destinations**", "**spots**", or "**touristic modules**" refer to the second level - specific attractions, neighborhoods, or activities within a region. Examples:
- Beijing: Forbidden City, Temple of Heaven, Hutongs, Great Wall
- Shanghai: The Bund, Yu Garden, Pudong District
- Guilin: Li River Cruise, Reed Flute Cave, Yangshuo

### Standard Pages in Each Region
Every major region follows a consistent structure with these standard pages:

1. **Overview** (`{region}_overview.html`)
   - Introduction to the region
   - Best time to visit
   - Getting around
   - Key highlights

2. **Preparation & Tickets** (`{region}_preparation.html`)
   - Advance bookings required
   - Ticket reservations
   - Museum/attraction booking information
   - Timeline for bookings

3. **Where to Stay** (`{region}_stay.html`)
   - Best neighborhoods/areas to stay
   - Accommodation types
   - Pros/cons of different areas
   - Booking tips

4. **Culinary Guide** (`{region}_culinary.html`)
   - Regional cuisine specialties
   - Signature dishes
   - Where to eat
   - Food culture
   - Street food recommendations

5. **Individual Destination Pages**
   - Specific attractions, sites, or experiences
   - Each with practical information (location, time needed, prices, tips)

6. **Day Trips** (where applicable)
   - Nearby destinations
   - Transportation information
   - Suggested itineraries

## Navigation Structure
The sidebar navigation is controlled by `_data/sidebars/china_sidebar.yml`. Each region has:
- An overview page
- Standard pages (preparation, stay, culinary)
- Multiple sub-pages for specific attractions/activities
- Modular content that can be mixed and matched

## Development Guidelines
- Use Jekyll best practices for content organization
- Keep content modular and reusable
- All content pages are in `/pages/china/` directory
- Follow the page frontmatter template (see existing pages)
- Use relative links within content using permalink format (`[text](permalink.html)`)
- Maintain clear navigation between regions and destinations
- Use front matter for metadata (dates, durations, costs, etc.)

## Page Frontmatter Template
```yaml
---
title: "Page Title"
keywords: keyword1, keyword2, keyword3
tags: [tag1, tag2]
sidebar: china_sidebar
permalink: page_name.html
summary: Brief one-sentence description for search and listings.
---
```

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

### Adding a New Region
1. Create standard pages:
   - `{region}_overview.md`
   - `{region}_preparation.md`
   - `{region}_stay.md`
   - `{region}_culinary.md`
2. Create destination/spot pages as needed
3. Add entries to `_data/sidebars/china_sidebar.yml`
4. Test locally before pushing

### Adding a New Destination/Spot
1. Create new page in `/pages/china/` with proper frontmatter
2. Use naming convention: `{region}_{destination}.md`
3. Add entry to appropriate region in `_data/sidebars/china_sidebar.yml`
4. Link from region overview page if it's a major attraction

## Important Files
- `_config.yml`: Site configuration
- `_data/sidebars/china_sidebar.yml`: Navigation structure
- `/pages/china/`: All destination content pages
- `index.md`: Homepage
- `Gemfile`: Ruby dependencies
- `/input/`: Raw HTML exports from Google Docs (source material)

## Content Guidelines
- Use descriptive page titles
- Include practical information:
  - Opening hours
  - Prices (in RMB and $ symbol for relative cost)
  - Duration of visit
  - Best time to visit
  - Booking requirements
- Add tips and recommendations
- Use consistent formatting across pages
- Include internal links to related pages using `[text](permalink.html)` format
- Use markdown headings appropriately (## for main sections, ### for subsections)

## Culinary Pages
Each region includes a dedicated culinary guide page featuring:
- Regional cuisine overview
- Signature dishes with descriptions
- Street food specialties
- Where to eat recommendations
- Dining tips and cultural notes
- Food safety and ordering advice

## Preparation Pages
Each region includes advance booking and preparation information:
- Which attractions require advance booking
- Booking windows (how many days ahead)
- Daily visitor limits
- Official booking websites
- Tours vs. independent visit options
- Transportation reservations

## Visual Elements
- Use relative image paths for local images
- External images via CDN URLs are acceptable
- Include alt text for accessibility
- Keep image file sizes reasonable
- Consider adding images to key destination pages

## Integration Notes

### Maps and KMZ Files
A Google My Maps KMZ file (`China 2026 v0.kmz`) is available in `/input/`. Options for integration:
1. **Embedded Map**: Convert to Google My Maps embed code (requires published map)
2. **Interactive Maps**: Use Leaflet.js or similar to display points
3. **Static Maps**: Extract coordinates and create static map images
4. **Link to External Map**: Publish Google My Map and link to it
5. **Per-Region Maps**: Create separate maps for each major region with POIs

Implementation suggestion: Add a "Maps" page or section to each region overview linking to an interactive map or embedded Google My Maps.

## Content Sources
The site was populated from HTML exports from Google Docs containing research and planning information. Original files preserved in `/input/` for reference.

## Development Workflow
1. Create/edit pages in `/pages/china/`
2. Update sidebar in `_data/sidebars/china_sidebar.yml` if needed
3. Test locally with `bundle exec jekyll serve`
4. Commit and push to main branch
5. GitHub Pages auto-builds and deploys

## Common Tasks

### To add a new attraction to existing region:
1. Create `{region}_{attraction}.md` in `/pages/china/`
2. Use existing pages as template for frontmatter
3. Add to sidebar.yml under appropriate region
4. Link from region overview if major attraction

### To add culinary information:
Add to the region's `{region}_culinary.md` page under appropriate section (signature dishes, street food, where to eat, etc.)

### To update navigation:
Edit `_data/sidebars/china_sidebar.yml` following the existing hierarchical structure

## Best Practices
- Maintain consistency in page structure across similar content types
- Update the overview page when adding significant new destinations
- Keep preparation pages current with booking requirements
- Test all internal links
- Ensure mobile responsiveness (theme handles this by default)
- Use descriptive permalink names matching page content
