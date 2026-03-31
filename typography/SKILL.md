---
name: vulk-typography
description: "Professional font pairing and typography rules. Triggers: font, typography, heading, serif, sans-serif, premium, elegant, corporate, luxury"
license: MIT
---

# Typography -- Professional Font System

## 1. Font Pairing Rules
- MAX 2 fonts per project (heading + body)
- Heading: bold, distinctive, expressive
- Body: clean, readable, neutral
- NEVER use more than 3 font weights total

## 2. Proven Pairings (import from Google Fonts)
- Premium corporate: Playfair Display + Inter
- Modern SaaS: Inter + Inter (weight contrast only)
- Editorial: Cormorant Garamond + Source Sans 3
- Tech/startup: Space Grotesk + DM Sans
- Luxury: Instrument Serif + Manrope
- Clean minimal: Geist + Geist Mono

## 3. Size Scale (Tailwind)
- Hero headline: text-5xl md:text-6xl lg:text-7xl (48-72px)
- Section heading: text-3xl md:text-4xl (30-36px)
- Card heading: text-xl md:text-2xl (20-24px)
- Body: text-base (16px)
- Small/caption: text-sm (14px)
- Label/eyebrow: text-xs uppercase tracking-wider (12px)

## 4. Tracking and Leading
- Headlines: tracking-tight (-0.025em) or tracking-tighter (-0.05em)
- Body: tracking-normal
- Labels: tracking-wider (0.05em) or tracking-widest (0.1em)
- Body line-height: leading-relaxed (1.625)
- Headlines: leading-tight (1.25) or leading-none (1)

## 5. Google Fonts Import (in index.html)

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
```

Then in CSS: `font-family: 'Inter', system-ui, sans-serif;`
