# Four Levels of UI/UX — Mistakes to Avoid at Each Stage

Source: Tim Gabe, "4 levels of UI/UX design (and BIG mistakes to avoid)." Read this as a self-audit checklist while building or reviewing a screen — find your current level and fix the named mistakes to climb.

## Beginner — six classic mistakes

Beginner work lacks constraint systems, visual structure, and an understanding of how light and hierarchy work on a glass screen.

- **The "reverse UI" trap (color).** Random high-saturation accents used as solid backgrounds with high-contrast text create a harsh, illegible look. Use HSB (hue, saturation, brightness) to control perceived light: soft desaturated tints for container surfaces, heavy saturation reserved strictly for primary CTAs.
- **Random pixel spacing.** Subjective, hardcoded spacing kills consistency. Build on an **8-pt grid** (4, 8, 16, 24, 32…) for predictable layout harmony.
- **Unintentional contrast boundaries.** Pure black (#000000) backgrounds or absolute white (#FFFFFF) borders cause visual strain. Soften with tint opacity and subtle off-black grays.
- **Centered paragraph walls.** Centering long body text destroys the reading anchor. Left-align anything over two lines.
- **Lack of hierarchy.** Same scale, weight, and color on everything leaves no entry point.
- **Treating components independently.** Designing buttons/screens without considering how they stack and function together as a system.

## Junior — minor visual progress, major copy failures

Better color harmony and softer surfaces, but weak copywriting, loose constraints, and inconsistent font scaling.

- **Passive/broken UX copy.** Ambiguous or passive labels that don't communicate benefit. Copy must be action-oriented and clear.
- **Font-scaling misalignment.** Random sizes crowd important fields. Use a concrete modular type scale (e.g. 1.25x or 1.414x) for sound hierarchy.
- **Padding imbalance.** Narrow text in boxes with too-small internal padding. Give buttons and surfaces generous padding on the 8-pt grid.

## Mid-Level — clearer copy, but visual overworking

Clean text hierarchy, accurate grid, clear copy — but prone to over-decoration.

- **The over-styling trap.** Too many gradients, complex drop shadows, unnecessary dividers, nested card borders added just to look "designed." Premium relies on restraint.
- **Visual noise accumulation.** Multiple stylized widgets competing for the eye weaken the primary task. Remove anything that doesn't serve function or status.

## Senior — mastery of system and restraint

Absolute structural discipline: balanced whitespace, clean modular grids, desaturated foundations with high-intent accents, crisp active microcopy.

- **The hidden senior mistake:** designing layouts that look spectacular as static canvases but are nightmares to build in clean, accessible, performant code.
- **The fix:** maintain strict handoff specs, understand flexbox/grid logic, keep auto-layout clean, ensure layouts translate to a predictable, performant implementation.

## The future of UI — design experiences, not screens

Move from isolated pixel surfaces to mapping end-to-end flows, application logic states, and contextual emotional integration. The blueprint: systemized 8-pt margins, strict type scales, copy treated as a core asset, and absolute visual restraint.

## Level progression matrix

| Level | Visual execution | Type & copy | Architecture & spacing |
| :-- | :-- | :-- | :-- |
| Beginner | Random saturated fills, harsh contrast | Centered text walls, uniform weights | Subjective spacing, no grid |
| Junior | Improved palettes, soft layers | Better weights, erratic sizing | Erratic padding, tight borders |
| Mid-Level | Clean but over-styled | Crisp, clear copy | Strict 8-pt grid, clean grids |
| Senior | Absolute restraint, high-intent accents | Premium modular type system | Seamless dev handoff, systematic layouts |
