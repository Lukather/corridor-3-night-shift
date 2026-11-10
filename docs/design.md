# Design notes

## The one mechanic

Shifting. It is a period of work *and* a change of direction, and in this game it is the same
button. Everything else is arithmetic around it.

The day shift pays about twice as much as the night shift and puts the Consultant - a rival who
takes credit - in the building with you. The night pays little, teaches fast, and is quieter: the
auditor walks the corridors at 02:40, and loose change turns up behind the vending machine.
Swapping mid-day costs half of what is left of the day, so a change of direction is never free.

Five hearts. A mishap, or an argument you lose, costs one; a day that ends without damage gives one
back. Thirty days, then the month closes and you get a score.

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
| the auditor | - | 6% per tick, takes 15% of anything over 300 tokens |
| finds | - | 8% per tick |

Twelve ticks to a day, 900 ms each. A run is about ten minutes.

Titles at 0, 75, 200, 400, 650, 950, 1350 and 1800 experience; the last one is Head of Department.
The vending machine sells a chair (+15% tokens, five times), night classes (+20% experience, three
times), an espresso machine (one extra shift change a day, twice), health cover (two hearts, once)
and a thermos (+30% night tokens, three times).

## How the balance was measured

`index.html` carries a small harness: `window.Corridor3.prova(policy, runs, seed)` plays whole
30-day games headlessly, buying from the vending machine when it can afford to without emptying its
pockets, and returns the results of every run. Three play styles, forty runs each, seed 2026:

| play style | reaches day 30 | rank at the end | tokens | score |
|---|---|---|---|---|
| day shifts only | 8 of 40 | Team Lead (median) | 780 | 1563 |
| night shifts only | 21 of 40 | Head of Department (median) | 685 | 2674 |
| mixed, swapping at midday | 21 of 40 | Head of Department (median) | 589 | 2582 |

Reading: the day shift holds the most tokens and survives the least - it is the expensive shift, not
the safe one. A player who stays on it is fired in 32 runs out of 40, against 19 for the other two,
which are inside the noise of forty runs of each other. The night is the safe, slow path to rank;
mixing is where the money for the vending machine comes from, and the thermos then pays it back at
night. This is the honest statement: nights alone work, days alone are a bet, and the good run
changes shift.

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
   day-only run returns to 8 of 40.

## Out of scope, on purpose

No sound design beyond two synthesised tones, no save between sessions, no second mechanic. The jam
advice is to build one mechanic and one playable level before anything else, and that is what this
is.
