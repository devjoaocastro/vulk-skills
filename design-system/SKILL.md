---
name: vulk-design-system
description: "Core design principles for professional, premium web applications. Always loaded. Triggers: design, premium, professional, modern, elegant, beautiful, stunning"
license: MIT
---

# Design System -- Core Principles

## 1. Color Strategy
- Define a semantic palette: primary, secondary, accent, background, surface, text, muted, border
- Use HSL for flexibility: `hsl(var(--primary))` allows easy theme switching
- Dark backgrounds: use neutral grays (#0a0a0a to #1a1a1a), NOT blue-black
- Light text on dark: use opacity steps (white/90, white/60, white/40, white/25)
- Accent colors: use sparingly -- one primary accent (green, blue, purple), one warm accent for CTAs
- NEVER use pure black (#000) for text or pure white (#fff) for backgrounds in premium designs

## 2. Spacing and Rhythm
- Use a 4px base grid: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96, 128
- Section padding: 80-120px vertical (clamp for responsive)
- Card padding: 24-32px
- Consistent gap between elements: 8px (tight), 16px (default), 24px (relaxed), 32px (loose)
- NEVER use random spacing -- every value should be from the scale

## 3. Visual Hierarchy
- One hero element per section (largest, boldest)
- Max 3 levels of text hierarchy visible at once
- Use size, weight, AND color to create hierarchy (not just size)
- Muted text for secondary info (opacity 0.5-0.7)
- Labels/eyebrows: uppercase, letter-spacing 0.05-0.1em, small size, muted color

## 4. Cards and Containers
- Border-radius: 12-16px for cards, 8px for inner elements, 9999px for pills
- Borders: 1px solid with low opacity (white/8 dark, gray-200 light)
- Shadows: layered (small tight + large diffuse) for depth
- Background: subtle tint (white/3-6% on dark, gray-50 on light)
- Hover: slight scale (1.02), border brighten, or background shift

## 5. Anti-Patterns (NEVER do)
- Rainbow gradients or neon colors
- More than 2 accent colors
- Inconsistent border-radius across components
- Text directly on images without overlay
- Centered text blocks wider than 600px
- Generic stock photo placeholders that add no value
- Shadows that look like glowing borders
- More than 3 font weights on one page
