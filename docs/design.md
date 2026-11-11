# Design notes

## The one mechanic

Shifting. It is a period of work *and* a change of direction, and in this game it is the same
button. Everything else is arithmetic around it.

The day shift pays about twice as much as the night shift and puts the Consultant - a rival who
takes credit - in the building with you. The night pays little, teaches fast, and is quieter: the
auditor walks the corridors at 02:40, and loose change turns up behind the vending machine.
Swapping mid-day costs half of what is left of the day, so a change of direction is never free - but
the shift you work tomorrow is a free choice made the night before.

Three things stop the clock and ask: the Consultant taking your credit, the audit at 02:40, and a
mishap with your name on the ticket. Each one offers two fixed ways out, one paid in hearts and one
paid in tokens, so a heart can be bought and tokens can be earned back. That is the arithmetic the
whole game hangs on, and it is why no single strategy wins: what a heart is worth depends on the
shift you are working and on how much of the month is left.

Five hearts, and a day that ends without damage gives one back. Thirty days, then the month closes
and you get a score.

## The building

Seven rooms, and you move through them as you are promoted: Reception, Open Space, Meeting Room,
Kitchen, Archive, Roof Terrace, Executive Floor. The room is where the game is looked at, so it
carries the progress: a promotion changes your surroundings before it changes anything else.

The rooms are drawn, not painted. Every room is a map of 30 cells by 8, each character a sprite of
8x8 pixels, four tones. The view is an 18-cell window that follows the hero, so the pixels stay
large enough to read. The hero walks with the clock, the Consultant appears in the room when he
turns up, and a find leaves a mark for one tick. The night shift does not filter the room: it maps
the four tones to their night values, which keeps the drawing crisp instead of washing it out.

## The numbers

| | day shift | night shift |
|---|---|---|
| tokens per event | x1.4 | x0.7 |
| experience per event | x0.75 | x1.6 |
| mishap per tick | 3.5% | 4% |
| the Consultant | 4.5% per tick | - |
| the auditor | - | 6% per tick |
| finds | - | 8% per tick, worth 45 x the night multiplier |

Twelve ticks to a day, two seconds each: a run is about twelve minutes of ticking, more once the
cards stop the clock. The audit bites above 150 tokens, taking 15% if you sit through it or about
7% if you buy the clerk a coffee.

Titles at 0, 75, 200, 400, 650, 950, 1350 and 1800 experience; the last one is Head of Department.
The vending machine sells a chair (+15% tokens, five times), night classes (+20% experience, three
times), an espresso machine (one extra shift change a day, twice), health cover (two hearts, once)
and a thermos (+30% night tokens, three times).

## How the balance was measured

`index.html` carries a small harness: `window.Corridor3.prova(policy, runs, seed, strategy)` plays
whole 30-day games headlessly, buying from the vending machine when it can afford to without emptying
its pockets, and returns the results of every run.

The cards - the Consultant, the audit, a mishap - are the decisions the game is made of, so the
harness has to model how they are answered. Four strategies. Each cell below is a count of **runs**,
never of days: forty games per cell, thirty days each, seed 2026. So "39 of 40" means thirty-nine
players out of forty reached the end of the month.

| strategy | what it does | day shifts only | nights only | mixed |
|---|---|---|---|---|
| `prima` | never pays: takes the heart | 0 of 40 runs | 21 of 40 runs | 21 of 40 runs |
| `avara` | pays only when the last heart is at stake | 20 of 40 runs | 37 of 40 runs | 34 of 40 runs |
| `oculata` | pays when hearts are low, or the price is small next to the purse | 31 of 40 runs | 39 of 40 runs | 35 of 40 runs |
| `paga` | always pays when it can | 30 of 40 runs | 38 of 40 runs | 35 of 40 runs |

Median score over the same runs, in the same order:

| strategy | day shifts only | nights only | mixed |
|---|---|---|---|
| `prima` | 1144 | 2696 | 2672 |
| `avara` | 1892 | 2780 | 2737 |
| `oculata` | 2001 | 2635 | 2613 |
| `paga` | 1875 | 2401 | 2311 |

Reading: no strategy wins on its own, which is the point of the cards - the best any of them manages
is thirty-nine runs out of forty. Refusing to pay dies on the day shift (not one run out of forty
finishes the month) and is merely poor at night. Paying every time survives best and finishes
poorest: at night it buys safety it did not need and closes on 367 tokens against the 680 of a
player who paid only to save the last heart. The two winning combinations are different ones,
`oculata` for the day and `avara` for the night, so the game is not asking which shift to work. It
is asking what a heart is worth today, and the answer changes with the shift.

## When the numbers lied

Worth writing down, because every one of them was found by measuring rather than by reading code.

1. An early version gave a 17% mishap rate on the day shift instead of 3.5%, because the threshold
   bands of the different events were added together across shifts. A band for one shift has to
   exclude the ranges of the events that cannot happen on it.
2. The harness did not apply the end-of-day routine, so the simulated game was harder than the real
   one: a missing call in the stub made every play style look unplayable.
3. It did not stub the renderer. Harmless while the room was three rectangles; after the room
   became a drawn map of two thousand, a 30-day simulation repainted the DOM four thousand times -
   930 ms per run instead of 15. A harness that measures the screen instead of the game is not a
   harness.
4. The Consultant was the day shift's danger, and in the original the argument is won by rolling a
   twenty-sided die and adding the rank against 21: never certain, and impossible to win at the
   bottom of a sixteen-rank ladder. Ported to the eight-rank ladder of this build it flattened into
   the same roll against the same 21, which is a certainty from rank 5 upward - so the day's danger
   became the day's best income. Measured over 20,000 bells: 873 wins to 2 losses, and a player who
   stayed on days died in his first week, before the ladder could pay the odds back. The fix keeps
   the shape and moves the threshold to 11 - 50% at Intern, 85% at Head of Department - and the
   day-only run returns to 8 runs of 40.
   The dice have since been taken out altogether: the Consultant, the audit and a mishap are now
   cards with fixed outcomes, and what a heart is worth is a decision rather than a probability. The
   entry stays because the lesson does - a ported probability is measured on the ladder it lands on,
   not on the one it came from.

## Out of scope, on purpose

No sound design beyond two synthesised tones, no save between sessions, no second mechanic. The jam
advice is to build one mechanic and one playable level before anything else, and that is what this
is.
