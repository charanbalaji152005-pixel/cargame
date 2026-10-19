# Hill Climber (SVG + Matter.js)

A side-scrolling hill-climb driving game rebuilt from a screen recording.
Everything on screen is **SVG** (sky, sun, parallax clouds / mountains / pine hills, road, buggy, wheels, crates, bridge)
and the motion is driven by the **Matter.js** physics engine.

## Setup
Requires Node.js 18+.

```bash
npm install
npm run dev        # http://localhost:5173
```
Production build: `npm run build` (output in `dist/`), preview with `npm run preview`.
Serve `dist/` from any static host (don't open it via `file://`, ES modules need http).

### Deploy to GitHub Pages
```bash
npm run deploy
```
Live Demo: [https://charanbalaji152005-pixel.github.io/cargame/](https://charanbalaji152005-pixel.github.io/cargame/)


## Controls
| Action | Keyboard | Touch |
|---|---|---|
| Drive | D / → | ▶ (bottom-left) |
| Tilt / Flip (brake on ground) | A / ← | ◀ (bottom-left) |
| Jump | W / ↑ | ⤒ (bottom-right) |
| Nitro | SPACE | 🔥 (bottom-right) |
| Restart | R | – |
| Pause | P / Esc | ❚❚ button |

Any key / tap restarts after a crash. The ◀ ▶ arrows next to "STAGE 1 / 5" switch stages.

## Project layout
```
index.html            HUD, hints bar, touch buttons, modal markup
src/main.js           game loop, Matter.js world, car, crates, bridge, camera, input, HUD
src/levels.js         stage definitions (stage 1 = route from the video, 2-5 procedural)
src/scene.js          layered parallax SVG backdrop
src/assets.js         loads the SVG files as raw markup
src/assets/*.svg      car-body, wheel, crate, cloud, mountain, sun, tree artwork (edit freely)
src/audio.js          Playful WebAudio synthesizer (cartoon engine, spring jumps, crate breaks, fanfare, crash & BGM)
src/style.css         HUD / modal styling
```

## Tweaking
* Road layout: edit the token lists in `src/levels.js`.
* Handling: wheel torque, jump (`y: -11`), nitro force (`0.01`) and suspension stiffness are in `src/main.js`.
* Art: replace any SVG in `src/assets/` (keep it centred on 0,0 – the physics body position is the SVG origin).
