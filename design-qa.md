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
