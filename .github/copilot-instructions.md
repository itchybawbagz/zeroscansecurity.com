# ZeroScan Security Website

**ALWAYS follow these instructions first and only fallback to additional search and context gathering if the information in the instructions is incomplete or found to be in error.**

ZeroScan Security is a static HTML website for a security vulnerability scanning service. The site consists of a simple landing page with embedded CSS styling and no JavaScript dependencies.

## Repository Structure
```
.
├── README.md          # Minimal project description
├── index.html         # Complete HTML landing page with embedded CSS
├── logo.svg          # SVG logo for the ZeroScan Security brand
└── .github/
    └── copilot-instructions.md  # This file
```

## Quick Start - Serving Locally

**Choose ONE of the following validated serving methods:**

### Method 1: Python HTTP Server (Recommended)
```bash
cd /home/runner/work/zeroscansecurity.com/zeroscansecurity.com
python3 -m http.server 8000
```
- **Timing**: Starts instantly (< 1 second)
- **Access**: http://localhost:8000
- **Use when**: Default development, quick testing

### Method 2: Node.js HTTP Server
```bash
cd /home/runner/work/zeroscansecurity.com/zeroscansecurity.com
npx http-server -p 8080
```
- **Timing**: First run downloads package (~5-10 seconds), subsequent runs instant
- **Access**: http://localhost:8080  
- **Use when**: Need CORS support or advanced HTTP features

### Method 3: PHP Built-in Server
```bash
cd /home/runner/work/zeroscansecurity.com/zeroscansecurity.com
php -S localhost:8001
```
- **Timing**: Starts instantly (< 1 second)
- **Access**: http://localhost:8001
- **Use when**: Testing with PHP environment

## Validation Scenarios

**ALWAYS run these validation steps after making ANY changes:**

1. **Basic Functionality Test**:
   ```bash
   # Start server (choose one method above)
   curl -s http://localhost:[PORT] | head -5
   # Should return HTML starting with "<!DOCTYPE html>"
   ```

2. **Complete User Scenario Validation**:
   - Load the site in a browser
   - Verify the page title shows "ZeroScan Security"
   - Check that navigation links (Home, About, Features, Contact) are visible
   - Confirm the main heading "ZeroScan Security" displays
   - Verify the feature list shows 4 items with checkmarks
   - Check that the green "Scan Your Website Now" button is present
   - Ensure footer copyright text displays correctly

3. **Browser Testing Commands**:
   ```bash
   # Test site accessibility
   curl -I http://localhost:[PORT]
   # Should return "HTTP/1.0 200 OK" or "HTTP/1.1 200 OK"
   
   # Verify HTML content
   curl -s http://localhost:[PORT] | grep -i "zeroscan"
   # Should return multiple matches including title and heading
   ```

## Making Changes

### HTML Content Changes
- **File to modify**: `index.html`
- **Contains**: Complete HTML structure with embedded CSS in `<style>` tags
- **Sections**: Header navigation, main content container, footer
- **Always test**: Serve locally and validate in browser after changes

### Styling Changes  
- **Location**: Embedded in `<style>` tag within `index.html` (lines 7-15)
- **Key classes**: `.container`, `.cta`, `nav a`, `header`, `footer`
- **Always test**: Check responsive behavior and visual appearance

### Logo Changes
- **File**: `logo.svg`
- **Format**: SVG with shield icon and text
- **Usage**: Referenced in site but currently not displayed in HTML
- **Always test**: If adding logo to HTML, verify it displays correctly

## No Build Process Required

**CRITICAL**: This is a static site with NO build process:
- No `npm install` needed
- No compilation step required  
- No bundling or minification
- No package.json or dependencies
- Changes to HTML/CSS take effect immediately

## No Testing Framework

**Current State**: No automated tests exist
- No Jest, Mocha, or other test frameworks
- No package.json test scripts
- No CI/CD testing workflows
- Validation is manual browser testing only

## Development Workflow

1. **Start Development**:
   ```bash
   cd /home/runner/work/zeroscansecurity.com/zeroscansecurity.com
   python3 -m http.server 8000 &
   ```

2. **Make Changes**: Edit `index.html` directly

3. **Validate Changes**: 
   - Refresh browser at http://localhost:8000
   - Run validation scenarios above
   - Check browser console for errors

4. **Stop Development**:
   ```bash
   pkill -f "python3 -m http.server" 
   ```

## Git Workflow

**Repository Info**:
- Remote: https://github.com/itchybawbagz/zeroscansecurity.com
- Current branch: `copilot/fix-2`  
- Main branch: `main`

**Standard workflow**:
```bash
git status                    # Check current changes
git add .                     # Stage changes  
git commit -m "Description"   # Commit with clear message
# Push handled by report_progress tool
```

## Common Development Tasks

### Add New Section to Page
1. Locate insertion point in `index.html`
2. Add HTML within `<div class="container">` section
3. Add corresponding CSS if needed in `<style>` section
4. Test locally and validate display

### Modify Navigation
1. Edit `<nav>` section in `index.html` (lines 19-24)
2. Update href attributes from "#" to actual URLs when ready
3. Test navigation functionality

### Update Styling
1. Modify CSS in `<style>` section (lines 7-15)
2. Key variables: colors (#24292e, #2ea44f), fonts (Arial), spacing
3. Test responsive behavior on different screen sizes

## Troubleshooting

### Port Already in Use
```bash
# Find process using port
lsof -i :8000
# Kill existing server
pkill -f "python3 -m http.server"
# Or use different port
python3 -m http.server 8080
```

### Site Not Loading
1. Check server is running: `curl -I http://localhost:[PORT]`
2. Verify current directory: `pwd` should end with `zeroscansecurity.com`
3. Check file exists: `ls -la index.html`

### Changes Not Visible  
1. Hard refresh browser (Ctrl+F5 or Cmd+Shift+R)
2. Check browser cache settings
3. Try different browser or incognito mode

## Files Reference

### index.html Structure
- Lines 1-6: HTML head with title and viewport
- Lines 7-15: Embedded CSS styles  
- Lines 18-25: Header with navigation
- Lines 26-36: Main content container
- Lines 37-40: Footer section

### Key CSS Classes
- `.container`: Main content wrapper (max-width: 900px)
- `.cta`: Green call-to-action button styling
- `header`: Dark header background (#24292e)
- `nav a`: Navigation link styling
- `footer`: Footer styling matching header

### logo.svg Details
- Size: 320x80 viewBox
- Contains shield icon with checkmark
- Text: "ZeroScan" and "Security" 
- Colors: Blue (#1a62b3, #14497e) and green (#2ea44f)