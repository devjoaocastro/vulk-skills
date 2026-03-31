---
name: vulk-layouts
description: "Professional page layouts and section patterns. Loaded for landing pages and multi-page sites. Triggers: landing, website, page, hero, section, footer, header, navbar, layout, corporate, portfolio, saas"
license: MIT
---

# Layouts -- Professional Page Structure

## 1. Page Order (proven conversion pattern)
Hero -> Trust bar (logos) -> Features/Benefits -> How it Works -> Testimonials -> Pricing -> CTA -> Footer

## 2. Header/Navbar (CRITICAL)
- Fixed/sticky at top with backdrop-blur
- Height: 64-80px
- Logo left, nav center, CTA right
- Mobile: hamburger menu with slide-in drawer
- Transparent on hero, solid on scroll
- z-index: 50

## 3. Hero Section (CRITICAL -- most visible)
- MUST have pt-24 minimum to clear fixed header
- Full viewport or 85vh minimum
- Centered content, max-w-4xl for text
- Headline: biggest text on page (text-5xl to text-7xl)
- Subheadline: 1-2 sentences max, muted color
- 1-2 CTA buttons (primary + secondary/ghost)
- Optional: background image/gradient, floating elements

## 4. Section Pattern

```jsx
<section className="py-20 md:py-28 lg:py-32">
  <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    {/* Eyebrow */}
    <p className="text-sm font-medium text-primary uppercase tracking-wider">Features</p>
    {/* Heading */}
    <h2 className="mt-3 text-3xl md:text-4xl font-bold">Section Title</h2>
    {/* Description */}
    <p className="mt-4 text-lg text-muted max-w-2xl">Description text</p>
    {/* Content */}
    <div className="mt-12 grid grid-cols-1 md:grid-cols-3 gap-8">
      {/* Cards */}
    </div>
  </div>
</section>
```

## 5. Footer
- 4-column grid: Brand + 3 link groups
- Logo + tagline + social icons in first column
- Bottom bar: copyright + legal links
- Border-top separator
- Muted colors, small text (text-sm)

## 6. Multi-Page Routing

```jsx
// App.tsx with React Router
<Routes>
  <Route element={<MainLayout />}>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
    <Route path="/services" element={<Services />} />
    <Route path="/contact" element={<Contact />} />
  </Route>
  <Route path="/login" element={<Login />} />
  <Route path="/admin" element={<ProtectedRoute><AdminLayout /></ProtectedRoute>}>
    <Route index element={<Dashboard />} />
    <Route path="users" element={<Users />} />
  </Route>
</Routes>
```
