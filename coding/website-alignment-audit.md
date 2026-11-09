# Universal Website Alignment, Container Consistency & Responsive Layout Audit

## Objective

Perform a comprehensive, project-wide visual alignment and layout consistency audit of the current website.

Automatically inspect the existing codebase, identify the framework and styling architecture, understand the established design system, and fix all unintended container alignment, horizontal spacing, width, and responsive layout inconsistencies.

The final result should be a visually consistent, professionally aligned, premium-quality website across all pages and screen sizes.

**This is an implementation task, not just an audit. Identify problems, fix their root causes, and verify the results.**

## Phase 1: Project Discovery & Design System Analysis

Before making any changes:

1. Identify the project's technology stack, framework, CMS, page builder, and styling approach.
2. Inspect the global layout architecture, including headers, navigation, content wrappers, footers, and reusable components.
3. Identify existing design tokens, CSS variables, spacing scales, maximum widths, breakpoints, and container utilities.
4. Determine how layout settings are managed through the theme, framework, CMS, or page builder.
5. Identify existing shared containers and whether individual pages override their behavior.
6. Understand the website's visual hierarchy and intentional full-width or asymmetric layouts.

Do not introduce a new design system unnecessarily. Improve and standardize the existing architecture.

## Phase 2: Establish the Primary Alignment Reference

Determine the website's intended global horizontal alignment system.

Use the header's main content container and brand/logo position as primary visual references where appropriate.

The following should follow consistent horizontal boundaries unless the design intentionally requires otherwise:

- Header logo and navigation
- Page headings and breadcrumbs
- Main content sections
- Section titles, subtitles, and descriptions
- Product/service cards and grids
- Forms and search interfaces
- Images, galleries, and carousels
- Content blocks and promotional sections
- Calls to action
- Footer content and columns

### Alignment Principles

- The primary content's left boundary should visually align with the header's intended content boundary.
- Use consistent maximum widths across related sections.
- Maintain balanced left and right margins.
- Establish consistent page gutters for each responsive breakpoint.
- Keep full-width backgrounds and media edge-to-edge when intended, while aligning their inner content.
- Avoid unnecessary nested padding and margin accumulation.
- Preserve intentional centered, asymmetric, or editorial layouts.
- Do not force all child elements to align directly with the logo when nested grid structures require different positioning.

## Phase 3: Automated Visual Inspection

Use Playwright, browser automation, or available browser testing tools to inspect the actual rendered website.

Test at the following viewport widths:

| Device | Width |
|---|---|
| Large desktop | 1920px |
| Desktop | 1440px |
| Laptop | 1366px |
| Small desktop | 1280px |
| Tablet landscape | 1024px |
| Tablet portrait | 768px |
| Mobile | 430px |
| Mobile | 390px |
| Small mobile | 375px |
| Narrow mobile | 320px |

Inspect all existing page types, reusable layouts, and representative pages.

Capture screenshots before making changes.

Measure actual rendered element positions using `getBoundingClientRect()` and computed styles wherever possible.

Check:

- Header versus main content alignment
- Inconsistent section container widths
- Uneven horizontal margins
- Improper padding and spacing
- Misaligned headings and content blocks
- Incorrect grid and card positioning
- Nested container offsets
- Unexpected content overflow
- Horizontal scrolling
- Responsive breakpoint inconsistencies
- Footer alignment differences
- Fixed-position and sticky element issues
- Layout shifts caused by images or dynamic content
- Alignment differences between similar pages

Distinguish genuine layout defects from intentional design decisions.

## Phase 4: Root Cause Analysis

For every issue, investigate the underlying cause before applying a fix.

Possible causes include:

- Conflicting CSS rules
- Different container maximum widths
- Incorrect framework utility classes
- Inconsistent page-builder settings
- Duplicate horizontal padding
- Nested width constraints
- Incorrect margin calculations
- Missing responsive overrides
- Grid or flexbox configuration problems
- Inconsistent global component usage
- Unexpected absolute positioning
- Third-party component styles

Prefer structural corrections over cosmetic patches.

## Phase 5: Implement a Consistent Container System

Standardize the existing global container architecture where needed.

Prefer reusable design tokens, shared layout components, CSS variables, theme settings, or framework-native container utilities.

Ensure the system supports:

