<div align="center">

# 👟 shoes Hero Section

### An animated, fully responsive product hero section for a running-shoe brand

Built with **React 18 · TypeScript · Tailwind CSS · Vite**

![React](https://img.shields.io/badge/React-18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=for-the-badge&logo=vite&logoColor=white)

### 🔗 [**Live Demo → heroshoes.netlify.app**](https://heroshoes.netlify.app/)

[![Netlify Status](https://img.shields.io/badge/Deployed_on-Netlify-00C7B7?style=for-the-badge&logo=netlify&logoColor=white)](https://heroshoes.netlify.app/)

</div>

<!-- Add a screenshot or GIF here once you have one:
![Volterra Hero preview](./screenshots/preview.png)
-->

---

## ✨ Overview

Volterra Hero is a single-page landing hero where switching the shoe changes the **entire mood of the page at once**. The shoe image, background, headline, description, info card and accent colours all update together, with smooth transitions between colourways.

## 🎯 Features

**Colourway switching**
- Click a thumbnail or colour dot
- Use the arrow buttons or the keyboard Left / Right arrow keys
- Swipe left / right on the shoe (touch screens)
- **Auto-change every 7 seconds** with a progress bar. A plain JavaScript timer drives it, so it works even when the OS has reduced motion turned on. It pauses while the mouse is over the shoe or the controls, and while the hero is scrolled out of view. The pause button stops it until you press play again, and any manual change restarts the countdown

**Visual polish**
- Smooth background cross-fade with a slow zoom
- Drifting light particles (pure CSS, no re-renders)
- Pointer depth effect: the shoe tilts and the background shifts slightly with the mouse
- Floating shoe with a ground shadow that "breathes" with it
- Responsive layout down to phones, with a mobile menu
- Bundled Plus Jakarta Sans font (no external font requests)

**Accessibility**
- Respects `prefers-reduced-motion` for decorative animations (float, zoom, entrance effects)
- Visible keyboard focus rings
- ARIA labels and carousel semantics

## 🛠 Tech Stack

| Area | Tools |
|---|---|
| UI | React 18, TypeScript |
| Styling | Tailwind CSS 3, custom keyframe animations |
| Icons | lucide-react |
| Font | @fontsource-variable/plus-jakarta-sans |
| Build tool | Vite 5 |

## 🚀 Getting Started

**Prerequisites:** Node.js 18 or newer and npm.

```bash
# 1. Install dependencies
npm install

# 2. Start the dev server
npm run dev

# 3. Build for production
npm run build

# 4. Preview the production build
npm run preview
```

## 📁 Project Structure

```
volterra-hero/
├── index.html
├── package.json
├── tailwind.config.ts        # fonts + custom animations
├── vite.config.ts
├── tsconfig.json
└── src/
    ├── main.tsx
    ├── App.tsx               # holds the active colourway + cart count
    ├── index.css             # base styles + hero progress-bar keyframes
    ├── components/
    │   ├── Hero.tsx          # main hero section + all interaction logic + auto-change timer
    │   ├── Particles.tsx     # floating light-dust effect
    │   ├── Marquee.tsx, Shop.tsx, Technology.tsx, About.tsx,
    │   │   Reviews.tsx, Faq.tsx, Contact.tsx, Footer.tsx,
    │   │   StickyNav.tsx     # the rest of the home page
    │   └── ...               # shared helpers (Section, Reveal, Buttons, icons)
    ├── hooks/                # useInView, useScrollSpy, useTheme, ...
    ├── data/
    │   ├── variants.ts       # shoe colourways (images, colours, text)
    │   └── site.ts           # shop, tech, reviews, FAQ and footer content
    └── assets/
        ├── shoes/            # transparent WebP shoe images
        └── backgrounds/      # 16:9 background images
```

## ➕ Add or Change a Shoe

1. Add the shoe image (transparent WebP or PNG) to `src/assets/shoes/`.
2. Add its background (16:9, about 1920×1080) to `src/assets/backgrounds/`.
3. Add one entry to `VARIANTS` in `src/data/variants.ts`:

```ts
{
  id: "green",
  colorName: "Forest Green",
  dot: "#16a34a",                       // colour dot in the switcher
  accent: "#16a34a",                    // buttons, badges, active ring
  gradient: ["#86efac", "#22c55e"],     // 2nd headline line
  shoe: greenShoe,
  background: greenBg,
  badge: "New Arrival",
  headline: ["Run Wild", "Stay Grounded"],
  description: "Your product description goes here.",
  card: { icon: Leaf, title: "Eco Friendly", text: "Made with recycled materials." },
}
```

> If the new shoe image has a different shape, update `SHOE_ASPECT` in the same file.

The blue and purple shoes and backgrounds included here are colour variants generated from the original orange shoe and waterfall background. For real colourways, replace the files with your own product photos using the same file names.

## ⚙️ Customisation

| What | Where |
|---|---|
| Auto-change speed | `AUTOPLAY_MS` at the top of `src/components/Hero.tsx`. That is the only place to change: both the timer and the progress bar follow it (e.g. `4000` = 4 seconds) |
| Turn auto-change off | Set the initial `userPaused` state to `true` in `Hero.tsx`, or remove the timer `useEffect` marked `AUTO-CHANGE` |
| Progress bar look | `.hero-progress` and `@keyframes hero-progress` in `src/index.css` |
| Particle count and motion | `src/components/Particles.tsx` |
| Nav links and feature badges | `navLinks` in `src/data/site.ts` and `FEATURES` in `src/components/Hero.tsx` |
| Other animations | `keyframes` and `animation` in `tailwind.config.ts` |

## 🏠 Full home page

The hero is now the top of a complete home page. Every section reuses the hero's look (dark slate, frosted glass, big
extra-bold headlines with a gradient second line, pill buttons) and **follows the hero's active colourway**: change the
shoe and the accent colour, glow and background photos of the whole page change with it.

| Section | Nav link | File |
|---|---|---|
| Hero | Home | `components/Hero.tsx` |
| Scrolling brand strip | – | `components/Marquee.tsx` |
| 3 product cards: size picker, wishlist heart, add to bag (updates the cart badge) | Shop | `components/Shop.tsx` |
| Interactive shoe with 4 pins + feature list | Products | `components/Technology.tsx` |
| Story + animated stats on the hero's background | About | `components/About.tsx` |
| Reviews | – | `components/Reviews.tsx` |
| FAQ accordion | – | `components/Faq.tsx` |
| Contact form | Contact | `components/Contact.tsx` |
| Footer and floating glass menu (highlights the current section) | – | `Footer.tsx`, `StickyNav.tsx` |

`src/App.tsx` puts it together and holds the hero's active colourway and the cart count.

### Replace the placeholder content

Everything below the hero is placeholder copy. Edit **`src/data/site.ts`**:

- `CONTACT_EMAIL`: the contact form opens the visitor's email app addressed here (there is no backend yet).
  Replace `onSubmit` in `Contact.tsx` with a `fetch()` to your API when you have one.
- `CURRENCY`, `products` (names, prices, taglines) and `sizes`: sample shop data.
- `tech` (the stats such as "240 g"), `aboutStats`: sample figures, replace with your real ones.
- `reviews`: sample reviews tagged "Sample". Use real customer reviews, then delete `sample: true`.
- `faqs`, `marquee`, `footerColumns`: wording only; check the claims are true for your product.

Product cards are built from `VARIANTS` in `src/data/variants.ts`, so a new colourway shows up in the hero **and** the
shop automatically. Add a matching entry to `products` in `site.ts` (same `id`).

### Changes to the hero

- **Auto-change is now timer-based.** Previously the next shoe was triggered by the progress bar's CSS animation ending,
  which silently never fired when the animation was disabled (for example, Windows with "Show animations" off). A
  `setTimeout` now advances the shoe, and the progress bar uses its own `hero-progress` keyframes in `index.css`.
- Nav links, "Shop Now", "Shop Collection" and "Scroll Down" now scroll to the sections.
- The cart badge shows the live count (it starts at 2, as before).
- Auto-play rests while the hero is scrolled out of view.
- Left / Right arrow keys no longer switch the shoe while you type in a form field.
- The hero's inner `<main>` became a `<div>` (the page now has a single `<main>` in `App.tsx`).

## 🧯 Troubleshooting

**`npm run build` fails with `has no exported member 'plans' / 'addons' / 'services' / 'steps'`**
`tsc` type-checks every file in `src/`, even files nothing imports. `Options.tsx` and `Services.tsx` were leftovers from
another project and expected data that `site.ts` does not have. They are not used by this page, so delete them
(`src/components/Options.tsx`, `src/components/Services.tsx`, plus the unused `Navbar.tsx` and `data/scooters.ts`
if you have them).

**The shoe does not change by itself**
Check that the pause button is not toggled on and that your mouse is not resting over the shoe or the controls.
Auto-change also waits while the hero is scrolled out of view.

## 🌐 Deployment

The live demo is deployed on **Netlify**: [heroshoes.netlify.app](https://heroshoes.netlify.app/). The project is a static Vite app, so it also deploys easily to **Vercel** or **GitHub Pages**:

- Build command: `npm run build`
- Output directory: `dist`

## 👤 Author

**Shekhar**
- GitHub: [@iamshekhararya](https://github.com/iamshekhararya)
- Portfolio: [shekhararya.netlify.app](https://shekhararya.netlify.app)
- LinkedIn: [shekhararya90](https://linkedin.com/in/shekhararya90)
