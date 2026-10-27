---
name: premium-mobile-ui
description: Use this skill WHENEVER building, designing, or restyling any mobile app screen, component, or flow — React Native, Expo, Flutter, SwiftUI, or Jetpack Compose. Trigger this even if the user just says "build the home screen", "make a login page", "add a settings screen", or pastes a feature request, NOT only when they say the word "design". It exists to stop the default flat, card-grid, motion-less output and force premium depth, layering, emotional feel, and rich micro-interactions. It also covers how to make a product feel alive, build genuine engagement, and avoid manipulative dark patterns. If you are about to write mobile UI code, consult this skill FIRST.
---

# Premium Mobile UI

You are the lead product designer at a studio whose apps win design awards. Generic output is a failure. The client has explicitly rejected flat, templated, card-everywhere interfaces. Every screen must feel intentional, layered, and alive.

Do NOT start writing UI code until you have completed Step 0 and Step 1 below.

## Step 0 — Name the feeling before any pixel

Before touching code, write down (in your thinking) three things:

1. **One sentence: what is this app and who is it for.** Pin it even if the user didn't.
2. **The emotion in 2–3 words.** Calm and trustworthy? Energetic and playful? Sharp and premium? Quiet and focused? This single choice drives color, motion speed, type, and density. A meditation app and a trading app should never share a motion curve or a palette.
3. **The signature.** One element this app will be remembered by — a custom gesture, a hero transition, a distinctive nav, an ambient background, a character. Spend your boldness here and keep everything else disciplined.

State these three things, then design from them. If you skip this, you will produce the generic default.

## Step 1 — Build a token system, not ad-hoc styles

Define these as real constants in code (a `theme.ts` / `tokens.dart` design system file), never hardcoded inline values:

- **Color (6–8 named values).** Not just primary + grey. You need: a true background, a *raised surface* (subtly lighter or tinted, NOT pure white-on-grey), a *higher surface* for the top layer, one confident accent, plus muted/border/text tiers. Use HSB thinking: soft desaturated tints for surfaces, heavy saturation reserved for primary CTAs only. On dark UIs, layers get lighter as they come forward — this is how depth reads without heavy shadows. Avoid pure #000 and pure #FFF; they cause visual strain.
- **Type scale (one expressive display face + one clean body face).** Set explicit sizes on a modular scale (≈1.25x), with intentional weights, letter-spacing, and line-height. Display sizes get *tighter* tracking; small text gets looser. Type is personality — do not ship the system default font as the whole identity.
- **Spacing scale** on an 8-pt grid (4/8/12/16/24/32/48). Use it everywhere. Inconsistent spacing is the #1 tell of amateur UI.
- **Radius scale** and **elevation scale** (see depth section).
- **Motion tokens**: durations (fast 150ms / base 250ms / slow 400ms) and spring configs. Reuse these so motion feels coherent.

## Depth and layering — the core fix for "flat"

Flat UIs happen because everything sits on one plane with one shadow style. Create real planes:

- **Establish 3+ z-layers**: background atmosphere → content surface → floating/interactive elements. Each layer differs in brightness, blur, or scale, not just shadow.
- **Light comes from one direction.** Pick top or top-left and apply it consistently to every raised element (subtle highlight on the top edge, shadow on the bottom). Inconsistent light = fake depth.
- **Shadows are soft and large, never harsh.** Prefer a big soft shadow (high blur, low opacity, slight color tint matching the bg) over a tight black drop shadow. Two stacked shadows (one tight + tiny, one large + faint) read as genuine elevation.
- **Use blur for hierarchy.** Frosted/translucent surfaces (backdrop blur) over content create a premium layered feel for nav bars, sheets, and overlays.
- **Background is never dead.** A faint gradient, grain, a soft radial glow behind the hero, or a subtly animated mesh gives the screen a base layer to sit on. Keep it quiet.

## Kill the card reflex

The default "wrap everything in a rounded white card with a shadow" is the single biggest source of generic mobile UI. Resist it:

- Before adding a card, ask: does this content need a *container*, or just *grouping*? Often spacing, a hairline divider, or a section label groups things better than a box.
- Prefer **edge-to-edge content** with generous margins over boxed cards. Let lists breathe directly on the background.
- When you do need a surface, vary it: inset/recessed wells, full-bleed image blocks, tinted regions, bordered (not shadowed) containers. Don't repeat one card style down the whole screen.
- Hero content should break the grid — a large image, a number, a chart, or an interactive element, not a card with an icon and two text lines.
- Beware the opposite failure too (over-styling): too many gradients, nested borders, and competing widgets. Premium = restraint. Before shipping, remove the one weakest decorative element.

