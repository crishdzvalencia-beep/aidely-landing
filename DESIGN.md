---
name: Aidely
colors:
  surface: '#faf8ff'
  surface-dim: '#d2d9f4'
  surface-bright: '#faf8ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f2f3ff'
  surface-container: '#eaedff'
  surface-container-high: '#e2e7ff'
  surface-container-highest: '#dae2fd'
  on-surface: '#131b2e'
  on-surface-variant: '#434655'
  inverse-surface: '#283044'
  inverse-on-surface: '#eef0ff'
  outline: '#737686'
  outline-variant: '#c3c6d7'
  surface-tint: '#0053db'
  primary: '#004ac6'
  on-primary: '#ffffff'
  primary-container: '#2563eb'
  on-primary-container: '#eeefff'
  inverse-primary: '#b4c5ff'
  secondary: '#006b5f'
  on-secondary: '#ffffff'
  secondary-container: '#6df5e1'
  on-secondary-container: '#006f64'
  tertiary: '#943700'
  on-tertiary: '#ffffff'
  tertiary-container: '#bc4800'
  on-tertiary-container: '#ffede6'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#dbe1ff'
  primary-fixed-dim: '#b4c5ff'
  on-primary-fixed: '#00174b'
  on-primary-fixed-variant: '#003ea8'
  secondary-fixed: '#71f8e4'
  secondary-fixed-dim: '#4fdbc8'
  on-secondary-fixed: '#00201c'
  on-secondary-fixed-variant: '#005048'
  tertiary-fixed: '#ffdbcd'
  tertiary-fixed-dim: '#ffb596'
  on-tertiary-fixed: '#360f00'
  on-tertiary-fixed-variant: '#7d2d00'
  background: '#faf8ff'
  on-background: '#131b2e'
  surface-variant: '#dae2fd'
typography:
  headline-xl:
    fontFamily: Sora
    fontSize: 48px
    fontWeight: '700'
    lineHeight: 56px
    letterSpacing: -0.02em
  headline-xl-mobile:
    fontFamily: Sora
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Sora
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 40px
    letterSpacing: -0.01em
  headline-lg-mobile:
    fontFamily: Sora
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
    letterSpacing: -0.01em
  headline-md:
    fontFamily: Sora
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
  body-lg:
    fontFamily: Inter
    fontSize: 18px
    fontWeight: '400'
    lineHeight: 28px
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-sm:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  label-md:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 20px
    letterSpacing: 0.05em
  label-sm:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  base: 8px
  container-max: 1280px
  gutter: 24px
  margin-mobile: 16px
  margin-desktop: 40px
  stack-sm: 8px
  stack-md: 16px
  stack-lg: 32px
---

## Brand & Style

The design system is anchored in the concept of "Conscious Efficiency." It targets professional users who value high-performance tools that don't feel cold or overly mechanical. The brand personality is helpful, trustworthy, and modern, seeking to evoke a sense of calm reliability through a clean, Professional SaaS aesthetic.

The visual style blends **Corporate Modern** with a human-centric approach. It prioritizes clarity and functional beauty, utilizing generous whitespace to reduce cognitive load. By combining precise geometry with soft edges and a vibrant palette, the design system ensures that complex automation tasks feel approachable and simple to execute.

## Colors

The palette is designed to build immediate trust while highlighting technical innovation. 

- **Trust Blue (#2563EB):** The primary driver for actions and brand presence. It signals stability and professional rigor.
- **Automation Teal (#14B8A6):** Used as a secondary accent to denote "active" states, success, or automated processes. It provides a refreshing contrast to the primary blue.
- **Primary Text (#0F172A):** A deep slate that ensures high legibility and a grounded feel, replacing pure black for a softer, more modern finish.
- **Soft White (#F8FAFC):** The foundational canvas. This off-white shade reduces screen glare and provides a premium, "airy" feel compared to stark white.

## Typography

This design system utilizes a dual-font strategy to balance character with utility. 

**Sora** is used for headlines to provide a bold, geometric, and futuristic personality. Its wider stance and unique apertures give the UI a distinctive "tech" edge.

**Inter** handles all body copy and UI labels. Chosen for its exceptional legibility and systematic neutral tone, it ensures that data-heavy screens remain easy to parse. 

For mobile, large display type scales down aggressively to maintain vertical rhythm, while body sizes remain constant to preserve accessibility.

## Layout & Spacing

The layout philosophy follows a **fluid grid** model with an 8px base unit. This ensures mathematical harmony across all components.

- **Mobile:** A 4-column grid with 16px side margins. Content is primarily stacked vertically.
- **Desktop:** A 12-column grid with a maximum container width of 1280px. Side margins expand to 40px to create a sense of breathability.

Whitespace is used intentionally as a structural element. Use "Stack" spacing (16px or 32px) to group related information, ensuring that the interface never feels cluttered. Gutters are fixed at 24px to provide clear separation between cards and layout modules.

## Elevation & Depth

Visual hierarchy is achieved through a combination of **tonal layers** and **ambient shadows**. 

The background (#F8FAFC) serves as the lowest layer. Primary cards and surfaces use a pure white (#FFFFFF) background to "pop" against the soft white base. 

Shadows are used sparingly and must be extra-diffused. Use a low-opacity slate tint for shadows (e.g., `rgba(15, 23, 42, 0.08)`) with a high blur radius to avoid a "dirty" look. Interactive elements like buttons and active cards should slightly increase their shadow spread on hover to provide tactile feedback without looking skeuomorphic.

## Shapes

The shape language is defined by a "Medium-Large" roundedness, reinforcing the friendly and modern brand persona.

- **Standard Elements:** Buttons, input fields, and small tags use a **0.5rem (8px)** radius.
- **Containers:** Content cards and modals use a **1rem (16px)** radius to feel substantial and soft.
- **Specialty Elements:** User avatars and specific pill-shaped status indicators use a fully rounded **9999px** radius.

This consistency in rounding ensures that the interface feels cohesive and safe, avoiding sharp "industrial" corners.

## Components

### Buttons
Primary buttons use a solid Trust Blue background with white text. Secondary buttons should use a subtle teal outline or a light teal ghost style. All buttons feature a 0.5rem radius and a slight transition on hover that deepens the shadow.

### Input Fields
Fields should have a subtle 1px border in a light grey-blue, with a focus state that utilizes a 2px Trust Blue ring. Labels should use the `label-sm` typography style for clarity.

### Cards
Cards are the primary container. They must have a pure white background, a 1rem corner radius, and a "Soft Ambient" shadow. Padding inside cards should be generous (typically 24px) to maintain the "clean" aesthetic.

### Chips & Tags
Use Automation Teal for success or active automation tags. Chips should be small, using the `label-sm` font, with a light background tint of the status color to maintain readability.

### Lists
Lists should use 16px of vertical spacing between items, separated by very faint 1px horizontal lines (`#E2E8F0`) or simple whitespace if the items are distinct enough.