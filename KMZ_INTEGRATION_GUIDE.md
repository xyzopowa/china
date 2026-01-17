# KMZ File Integration Options for China Travel Website

## About the KMZ File

The file `China 2026 v0.kmz` in the `/input` directory is a Google My Maps export containing points of interest (POIs) for the China travel itinerary.

## What is a KMZ File?

- KMZ (Keyhole Markup Language Zipped) is a compressed KML file
- Contains geographic data: coordinates, markers, descriptions, routes
- Created by Google My Maps
- Can contain custom markers, polygons, and routes

## Integration Options

### Option 1: Embedded Google My Maps (Recommended - Easiest)

**How it works:**
1. Upload the KMZ file to Google My Maps (or use original Google My Maps)
2. Publish the map publicly
3. Get the embed code
4. Add to website pages

**Advantages:**
- No coding required
- Interactive features built-in
- Google maintains the map
- Easy to update

**Implementation:**
1. Go to [Google My Maps](https://www.google.com/mymaps)
2. Open the map (import KMZ if needed)
3. Share → Make public or "Anyone with link"
4. Click the 3-dot menu → "Embed on my site"
5. Copy the iframe code
6. Add to your Jekyll pages

**Example embed code:**
```html
<iframe src="https://www.google.com/maps/d/embed?mid=YOUR_MAP_ID" width="100%" height="600"></iframe>
```

**Where to add:**
- Create a `maps.md` page in the main navigation
- Add maps section to each region overview page
- Create a dedicated maps page per region

### Option 2: Leaflet.js Interactive Maps

**How it works:**
1. Extract POIs from KMZ file (convert to GeoJSON)
2. Use Leaflet.js library to create interactive maps
3. Customize markers and styling
4. Host entirely on your site

**Advantages:**
- Complete control over appearance
- No dependency on Google
- Can customize extensively
- Lighter weight

**Disadvantages:**
- Requires JavaScript knowledge
- More setup work
- Need to maintain map data

**Steps:**
1. Convert KMZ to GeoJSON:
   - Use online tools like [MyGeodata Converter](https://mygeodata.cloud/converter)
   - Or extract KML and convert with Python/Node tools

2. Add Leaflet.js to your site:
```html
<!-- In page head or layout -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
```

3. Create map container:
```html
<div id="map" style="height: 600px;"></div>
```

4. Initialize map with markers:
```javascript
var map = L.map('map').setView([39.9042, 116.4074], 5); // Center on China

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap contributors'
}).addTo(map);

// Add markers from GeoJSON
L.marker([39.9042, 116.4074]).addTo(map)
    .bindPopup('Beijing - Forbidden City');
// ... more markers
```

### Option 3: Static Map Images

**How it works:**
1. Take screenshots of important map sections
2. Or generate static maps via Google Maps Static API
3. Add as images to pages

**Advantages:**
- Fast loading
- No JavaScript required
- Works everywhere

**Disadvantages:**
- Not interactive
- Need separate image for each view
- More difficult to maintain

**When to use:**
- As fallback for Option 1 or 2
- Print-friendly version
- Quick overview in blog posts

### Option 4: Link to External Map

**How it works:**
- Publish Google My Map
- Add prominent links to the map from your site

**Advantages:**
- Simplest implementation
- No embedding needed
- Full Google Maps features

**Disadvantages:**
- Users leave your site
- Less integrated experience

**Implementation:**
```markdown
## Interactive Map

[View full interactive map of our China itinerary →](https://www.google.com/maps/d/viewer?mid=YOUR_MAP_ID)
```

### Option 5: Per-Region Maps

**How it works:**
- Extract POIs for each region from KMZ
- Create separate maps for Beijing, Shanghai, Xi'an, etc.
- Embed regional maps in each region's overview page

**Advantages:**
- Focused, relevant information
- Faster loading
- Better mobile experience

**Disadvantages:**
- More maps to maintain
- Need to split the KMZ data

**Implementation:**
Create separate Google My Maps for each region, or filter GeoJSON data by region.

## Recommended Approach

### For This Website: Hybrid Approach

1. **Homepage**: Link to main Google My Map
2. **Each Region Overview**: Embedded region-specific map (Google My Maps or Leaflet)
3. **Maps Page**: Full embedded map with all regions

### Immediate Steps:

**Step 1: Prepare the Map**
```bash
# Option A: Use existing Google My Maps
1. Go to Google My Maps
2. Open your China 2026 map
3. Share → Anyone with link
4. Get embed code

# Option B: Import KMZ
1. Go to Google My Maps
2. Create new map
3. Import → Upload China 2026 v0.kmz
4. Publish and get embed code
```

**Step 2: Create Maps Page**

Create `/pages/china/maps.md`:
```markdown
---
title: "Interactive Maps"
keywords: maps, locations, itinerary
tags: [maps]
sidebar: china_sidebar
permalink: maps.html
summary: Interactive maps showing all destinations and points of interest.
---

## China 2026 Itinerary Map

<iframe src="https://www.google.com/maps/d/embed?mid=YOUR_MAP_ID" width="100%" height="800"></iframe>

## How to Use

- Click markers for details
- Use layers to filter by region
- Save map to your Google account
- Download for offline use (in Google Maps app)
```

**Step 3: Add to Sidebar**

In `_data/sidebars/china_sidebar.yml`:
```yaml
  - title: Maps
    output: web, pdf
    folderitems:
    - title: Interactive Maps
      url: /maps.html
      output: web, pdf
```

**Step 4: Add Mini Maps to Region Pages**

In region overview pages, add map section:
```markdown
## Map

<iframe src="https://www.google.com/maps/d/embed?mid=YOUR_MAP_ID" width="100%" height="400"></iframe>

*[View full-screen map →](maps.html)*
```

## Converting KMZ for Custom Use

If you want to extract data from the KMZ:

**Using Python:**
```python
import zipfile
from xml.etree import ElementTree as ET

# Extract KML from KMZ
with zipfile.ZipFile('input/China 2026 v0.kmz', 'r') as kmz:
    kml = kmz.read('doc.kml')

# Parse KML
root = ET.fromstring(kml)

# Extract placemarks
for placemark in root.findall('.//{http://www.opengis.net/kml/2.2}Placemark'):
    name = placemark.find('{http://www.opengis.net/kml/2.2}name').text
    coords = placemark.find('.//{http://www.opengis.net/kml/2.2}coordinates').text
    print(f"{name}: {coords}")
```

**Using Online Tools:**
- [MyGeodata Converter](https://mygeodata.cloud/converter/) - Convert KMZ to GeoJSON
- [GPS Visualizer](https://www.gpsvisualizer.com/) - Convert and visualize

## Mobile Considerations

- Embedded maps can be heavy on mobile
- Consider adding a "View in Google Maps" link for mobile users
- Test on actual mobile devices
- Ensure responsive iframe sizing

## Recommended CSS for Embedded Maps

```css
.map-container {
    position: relative;
    padding-bottom: 56.25%; /* 16:9 ratio */
    height: 0;
    overflow: hidden;
}

.map-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
```

## Next Steps

1. Decide on primary approach (recommend: embedded Google My Maps)
2. Publish your Google My Map
3. Create `/pages/china/maps.md` page
4. Add map embeds to region overview pages
5. Test on desktop and mobile
6. Consider adding maps to PDF export if needed

## Resources

- [Google My Maps Help](https://support.google.com/mymaps)
- [Leaflet.js Documentation](https://leafletjs.com/)
- [KML Reference](https://developers.google.com/kml/documentation/kmlreference)
- [GeoJSON Specification](https://geojson.org/)
