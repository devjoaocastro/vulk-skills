---
name: vulk-accessibility
description: "Accessibility and semantic HTML patterns. Triggers: accessible, a11y, aria, semantic, screen reader, keyboard"
license: MIT
---

# Accessibility -- Essential Patterns

1. **Semantic HTML:** Use correct elements (nav, main, section, article, aside, footer, header)
2. **Headings:** One h1 per page, then h2 -> h3 -> h4 in order. Never skip levels
3. **Images:** Always alt text. Decorative images: alt=""
4. **Buttons vs Links:** Button for actions, anchor for navigation. Never div with onClick
5. **Focus:** All interactive elements must be keyboard accessible with visible focus ring
6. **Color contrast:** 4.5:1 minimum for text, 3:1 for large text
7. **Forms:** Every input needs a label (visible or sr-only). Error messages linked with aria-describedby
8. **Reduced motion:** Wrap animations in `@media (prefers-reduced-motion: no-preference)`
