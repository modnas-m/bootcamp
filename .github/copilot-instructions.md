# Copilot Instructions for Portfolio Homepage

## Project Overview
Single-page HTML portfolio for María Sánchez Domínguez, an architect and computational design specialist. The site uses vanilla JavaScript for client-side navigation without any build tools, frameworks, or external dependencies.

## Architecture & Key Patterns

### Page Navigation System
- **Pages**: Implemented via divs with `id` attributes (`home`, `about`, `work`, `project-1` through `project-6`)
- **State Management**: Uses CSS class `.active` on both navigation links and page divs to show/hide content
- **Key Pattern**: `display: none` by default; `.active` pages use `display: flex`
- **Event Handlers**: All in `<script>` tag at end of HTML
  - Navigation: Click handlers on `.nav-link` elements toggle `.active` class
  - Work items: Click `.work-item` shows corresponding project detail page
  - Back button: Returns from project detail to work grid

### Styling Architecture
- **Responsive Grid**: Work section uses `grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))` for flexible project cards
- **Two-Column Layout**: Flexbox layout with fixed-width sidebar (340px) + flexible main content
- **Color Scheme**: Primary accent `#e74c3c` (red), backgrounds `#f5f5f5` (light gray), borders/text `#000`/`#333`
- **Hover Effects**: Navigation links and work items change to accent color; work items translate up 5px

## Common Development Tasks

### Adding New Projects
1. Add new `<div id="project-N" class="page project-detail">` block in the work section
2. Add corresponding `.work-item` with `data-project="N"` attribute in the work grid
3. JavaScript automatically handles the click routing—no code changes needed
4. Keep project naming consistent: Project N / project-N

### Updating Navigation
- Edit `.nav-link` elements in navigation div
- Add `data-page` attribute matching the target page `id`
- JavaScript dynamically targets pages by `data-page` value

### Modifying Layout/Colors
- All styling is in `<style>` tag (lines 8-176)
- Colors are hardcoded values; no color variables
- Sidebar width affects main content flex layout—adjust `.sidebar { width }` and corresponding responsive behavior

## Important Conventions

- **No External Dependencies**: All HTML, CSS, and JavaScript are inline in a single file
- **Accessibility Note**: Social buttons are empty `<button>` elements with no `aria-label`—consider adding labels if expanding
- **Image Placeholders**: All images use gray divs (e.g., `.profile-circle`, `.project-image-placeholder`); no actual image assets currently in use
- **Filename**: Portfolio is single file `portfolio_homepage.html`—moving or renaming requires updating any external references

## When Expanding the Site

- Keep JavaScript event delegation pattern (query all elements, attach listeners in loop)
- Maintain page/project naming scheme for clarity
- Test all navigation paths when adding new pages
- Social buttons currently non-functional—clarify intended behavior before implementation
