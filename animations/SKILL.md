---
name: vulk-animations
description: "Professional animation patterns using Framer Motion and CSS. Loaded for web projects. Triggers: animation, animate, motion, transition, scroll, reveal, parallax, gsap, framer"
license: MIT
---

# Animations -- Professional Patterns

## 1. Framer Motion (preferred for React)
- Import: `import { motion, AnimatePresence } from 'framer-motion'`
- Reveal on scroll: `whileInView` with `viewport={{ once: true }}`
- Stagger children: use `variants` with parent `staggerChildren`
- Page transitions: wrap routes in `AnimatePresence mode="wait"`
- NEVER animate layout-heavy properties (width, height) -- use scale/opacity

## 2. Scroll Reveal Pattern (use everywhere)

```jsx
<motion.div
  initial={{ opacity: 0, y: 30 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{ once: true, margin: "-50px" }}
  transition={{ duration: 0.6, ease: [0.22, 1, 0.36, 1] }}
>
  {content}
</motion.div>
```

## 3. Stagger Pattern

```jsx
const container = { hidden: {}, show: { transition: { staggerChildren: 0.1 } } };
const item = { hidden: { opacity: 0, y: 20 }, show: { opacity: 1, y: 0 } };
<motion.div variants={container} initial="hidden" whileInView="show" viewport={{ once: true }}>
  {items.map(i => <motion.div key={i} variants={item}>{i}</motion.div>)}
</motion.div>
```

## 4. Hover Interactions
- Cards: `whileHover={{ y: -4, transition: { duration: 0.2 } }}`
- Buttons: `whileHover={{ scale: 1.02 }} whileTap={{ scale: 0.98 }}`
- SUBTLE is key -- max 4px movement, max 1.05 scale

## 5. Animated Counters
- Use `useInView` + `useSpring` for number counting
- Trigger once, animate from 0 to target
- Format with toLocaleString() for thousands separator

## 6. Performance Rules
- Only animate transform (x, y, scale, rotate) and opacity
- Use `will-change: transform` on animated elements
- `layout` prop only when needed (expensive)
- Disable animations for `prefers-reduced-motion`
