# China 2026 Travel Itinerary

Comprehensive travel guide for planning a trip to China in 2026.

## Website

This Jekyll-based documentation website is deployed via GitHub Pages:

**🌐 https://xyzopowa.github.io/china/**

## About

This repository hosts a modular travel guide for China 2026, featuring:

- **Beijing**: Forbidden City, Great Wall, modern districts
- **Xi'an**: Terracotta Warriors, Ancient City Wall, Mt. Huashan
- **Chongqing**: Mountain city, hot pot capital
- **Yichang**: Three Gorges Dam, river cruises
- Flexible, customizable itineraries for each destination

## Technology Stack

- **Framework**: Jekyll (Documentation Theme)
- **Theme**: [Jekyll Documentation Theme](https://github.com/tomjoht/documentation-theme-jekyll)
- **Hosting**: GitHub Pages
- **Content**: Markdown

## Local Development

### Prerequisites

- Ruby 2.5+ and RubyGems
- Bundler (`gem install bundler`)

### Setup and Build

1. **Clone the repository**
   ```bash
   git clone https://github.com/xyzopowa/china.git
   cd china
   ```

2. **Install dependencies**
   ```bash
   bundle install
   ```

3. **Build and serve locally**
   ```bash
   bundle exec jekyll serve
   ```

4. **View the site**
   Open your browser to: `http://localhost:4000/china/`

### Quick Commands

```bash
# Install/update dependencies
bundle install
bundle update

# Build the site
bundle exec jekyll build

# Serve locally with live reload
bundle exec jekyll serve

# Serve with live reload (accessible from network)
bundle exec jekyll serve --host 0.0.0.0

# Build for production
JEKYLL_ENV=production bundle exec jekyll build
```

## When Updating Website Content

After making changes to content files:

1. **Test locally first**
   ```bash
   bundle exec jekyll serve
   ```
   
2. **Check the site** at `http://localhost:4000/china/`

3. **Commit and push changes**
   ```bash
   git add .
   git commit -m "Description of changes"
   git push
   ```

4. **GitHub Pages will automatically rebuild** the site (takes 1-2 minutes)

5. **Verify deployment** at https://xyzopowa.github.io/china/

## Project Structure

```
├── _config.yml                    # Site configuration
├── _data/
│   └── sidebars/
│       └── china_sidebar.yml      # Navigation structure
├── _includes/                     # Reusable components
├── _layouts/                      # Page templates
├── pages/
│   └── china/                     # Travel destination pages
├── css/                           # Stylesheets
├── index.md                       # Homepage
└── Gemfile                        # Ruby dependencies
```

## Adding New Content

### Adding a New Destination

1. Create page in `pages/china/`:
   ```markdown
   ---
   title: "Destination Name"
   keywords: keywords here
   tags: [tag]
   sidebar: china_sidebar
   permalink: destination_name.html
   summary: "Brief description"
   ---
   
   Content here...
   ```

2. Add to sidebar in `_data/sidebars/china_sidebar.yml`:
   ```yaml
   - title: Destination Name
     url: /destination_name.html
     output: web, pdf
   ```

3. Test locally before pushing

## Troubleshooting

### Common Issues

**Bundle install fails:**
```bash
gem install bundler
bundle update
```

**Port already in use:**
```bash
bundle exec jekyll serve --port 4001
```

**Changes not showing:**
- Hard refresh browser (Ctrl+F5 or Cmd+Shift+R)
- Clear Jekyll cache: `rm -rf _site .jekyll-cache`

## Contributing

This is a personal travel planning project. Feel free to fork for your own travel plans!

## License

Content © 2026 - For personal use
