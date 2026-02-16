# Simple Curriculum Vitae

Static HTML/CSS CV with two layout variants, optimized for A4 print output.

## Project Structure

- `cv_profile/` - CV variant with profile picture in sidebar
- `cv_without/` - CV variant without profile picture
- Each variant contains:
  - `cv-julian-engler.html` - Main CV document (2-page layout)
  - `assets/style.css` - Print styles and icon config
  - `assets/tailwind.config.js` - Tailwind theme (colors, fonts, border-radius)
  - `assets/profil_pic.{jpg,png}` - Profile images (cv_profile only)
  - `docs/` - Layout reference/scratch files

## Tech Stack

- **Tailwind CSS** via CDN (`cdn.tailwindcss.com`) - no build step
- **Google Fonts**: Inter (display font)
- **Google Material Symbols Outlined** for icons
- No bundler, no Node dependencies, no build process - open HTML files directly in browser

## Key Patterns

### Bilingual Support (DE/EN)
- Default language is German (`<html lang="de">`)
- English translations via `data-en` attributes on elements
- `toggleLang()` JS function swaps text content between `data-de` and `data-en`
- The toggle button in the toolbar shows "EN" (to switch to English) or "DE" (to switch back)

### Dark Mode
- Toggled via class strategy (`<html class="light">` / `dark` class toggle)
- Configured in Tailwind: `darkMode: "class"`
- All elements use `dark:` variant classes

### Print Optimization
- A4 page layout: `210mm x 297mm`
- `.a4-container` class for page containers
- `.page-break` class for page breaks between pages
- `.no-print` class hides toolbar/footer when printing
- `style.css` contains all `@media print` rules with explicit color preservation
- `.sidebar-print` overrides sidebar width/padding for print

### Color Theme (Tailwind config)
- `primary`: `#007517` (green)
- `forest-dark`: `#00493a`
- `forest-mid`: `#00735c`
- `cool-gray-light`: `#edf0ee`
- `cool-gray-text`: `#606462`

### Layout
- 2-page A4 design with sidebar (300px) + main content area
- Page 1: Profile/contact/skills (sidebar) + summary + experience (main)
- Page 2: Education/qualifications/links (sidebar) + continued experience (main)
- Companies with multiple roles use a timeline (border-left + dots) to group positions

## Guidelines

- Keep both variants (`cv_profile` and `cv_without`) in sync when making structural or style changes
- Always add `data-en="..."` attributes when adding German text content
- Use Tailwind utility classes; avoid custom CSS except for print rules in `style.css`
- Test print output after layout changes (browser print preview)
- Tech tags use small pill-style spans with `text-[9px]` or `text-[10px]`
