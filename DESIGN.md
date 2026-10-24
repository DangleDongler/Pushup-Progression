# Design

## Philosophy: Ninety Degrees

Effort is invisible until something measures it. This visual language borrows from the instruments people trust to tell the truth about a body in motion: the protractor, the goniometer, the chalk line on a gym floor. Every mark exists because it records something. An arc is an angle, a tick is an increment, a bar is a quantity. Decoration that measures nothing is removed. What remains should feel meticulously crafted, the product of painstaking calibration rather than ornament.

Space is quiet and cool, like chalk dust on a clean floor. Large areas of near-white and deep ink hold still so that a single instrument can speak. Composition centres on one gauge at a time, never several competing for attention. Margins are generous and exact, and alignment is treated as a measurement in its own right: an edge that is a few pixels off reads as an instrument out of true.

Colour is a signal, never a mood. One saturated cobalt is reserved for the moment something is achieved: a threshold crossed, a rep counted, a level unlocked. Red appears only when a measurement fails. Amber appears only when the instrument itself needs adjusting. Everything else is ink, chalk and graphite, so that the rare colour carries its full weight. The palette should look like the result of deliberate, master-level restraint.

Scale creates hierarchy. A single numeral can be enormous, tall and condensed like a scoreboard figure, while everything around it whispers in small, even text. Thin graduated ticks sit beside heavy forms, and the contrast between hairline and mass is where the energy lives. Type is set as precisely as the ticks themselves, with tabular figures so numbers never shift as they change.

Motion answers effort. Nothing moves on its own except the gauge, which follows the body, and the brief pulse when a measurement is confirmed. Each transition should feel inevitable and expertly timed, the kind of detail that looks effortless only because someone laboured over it.

## Design system for the app

### Colour

| Name | Hex | Use |
|---|---|---|
| Ink | `#12162A` | Text on chalk, dark glass over the camera |
| Chalk | `#ECEEE8` | Start screen, ladder, history and settings backgrounds |
| Paper | `#F7F8F4` | Grouped lists on chalk |
| Cobalt | `#2B45FF` | Counted, progress, primary buttons (lighter `#8C9BFF` on dark) |
| Graphite | `#5D6375` | Secondary text on chalk (`#B3B8C7` on dark) |
| Signal | `#E5383B` | Not counted |
| Amber | `#F5B83D` | Camera advice |

### Type

Archivo (variable width and weight), one family throughout.
- Rep numbers: weight 800, width 62% (tall and condensed), tabular figures.
- Screen titles: weight 750, width 75%.
- Body: weight 420, width 100%, 16px, line height 1.45.
- Sentence case everywhere. No all-caps labels.

### Layout

- **Workout:** the camera fills the screen. A slim bar at the top, the depth gauge and rep count centred near the bottom, and a dock with the exercise picker, knuckles toggle and Finish set.
- **Planning screens** (start, ladder, history, settings): chalk sheets, left-aligned text, grouped lists.
- **Ladder:** a vertical rail of rungs, because the levels are a real sequence.

### Principles

1. Every mark measures something real.
2. One loud element per screen; everything else stays quiet.
3. Chalk to plan, glass to train.
4. Cobalt means counted or progress, red means not counted, amber means fix the camera.
5. Readable at arm's length from the floor.