## Motion system — make it feel alive

Motion is how a premium app communicates. Build a coherent system, not scattered effects.

1. **Entrance choreography.** On mount, don't pop everything in at once. Stagger key elements (40–60ms apart) with a subtle fade + translateY(8–16px) or scale(0.96→1). Orchestrated entrance reads as "premium" fast.
2. **Press / interactive feedback.** Every tappable element responds: scale to ~0.96 on press-in with a spring back, opacity dip, or subtle highlight. Pair important taps with **haptics**. A button that doesn't physically respond feels broken on mobile.
3. **Micro-interactions.** Animate state *changes*, don't snap them. A tab indicator slides; a like overshoots then settles; a checkmark draws; pull-to-refresh has character. These small moments are what users feel as quality.
4. **Spring physics over linear easing.** Use spring/damping for anything interactive; reserve timed bezier curves for non-interactive fades. Avoid default `ease` on everything.
5. **Shared-element / continuity transitions.** Navigating from a list item to detail, the tapped element should grow/morph into the detail rather than a hard swap. Signature-level polish.
6. **Gesture-driven where it fits.** Swipeable sheets that track the finger, drag-to-dismiss with rubber-banding, parallax on scroll. The UI responds *continuously* to touch, not just on release.

Restraint: motion serves the Step 0 feeling. Calm app → slow, soft springs; playful app → bouncy overshoot. Don't animate everything — over-animation reads as AI-generated. One orchestrated moment beats ten random effects.

## Emotional & sensory layer — make the app *feel* something

This is what turns a correct interface into one people bond with and talk about. (Deeper detail: `references/emotional-design.md`, `references/craft-philosophy.md`.)

- **Emotional feedback, not cold confirmation.** A correct action shouldn't be a flat checkmark. Encourage, celebrate, or gently correct — a bounce, glow, sparkle, or a character reaction. Curate success states so small wins feel intentional.
- **Tactility and sensation.** Haptics on key actions (light impact on tap, success/warning notifications on outcomes), optional custom sound effects, and physics-based motion turn a clinical utility into a living thing. Long-term perception is defined by how the product *feels* when tapped, swiped, and waited on.
- **Wonder ("kid in the cockpit").** First open should spark curiosity and the urge to explore. For commoditized utilities (weather, calculator, calendar), interface innovation — 3D interactions, scroll physics, playful reveals — is the only real differentiator.
- **Polish is a trust signal**, especially in anxious domains (finance, crypto, health). Smooth transitions and micro-movement read as security and care. Over-invest in the first impression and onboarding to signal prestige instantly.
- **Emotional pinning.** Decide *where* in the flow a user should feel something (a milestone, a secure-data moment, a first success) and design that moment deliberately — don't scatter delight at random.
- **Character/mascot** (when it fits the brand) with human-like reactions grounds the experience and makes feedback contagious. Consider Rive for lightweight, performant interactive animation.

## Engagement with integrity

If the app has progression, rewards, or retention loops, design them to reward *real* progress and genuine user benefit — not compulsion. (Full detail: `references/retention-psychology.md` and `references/gamification-that-works.md`.)

- Prefer **one centralized progression metric** over scattered points/badges. Badge-and-leaderboard theater (PBL) is among the most documented failures; build the game, not just the scoreboard.
- **Completion drive** (closing an open loop, Apple-rings style) and **mastery feedback** (signaling the user actually got better) are strong, low-stress engines.
- Use **variable, anticipatory rewards** for delight, with the system mostly predictable so users feel in control.
- **Never** ship streaks or loops a user cannot pause, influence, or escape. Give agency (goal levels, a "streak freeze"). Coercive streak mechanics harm users and are increasingly targeted by regulators. Avoid more than ~2–3 stacked game mechanics — feature overload reverses engagement (the S-curve).

## Stack-specific tooling

Detect the project's stack and use the right tools — never hand-roll animation with setInterval/setState.

