# Jackpot Wheel — Skin Guide

Graphics are split into two folders:

- **`skin/`** — everything you replace to give the wheel a new visual identity. Keep filenames identical when swapping.
- **`assets/`** — coin-rain sprites, shared across skins (rarely need to change).
- **`audio/`** — all sound clips (music, SFX, voice).

## `skin/` — reskin these

| File | Role | Source resolution | Notes |
|---|---|---|---|
| `wheel-base.png` | The spinning colored disc, 16 equal sectors, no text | 2118×2118 (square, transparent) | Rendered at 360×360; sector 0 starts at 12 o'clock, sectors run clockwise, each 22.5° wide. Text labels are drawn separately in HTML on top, rotating with this image |
| `wheel-frame.png` | Static outer rim/frame | 2118×2118 (square, transparent), same canvas as `wheel-base.png` | Overlaid at the same 360×360 box but does NOT rotate — sits fixed while the disc spins underneath |
| `marker.png` | Pointer/indicator at bottom of wheel | 396×801 (transparent), tip pointing up | Positioned independently of wheel scaling; tip should point up toward the wheel center |
| `icon_default.png` | Closed chest (shown while spinning) | 275×275 (square, transparent) | |
| `icon_mini.png` | Open chest — Mini tier | same aspect as `icon_default` | No flames |
| `icon_minor.png` | Open chest — Minor tier | same aspect | Light glow |
| `icon_major.png` | Open chest — Major tier | same aspect | Stronger fire |
| `icon_super.png` | Open chest — Jackpot do Fogo (top tier) | same aspect | Largest flames/gold |
| `image-88.png` | "KTO Jackpot de Fogo" logo/banner art | 574×256 (transparent) | Used above wheel and on win screen |

## `assets/` — usually untouched

| File | Role |
|---|---|
| `coin0.png`–`coin10.png` | Coin-rain sprites (10 variants) |

## `audio/` — all sound

| File | Role |
|---|---|
| `short_dramatic.mp3` | Background loop |
| `countdown-sine-wave-beeps.mp3` | Countdown beeps |
| `win-loop.mp3` | Win ambience loop |
| `coins-drop.wav` | Coin-drop SFX |
| `reel-spin.wav` | Wheel ratchet SFX while spinning |

## Rules for a clean re-skin
- Keep transparent PNGs transparent (chest icons, wheel ring, pointer, logo) — they sit over the background and glow effects.
- Keep `wheel-base.png` and `wheel-frame.png` square, same canvas size, and centered; the 16-sector order (repeating Mini/Minor/Major/Mega/No Win, ×2, with an extra Mini/Minor/Major run in between) is baked into the code's `SECTORS` array by angle, not read from the art — swap colors freely but don't change sector count/order without updating `SECTORS` in `index.html`.
- The wheel never lands on a "No Win" sector — it's excluded from the random/weighted target pool, purely cosmetic.
- Chest icons should share the same canvas size/anchor point across all 5 (`icon_default` + 4 tiers) so they don't jump when swapped mid-animation.
- Tier colors (title, halo, fire tint) are set in code (`TIERS` array in `index.html`), not baked into the art — update them there if the new skin needs different accent colors.
