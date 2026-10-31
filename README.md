# Volterra Hero (React + TypeScript + Tailwind)

```bash
npm install
npm run dev
```

## What it does
Switch shoes and the **shoe, background, headline, description, info card and accent colours all change together.**

Ways to switch:
- click a thumbnail or colour dot
- arrow buttons, or the Left / Right arrow keys
- swipe left / right on the shoe (touch screens)
- auto-play every 7 s (progress bar shows the timing; pauses while the mouse is over the shoe or the controls, and the pause button stops it for good)

## Polish included
- Smooth cross-fade + slow zoom on the background, drifting light particles
- Pointer depth effect: shoe tilts and background shifts slightly with the mouse
- Shoe floats with a ground shadow that breathes with it
- Mobile menu, responsive down to phones, bundled Plus Jakarta Sans font (no external requests)
- Respects `prefers-reduced-motion`, keyboard focus rings, ARIA labels, carousel semantics

## Add / change a shoe
1. Put the shoe image (transparent WebP/PNG) in `src/assets/shoes/`
2. Put its background in `src/assets/backgrounds/` (16:9, about 1920x1080)
3. Add one entry to `VARIANTS` in `src/data/variants.ts` with the text and colours you want

If the new shoe image has a different shape, update `SHOE_ASPECT` in the same file.

The blue and purple shoes and backgrounds shipped here are colour variants generated from the
original orange shoe and the waterfall background. For real colourways, just replace the
files with your own product photos using the same file names.

## Tweaks
- Auto-play speed: `AUTOPLAY_MS` at the top of `src/components/Hero.tsx` (also change `progress 7s` in `tailwind.config.ts`; the inline duration already follows `AUTOPLAY_MS`)
- Particles: `src/components/Particles.tsx`
"# herosection" 
"# herosection" 