1. A consistent global content width
2. Appropriate maximum-width constraints
3. Responsive horizontal gutters
4. Automatic horizontal centering
5. Full-width sections with aligned inner content
6. Nested grid and content layouts
7. Reusable spacing conventions
8. Compatibility with the existing CMS or page builder

Use the project's established naming conventions and architectural patterns.

Avoid:

- Hardcoded arbitrary offsets
- Excessive `!important` declarations
- Repeated section-specific overrides
- Unnecessary duplicate container definitions
- Breaking existing responsive behavior
- Introducing incompatible third-party dependencies

**Important:** Do not select arbitrary container widths or spacing values. Derive them from the established design system and existing visual references.

## Phase 6: Fix All Affected Pages

Apply necessary corrections throughout the project.

Fix shared components globally whenever possible rather than modifying each page independently.

Review:

- Homepage
- Standard content pages
- Listing and archive pages
- Detail pages
- Forms and checkout flows, where applicable
- Landing pages
- Blog pages
- Search and filter interfaces
- Authentication and dashboard pages, where applicable
- Header and footer variants
- Dynamic and CMS-generated templates

Preserve existing content, styling, branding, functionality, and page structure unless changes are necessary to correct a verified layout defect.

Do not redesign sections that are already visually correct.

## Phase 7: Responsive Layout Optimization

Test and correct alignment at all supported breakpoints.

Ensure:

- Consistent mobile gutters
- Correct content stacking
- Proper grid transitions
- No unwanted horizontal scrolling
- Images remain within their intended boundaries
- Buttons and forms fit their containers
- Navigation remains usable
- Cards maintain consistent spacing
- Typography does not cause overflow
- Responsive padding follows a coherent scale

Also test intermediate widths between major breakpoints to identify hidden layout issues.

## Phase 8: Visual Regression & Functional Verification

After implementing changes:

1. Reopen the website using the available browser testing tools.
2. Capture after-fix screenshots using the same viewport dimensions.
3. Compare before-and-after screenshots.
4. Measure the updated container boundaries.
5. Verify alignment consistency across related sections.
6. Confirm that intentional full-width designs remain intact.
7. Check for unexpected visual regressions.
8. Confirm that interactive elements still work correctly.
9. Verify all affected page templates.
10. Test for horizontal overflow and responsive layout failures.

Where practical, create reusable automated tests for container alignment, responsive gutters, and horizontal overflow.

Never claim a test passed unless it was actually executed.

## Phase 9: Production Safety & Code Quality

Follow the existing project's coding standards.

- Preserve SEO-related markup and metadata.
- Do not modify business logic unnecessarily.
- Do not break booking, checkout, authentication, or other interactive functionality.
- Preserve accessibility and semantic HTML.
- Maintain CMS/page-builder editability.
- Avoid unnecessary dependencies.
- Minimize CSS complexity.
- Ensure fixes are maintainable and reusable.
- Avoid modifying generated or vendor files when a supported customization mechanism exists.

## Phase 10: Final Report

After completing the fixes, provide a structured report covering:

### A. Project Analysis
- Detected technology stack
- Existing container architecture
- Identified alignment reference
- Global container and responsive spacing conventions

### B. Issues Found
For each confirmed issue, report:

- Page or component
- Viewport width
- Observed alignment problem
- Root cause
- Correction implemented

### C. Implementation Summary
- Shared components updated
- Global styles updated
- Page-specific fixes
- Responsive improvements

### D. Verification
- Pages tested
- Viewports tested
- Before-and-after screenshots
- Alignment measurements
- Regression test results
- Remaining limitations or unresolved issues

## Completion Criteria

Consider the task complete only when:

- The website uses a coherent global container alignment system.
- Related content sections follow consistent horizontal boundaries.
- Header, primary content, and footer alignment is visually harmonious.
- Responsive gutters and spacing are consistent.
- No unintended horizontal overflow remains in tested layouts.
- Intentional design exceptions are preserved.
- All affected pages have been verified.
- No significant visual or functional regressions have been introduced.

## Execution Instructions

Work autonomously within the current project.

First inspect and understand the architecture, then identify the problems, implement appropriate fixes, and perform thorough visual and functional verification.

Use available project skills, design-system guidelines, browser automation, and testing tools where appropriate.

Do not make assumptions about the project's framework or styling conventions.

Do not stop after analysis or provide only recommendations.

**Expected Result: A fully audited, properly aligned, responsive, visually polished, and maintainable website with consistent container spacing across the entire project.**
