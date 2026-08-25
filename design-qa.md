# Design QA

## Comparison target

- Source visual truth: `C:\Users\power\Documents\ChatGPT\WITTENSTTEIN\.audit\wittenstein-2026-08-14\desktop-viewport.png`
- Source mobile visual: `C:\Users\power\Documents\ChatGPT\WITTENSTTEIN\.audit\wittenstein-2026-08-14\mobile-viewport.png`
- Implementation desktop: `.preview/desktop-final.png`
- Implementation mobile: `.preview/mobile-final.png`
- Local implementation URL: `http://127.0.0.1:4173/`
- State: initial page load, dark theme, background video playing

## Normalization

- Desktop CSS viewport: 1280 x 800; source and implementation captures: 1265 x 791 px.
- Mobile CSS viewport: 390 x 844; source and implementation captures: 375 x 812 px.
- Browser chrome and scrollbar account for the capture dimensions. Source and implementation use matching viewports and density.

## Full-view comparison evidence

- The original hero composition, video treatment, four-column desktop grid, one-column mobile grid, product imagery, and page density remain intact.
- The implementation adds the supplied WITTENSTEIN SVG logo without replacing or redrawing the source asset.
- Brand teal is limited to the eyebrow, product numbering, link affordance, card border interaction, and keyboard focus.
- Korean copy is visibly larger and brighter while preserving the original hierarchy.

## Focused region comparison evidence

- Hero: the supplied logo renders at its native aspect ratio; the Korean description is 17 px desktop and 16 px mobile with increased contrast.
- Product cards: titles render at 17 px desktop / 18 px mobile; descriptions render at 14 px with 1.6 line height and 72% white.
- Interaction: all eight cards include `제품 보기`, safe new-tab attributes, hover feedback, and a 3 px teal keyboard-focus inset.
- Assets: the logo, eight card images, and video all load. Video ready state is 4. No horizontal overflow was detected.

## Required fidelity surfaces

- Fonts and typography: Pretendard Variable is self-hosted for Korean; Inter remains on the Latin brand display text. Wrapping is stable at both tested viewports.
- Spacing and layout rhythm: hero and grid proportions are preserved. Card copy padding and vertical rhythm were increased for readability.
- Colors and visual tokens: the supplied identity family is represented by `#649ba8` and `#8bbdc8`, with the existing near-black background retained.
- Image quality and asset fidelity: supplied vector logo and existing source product/video assets are used directly. No placeholder or code-drawn replacement is present.
- Copy and content: original product names and descriptions are unchanged; `제품 보기` is the only added action label.

## Comparison history

### Iteration 1

- [P2] The `제품 / 8개 카테고리` header remained underneath the hero stacking context because of the original negative shelf margin.
- Fix: made the shelf a positioned stacking layer above the hero.
- Post-fix evidence: the header is visible at desktop and mobile sizes and precedes the first card without overlap.

### Iteration 2

- No actionable P0, P1, or P2 findings remain.
- Console warnings/errors: none.
- Primary interactions checked: card link semantics, new-tab safety attributes, hover styling, keyboard focus, responsive reflow.

## Follow-up polish

- [P3] The logo plaque size can be tuned after the user chooses whether the official mark should feel prominent or understated.

final result: passed

---

# Sizing Tools Design QA

## Comparison target

- Source visual truth: `artifacts/sizing-tools-selected-reference.png`
- Implementation mobile: `artifacts/sizing-tools-mobile-final.png`
- Full-view comparison: `artifacts/sizing-tools-compare-final.png`
- Implementation desktop: `artifacts/sizing-tools-desktop-final.png`
- Current hero source: user-provided WITTENSTEIN company header video with the cybertronic drive systems image retained as the fallback poster.
- Local implementation URL: `http://127.0.0.1:8796/sizing-tools/`
- State: initial page load with all three official sizing-tool choices and the FAtec consultation action visible.

## Normalization

- Source pixels: 852 x 1846.
- Mobile implementation pixels and CSS viewport: 390 x 844 at browser device scale 1.
- Comparison image: both source and implementation normalized to 390 x 844 and placed side by side.
- Desktop implementation viewport: 1280 x 900.

## Full-view comparison evidence

- The final mobile composition preserves the selected split structure: dark motion hero, overlapping white selection sheet, three outlined tool cards with interactive teal hover states, and a compact consultation strip.
- The top marks use only `WITTENSTEIN` and the exact requested `FAtec` capitalization; `alpha` and `SYSTEM` are absent.
- All three tools and the consultation action fit within the 390 x 844 first screen.
- The exact brand accent `#6FA2AE` is used for the primary selector and supporting rules/actions.

## Focused region comparison evidence

