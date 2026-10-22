# Exploration 25 — Typography Design System

Exploration 25 preserves Exploration 24's interface, navigation and intro while establishing a consistent, device-independent typography system for the prototype.

## Shared design-system foundation

- `DESIGN.md` now defines three token layers: primitives, semantic roles and narrowly scoped component tokens.
- Components consume semantic roles. Raw palette values, arbitrary spacing and local stroke widths are not component API.
- Color, typography, spacing, corners and strokes each have primitive scales with semantic mappings that can be shared by Figma, CSS and Roku constants.
- Content count never creates a typography, corner or stroke variant. A two-outcome card and a five-outcome card share the same visual grammar.
- Roku component strokes use only 3 px and 6 px at the 1920×1080 authoring canvas. These become exact 2 px and 4 px device strokes at 1280×720.
- Subtle, standard and strong boundaries vary opacity and semantic role; no component uses a fractional TV stroke.
- The focus ring is 6 px with a 3 px external offset. Clipping containers provide at least 12 px of internal clearance for the full external paint area.

## Typography baseline

- Inter is the single bundled prototype family for body, display and numeric roles. This removes the platform-dependent mixture of Helvetica/System UI and Avenir Next Condensed caused by unavailable `kalshiSans` and `kalshiCondensed` files.
- Body, display and numeric remain separate semantic tokens. Licensed Kalshi faces can replace those token values later without rewriting component CSS.
- Component typography is expressed through named tokens instead of relying on the apparent size of unrelated fallback families.
- Event-card eyebrows use Inter Medium at 20/24, one weight step below the previous 600 treatment.
- Event-card questions use one shared Inter Medium style at 30/36 and are clamped to two lines with an ellipsis when the text exceeds the available space.
- Navigation tabs use Inter Semibold at 24/30. Because tabs and questions now share the same family, their 24 px versus 30 px hierarchy is visually measurable and consistent across review devices.
- Every outcome row now uses the same typography regardless of whether an event has one, two or five markets: name 24/30 Medium, multiplier 20/24 Medium and current probability 28/34 SemiBold.
- Market count affects available spacing and D-pad scrolling only. It no longer enlarges type to fill otherwise empty card space.
- Series colors and chart encoding remain unchanged.

## Entry sequence

1. The viewer focuses the contextual prediction prompt and presses OK.
2. The final 576 px panel space opens beside the broadcast with a black surface.
3. Tappp's three equal-outer-diameter circles draw sequentially and clockwise in Kalshi green. Their internal weights differ; the third circle fills continuously as it draws.
4. A solid Kalshi-green field expands from the middle circle and reveals `AD SPACE` through a centered mask.
5. The completed advertising state remains visible for three seconds.
6. The interstitial fades out, then the unchanged product panel enters and begins its initial skeleton-loading sequence.

Back during the interstitial cancels it and restores focus to the same prompt. All other remote input is ignored until the intro finishes. The interstitial is an isolated prototype placeholder; no advertising platform, campaign content, or production ad behavior is implied.

## Objective

Improve comprehension of live market movement on TV by giving the selected market's probability history more space and removing secondary content that competes with the decision.

## Baseline

- Exploration 22 provides the chart-focused functional and visual baseline.
- Exploration 22 remains unchanged.
- Trading simulation, QR handoff, team identity and remote navigation are preserved.
- The persistent header is reduced to Kalshi branding. Trade, Positions and Balance are removed from the visible and focusable navigation model.
- Loading progress overlays the divider directly below the Kalshi logo so it remains inside the TV-safe panel area.
- Up from the category tabs or a contextual-navigation pill stops at that row, so the D-pad never lands on an invisible header destination.

## Chart pattern

- Event cards show one curve per listed outcome. Each curve represents that outcome market's Yes probability and matches the outcome color used in the list.
- Market detail shows one historical curve: the Yes probability of the selected outcome. No remains available in the trading controls as the complementary side, without duplicating the chart with a mirrored line.
- Market detail uses the Game history with `Kickoff / Halftime / Q4 · 2:14` anchors. The redundant chart title and Live / Game / All selector are removed so the visualization receives the full available vertical area.
- Read-only audience comments are removed from Market Detail. Their space is reassigned to the chart, which grows from 104 px to 180 px while trading controls retain their established sizes.
- Simulated activity continues to rise beside the visualization; live percentages, curve endpoints and halos update in place.
- Every event-card curve ends with the current percentage for that same outcome. The endpoint label and outcome row share one value and update together; when several labels cluster, the labels separate vertically and retain short color-matched connectors to their curves.

## Why this is more effective on TV

- The shape of each curve communicates direction, volatility and crossings over time.
- Multi-outcome questions remain comparable in the event card, where all outcomes share one scale.
- The selected outcome keeps the same series color from card to detail, reducing relearning and making the relationship explicit.
- The larger endpoint percentage preserves present-state legibility from across the room.
- The fixed Game timeline connects probability movement directly to the broadcast without adding another focus stop.
- Team identity appears only for an explicit head-to-head matchup. Props such as overtime, margin and player performance do not infer participants from category metadata.

## Interaction

- Arrow keys move focus through the existing header, outcomes, amount and CTA.
- Up from the first trading control returns directly to contextual navigation; the removed chart controls no longer create hidden focus stops.
- Back preserves the established contextual behavior.
- After five seconds without interaction, the expanded entry prompt animates back to its persistent compact state.
- All displayed market activity remains explicitly simulated.
