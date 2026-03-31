---
name: vulk-tailwind
description: "Correct Tailwind CSS usage patterns. Always loaded. Triggers: tailwind, css, style, responsive, dark mode"
license: MIT
---

# Tailwind CSS -- Correct Usage

## 1. Responsive Design (CRITICAL -- most common failure)
- Mobile-first: base classes are mobile, add `sm:`, `md:`, `lg:`, `xl:` for larger
- Hero sections: `min-h-screen` or `min-h-[80vh]` -- NEVER fixed `h-screen` (breaks on mobile)
- Header clearance: hero must have `pt-20` or `pt-24` to clear fixed navbar
- Grid: `grid-cols-1 md:grid-cols-2 lg:grid-cols-3` -- ALWAYS start with 1 column
- Text: `text-3xl md:text-4xl lg:text-5xl xl:text-6xl` -- scale up, never fixed
- Padding: `px-4 md:px-6 lg:px-8` -- more padding on larger screens
- Container: `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` -- centered content
- Images: `w-full h-auto` or `aspect-[16/9] object-cover` -- NEVER fixed dimensions
- Hide/show: `hidden md:block` for desktop-only, `md:hidden` for mobile-only
- Stack to Row: `flex flex-col md:flex-row` -- vertical on mobile, horizontal on desktop

## 2. Common Responsive Failures to AVOID
- `w-[800px]` -- use `max-w-3xl w-full` instead
- `h-screen` on hero without `min-h-screen` -- content overflows on mobile
- Fixed pixel gaps/padding -- use responsive: `gap-4 md:gap-6 lg:gap-8`
- `text-6xl` without smaller mobile size -- unreadable on phones
- Horizontal scroll -- check every section overflows correctly
- Hero text touching the navbar -- ALWAYS add `pt-20` minimum

## 3. Hero Section Pattern (CORRECT)

```jsx
<section className="relative min-h-[85vh] flex items-center pt-24 pb-16 px-4">
  <div className="max-w-7xl mx-auto text-center">
    <h1 className="text-4xl md:text-5xl lg:text-6xl xl:text-7xl font-bold tracking-tight">
      Headline Here
    </h1>
    <p className="mt-6 text-lg md:text-xl text-muted max-w-2xl mx-auto">
      Subheadline text
    </p>
    <div className="mt-8 flex flex-col sm:flex-row gap-4 justify-center">
      <button>CTA</button>
    </div>
  </div>
</section>
```

## 4. Dark Mode
- Use CSS variables for colors: `bg-[hsl(var(--background))]`
- Or Tailwind dark: `bg-white dark:bg-gray-950`
- Text: `text-gray-900 dark:text-white`
- Borders: `border-gray-200 dark:border-white/10`

## 5. Utility Patterns
- Truncate: `truncate` or `line-clamp-2`
- Glass: `backdrop-blur-xl bg-white/10 border border-white/20`
- Gradient text: `bg-gradient-to-r from-X to-Y bg-clip-text text-transparent`
- Focus ring: `focus:outline-none focus:ring-2 focus:ring-primary/50`
