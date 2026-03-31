---
name: vulk-gsap
description: "Official GSAP patterns: core API, ScrollTrigger, timelines, React integration. Use for premium scroll animations, parallax, pinned sections, and complex sequencing. Triggers: gsap, greensock, scrolltrigger, scroll animation, parallax, pin, scrub, timeline animation, scroll-driven, scroll reveal, advanced animation"
license: MIT
---

# GSAP (GreenSock) -- Correct Patterns

When using GSAP instead of Framer Motion (prefer GSAP for scroll-driven, pinned, and complex sequenced animations).

## 1. Installation and Setup

```bash
npm install gsap @gsap/react
```

```javascript
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { useGSAP } from "@gsap/react";
gsap.registerPlugin(useGSAP, ScrollTrigger);
```

## 2. React Integration (useGSAP -- REQUIRED)

```jsx
import { useRef } from "react";
import { useGSAP } from "@gsap/react";
import gsap from "gsap";
gsap.registerPlugin(useGSAP);

function Component() {
  const container = useRef(null);
  useGSAP(() => {
    gsap.to(".box", { x: 100, duration: 0.6, ease: "power2.out" });
  }, { scope: container });
  return <div ref={container}><div className="box">...</div></div>;
}
```

- Always use `useGSAP` with `scope` (NOT useEffect)
- Register useGSAP as a plugin before use
- Cleanup is automatic (no manual kill/revert needed)
- NEVER use bare useEffect for GSAP -- cleanup breaks

## 3. Core Tweens (prefer transform aliases)

```javascript
// Correct -- use x/y (transform), autoAlpha (opacity + visibility)
gsap.to(".el", { x: 100, autoAlpha: 1, duration: 0.6, ease: "power2.inOut" });
// Wrong -- layout props cause reflow
gsap.to(".el", { left: 100, opacity: 1 }); // triggers layout
```

## 4. Timeline (sequence multiple animations)

```javascript
const tl = gsap.timeline({ defaults: { duration: 0.5, ease: "power2" } });
tl.to(".a", { x: 100 })
  .to(".b", { y: 50 }, "+=0.2")   // 0.2s after previous ends
  .to(".c", { opacity: 0 }, "<")   // same start as previous
  .to(".d", { scale: 2 }, "<0.2"); // 0.2s after previous starts
```

Position parameter: `"<"` = start with previous, `">"` = after previous, `"+=0.2"` = gap, `"-=0.1"` = overlap

## 5. ScrollTrigger (scroll-linked animations)

```javascript
gsap.registerPlugin(ScrollTrigger);

// Basic trigger
gsap.to(".box", {
  x: 500,
  scrollTrigger: {
    trigger: ".box",
    start: "top center",
    end: "bottom center",
    toggleActions: "play reverse play reverse",
  }
});

// Timeline with ScrollTrigger
const tl = gsap.timeline({
  scrollTrigger: {
    trigger: ".section",
    start: "top top",
    end: "+=200%",
    scrub: 1,
    pin: true,
  }
});
tl.to(".panel1", { xPercent: -100 })
  .to(".panel2", { xPercent: -100 });
```

## 6. Stagger (animate multiple elements)

```javascript
gsap.from(".card", {
  y: 60, autoAlpha: 0, duration: 0.8,
  stagger: { each: 0.15, from: "start" },
  scrollTrigger: { trigger: ".cards", start: "top 80%" }
});
```

## 7. Performance Rules
- Only animate transform (x, y, scale, rotation) and opacity
- Use `will-change: transform` on animated elements
- Use `gsap.quickTo()` for frequently updated values (mouse followers)
- Never animate width, height, top, left, margin, padding
- Never create new timelines every frame

## 8. Common Plugins
- `ScrollToPlugin`: `gsap.to(window, { scrollTo: "#section" })`
- `Flip`: layout animation (before to after state)
- `SplitText`: split text into chars/words/lines for animation
- `Draggable`: make elements draggable
- `Observer`: normalized input events (scroll, touch, pointer)
- All require: `import { Plugin } from "gsap/Plugin"; gsap.registerPlugin(Plugin);`

## 9. Easing Reference
- Smooth: `"power2.out"` (default good choice)
- Snappy: `"power3.out"`, `"back.out(1.7)"`
- Bouncy: `"bounce.out"`, `"elastic.out(1, 0.3)"`
- Linear scroll: `"none"` (for scrub timelines)