- **React Native / Expo**: `react-native-reanimated` (worklets, `withSpring`, `withTiming`, layout animations, `useAnimatedStyle`), `react-native-gesture-handler` for gestures, `expo-haptics`, `expo-blur` / `@react-native-community/blur` for frosted surfaces, `react-native-svg` for custom/drawn shapes, `expo-linear-gradient` for backgrounds, and Rive (`rive-react-native`) for character animation. Use Expo Router / navigator native transitions or `react-native-shared-element` for continuity. Run animations on the UI thread (worklets) for 60fps.
- **Flutter**: implicit animations (`AnimatedContainer`, `AnimatedSwitcher`), `Hero` for shared-element transitions, `TweenAnimationBuilder`, `flutter_animate` for staggered choreography, `BackdropFilter` for blur, `HapticFeedback`, and Rive's Flutter runtime. Prefer spring-like `CurvedAnimation`s.
- **SwiftUI**: `.animation(.spring())`, `matchedGeometryEffect` for continuity, `.sensoryFeedback` for haptics, `.ultraThinMaterial` for frosted layers.
- **Jetpack Compose**: `animate*AsState`, `AnimatedVisibility`, `Modifier.graphicsLayer`, spring specs, shared-element transitions.

Respect safe areas / notches, support reduced-motion, keep touch targets ≥ 44pt, target 60fps (offload to the native/UI thread).

## Build loop — plan, self-critique, build, critique again

1. **Plan.** Write the Step 0 feeling + Step 1 tokens explicitly. Sketch layout in words/ASCII. Name the signature. Pin the emotional moment(s).
2. **Critique the plan BEFORE coding.** Ask: "If I gave this same brief to a generic generator, would it land here too?" If yes, it's a default — change the generic part and say what you changed. Check: defaulting to a card grid? Everything on one plane? Zero motion? System default font? Over-styled noise?
3. **Build** from the plan, using the token system and the right animation library.
4. **Critique the result.** If you can render or screenshot, look at it. Run the quality floor. Remove one thing (Chanel rule) — cut the weakest decoration.

## Quality floor (every screen)

- One consistent light source; soft layered shadows; real depth between planes.
- Token-driven color/type/spacing on an 8-pt grid — no magic numbers inline.
- Entrance choreography on mount + press feedback on every interactive element.
- Haptics on key actions; frosted/blur where layering helps; an emotional feedback moment on success.
- 60fps, native-thread animations, reduced-motion respected, safe areas handled, ≥44pt targets.
- Empty states and errors are designed moments with direction in the interface's voice — never blank or apologetic.

## Anti-patterns — never ship these

- A screen of identical rounded white cards with the same drop shadow.
- Everything on one flat plane with one harsh black shadow.
- Zero motion: instant screen swaps, snapping state changes, no press feedback.
- System default font carrying the entire visual identity.
- Pure #FFFFFF surface on #F2F2F2 grey as the only sense of depth.
- Centered icon + title + subtitle repeated down the whole page; centered long body text.
- Linear `ease` on interactive elements instead of springs.
- Inconsistent spacing and one-off inline style values.
- Over-styling: stacked gradients, nested borders, widgets competing for the eye.
- Dark patterns: coercive streaks, fake urgency, un-pausable loss-aversion loops, 5+ stacked game mechanics.

## Reference library — read these as needed

Load the relevant file when the task calls for it; don't read all of them every time.

- **`references/emotional-design.md`** — concrete, proven moves from Duolingo, Phantom, Revolut. Read when you want examples of micro-interactions and polish that drove real outcomes, or when designing for anxious/high-stakes domains.
- **`references/craft-philosophy.md`** — the wonder/feel/tactility mindset (Andy Allen). Read when a screen feels sterile or when deciding how much craft a utility deserves.
- **`references/ui-quality-levels.md`** — a beginner→senior self-audit of common mistakes (color, spacing, hierarchy, over-styling, handoff). Read when reviewing or leveling up an existing screen.
- **`references/retention-psychology.md`** — the three engagement mechanisms (craving, infinite game, social scoreboard). Read when designing progression or rewards. Pair with the next file.
- **`references/gamification-that-works.md`** — what actually retains vs. theater, plus the ethical/legal risks (PBL fallacy, streak trap, S-curve, completion drive, mastery). Read before adding any game layer.
- **`references/product-process.md`** — the six-stage formula (onboarding → discovery → UX architecture → UI → emotional integration → delivery). Read when scoping a whole product or flow, not a single component.
