# Nival — Cyberspace Identity

A single-file, framework-free landing page for a fictional digital-identity studio.
Its signature feature is a **cursor-following spotlight reveal** that unmasks a
heavy armored android through a soft radial alpha mask laid over a lighter one.

> Everything — HTML, CSS and JavaScript — lives inline in **one `index.html`**.
> No build step, no dependencies, no local assets. Just open the file.

**Live-ready:** open `index.html` in any modern browser.

---

## ✨ Highlights

- **Spotlight reveal** — a `<canvas>`-generated radial alpha mask is painted onto the
  back hero image every frame and eased toward the pointer at 10 %/frame, revealing
  the dark armored variant only inside a soft-edged circle.
- **Fixed design canvas** — the layout is authored on a fixed 1536 × 1024 "stage"
  that is CSS-`transform`-scaled to fit any viewport, so proportions never break.
- **Three responsive tiers**
  - **A** — desktop / landscape (scaled 1536 × 1024 canvas)
  - **B** — portrait-ish screens (scaled 640 × 1366 canvas + container-query relax)
  - **C** — real phones (a natural, scrolling CSS **grid** — the scaled canvas is abandoned)
- **Cinematic entrance** — a Web Animations API timeline reveals every element once,
  then freezes the page completely static. A blocking guard + 5 s safety net guarantee
  the page can never stay hidden.
- **Glassmorphism UI** — frosted nav pill, join button, info card and mobile menu.
- **Fully accessible** — labelled icon buttons, `aria-expanded` / `aria-pressed` /
  `aria-hidden` state, a polite live-region toast, visible focus rings, and a complete
  `prefers-reduced-motion` guard.

---

## 🧠 The spotlight, done right

The drop-shadow / hue-rotate / saturate filters live on **`.hero-front`**, never on the
`.hero` parent. A filter on the parent would apply the drop-shadow to the *combined*
alpha of both layers, so the revealed spotlight blob would cast a dark navy halo into
the empty background. Keeping the filter on the front image alone eliminates that artifact.

The `.stage` ancestor is `transform`-scaled, so `getBoundingClientRect()` returns
*rendered* pixels while the mask lives in the element's own *unscaled* 600 × 759 space.
The pointer handler divides by that scale (`offsetWidth / rect.width`) so the spotlight
tracks the cursor exactly instead of drifting.

---

## 🎛️ Interactions

| Control | Behaviour |
|---|---|
| Hero | Move the cursor over it to reveal the armored variant through the spotlight |
| Nav / menu links | Sync the active state across both the desktop pill and the mobile panel |
| Hamburger | Opens the glass menu panel in compact mode (Esc / outside-click closes it) |
| Join | Toggles between **Join us** / **Joined** on both buttons |
| ▶ Play | Activates the "awake" breathing animation on the hero |
| 👁 Eye | Toggles a live preview of the identity |
| Avatar gallery / shuffle / next | Re-tints the hero (hue + saturation) per identity |
| Socials | Toast confirmation |

Every action surfaces a short status toast.

---

## 📁 Structure

```
.
├── index.html   ← the entire app (HTML + inline CSS + inline JS)
├── README.md
└── LICENSE
```

## ▶ Run it

No tooling required:

```bash
# just open it
start index.html      # Windows
open index.html       # macOS
```

or drag `index.html` into a browser tab.

---

## 🛠️ Tech

Vanilla HTML5 · modern CSS (container queries, CSS masks, `svh`, `clamp()`) ·
vanilla JavaScript (Canvas 2D, Web Animations API, Pointer Events). Inter via Google Fonts.

## 📄 License

[MIT](LICENSE) © Nikolay Stoyanov