- A separate focused crop was not required because the normalized full-view comparison keeps the brand marks, hero copy, product names, metadata, and action labels readable at the target mobile width.
- Browser DOM inspection additionally confirmed the exact `FAtec` text, Korean labels, official destination URLs, and link accessibility names.
- Individual source assets were opened before implementation; the final browser capture confirms that the hero, WITTENSTEIN logo, three tool images, and icon asset all render without placeholders.

## Required fidelity surfaces

- Fonts and typography: local Pretendard Variable and Inter assets reproduce the selected Korean/Latin hierarchy; the headline wraps in two lines and all tool names remain readable.
- Spacing and layout rhythm: the hero-to-sheet transition aligns with the source, the three selectors use a consistent 122 px mobile rhythm, and the total page height is 844 px at the target viewport.
- Colors and visual tokens: near-black, white, graphite, and exact `#6FA2AE` are used without substitute blues or gradients.
- Image quality and asset fidelity: the user-provided WITTENSTEIN WEBM is used as the current hero with the supplied cybertronic image as its fallback poster; official WITTENSTEIN tool-laptop captures and the supplied WITTENSTEIN SVG logo are used directly. No placeholder or code-drawn visual asset remains.
- Copy and content: the hero, three use-case labels, metadata, actions, consultation text, `WITTENSTEIN`, and `FAtec` match the selected direction and latest user correction.

## Comparison history

### Iteration 1

- [P1] The initial mobile hero and selector rows were too tall, pushing the third tool and consultation action below the first screen.
- Fix: reduced the mobile hero to 358 px, tightened the selector rhythm, and adjusted typography while retaining legible touch targets.
- Post-fix evidence: `artifacts/sizing-tools-mobile-final.png` shows all three tools and consultation action within the 390 x 844 viewport.

### Iteration 2

- [P2] Tool laptop images appeared too small because their source crops retained excessive whitespace, and the hero machinery dominated the text region.
- Fix: recropped each official laptop image around the product and constrained the mobile hero image to the right 72% of the hero.
- Post-fix evidence: `artifacts/sizing-tools-compare-final.png` shows closer visual scale and clearer separation between copy and machinery.

### Iteration 3 — hero replacement

- User direction: replace the generated gearbox hero with the supplied WITTENSTEIN cybertronic drive systems image.
- Fix: switched to `hero-cybertronic-drive.webp`, restored full-width mobile coverage, and set desktop/mobile focal positions to keep the engineer and holographic product sequence visible.
- Post-fix evidence: visual browser review at desktop and mobile sizes confirms readable hero copy, uncropped brand marks, and a balanced subject position.

### Iteration 4 — interaction, rounding, and motion hero

- User direction: remove the permanently teal first card, apply teal only to the card under the pointer, round all major cards/sections like an iPhone app, and replace the hero image with the supplied WITTENSTEIN WEBM.
- Fix: all three tools now share the same white default state and independent `#6FA2AE` hover/focus state; desktop/mobile card radii are 18/14 px, the selection sheet uses 24/18 px, and the hero video autoplays muted, loops, and plays inline with a poster fallback.
- Post-fix evidence: browser interaction checks returned one teal card and two white cards for each of the three pointer positions. The video reported `paused: false`, `muted: true`, `loop: true`, and `readyState: 4`.

### Iteration 5 — official stacked WITTENSTEIN mark

- User direction: replace the hero's previous horizontal WITTENSTEIN logo with the supplied `WITTENSTEIN SE.svg` artwork.
- Fix: the supplied SVG is referenced directly from the local brand assets and presented at its native stacked aspect ratio on a compact translucent-white plate, preserving the original gradient mark and dark wordmark over the moving hero.
- Post-fix evidence: desktop and 390 px mobile browser captures confirm uncropped rendering, a balanced lockup against `FAtec`, and clear separation from the hero copy. The browser reports the exact 1107 x 914 SVG natural dimensions and the new local asset path.

### Final checks

- Browser console warnings/errors: none.
- Horizontal overflow: none at 1280 x 900 (`1265 / 1265` client/scroll width) or 390 x 844 (`390 / 390`).
- Mobile first-screen fit: page height is exactly 844 px; the third tool ends at 725 px and the consultation action ends at 791 px.
- Updated rounded layout fit: at 390 x 844 the consultation section ends at 803 px, with `390 / 390` client/scroll width and no clipping.
- Primary interactions checked: three official external destinations, safe new-tab attributes, consultation email target, hover/focus styles, and responsive layout.
- Asset delivery: the 1920 x 1080 VP9 hero video loads and autoplays; all page images load with non-zero natural dimensions; the direct page console is clear.
- Logo delivery: `wittenstein-se-logo.svg` loads at its full 1107 x 914 intrinsic size, retains the source gradients, and remains inside the rounded brand plate without distortion on desktop or mobile.

## Follow-up polish

- [P3] The tool screenshots are intentionally faithful crops from the official page and therefore softer than the generated reference artwork at high zoom.

final result: passed
