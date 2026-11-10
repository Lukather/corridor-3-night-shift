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
pockets, and returns the results of every run. Three play styles, sixteen runs each:

| play style | reaches day 30 | rank at the end | tokens | score |
|---|---|---|---|---|
| day shifts only | 5 of 16 | Manager (median) | 823 | 1954 |
| night shifts only | 9 of 16 | Junior Clerk (median) | 599 | 2214 |
| mixed, swapping at midday | 11 of 16 | Head of Department (median) | 570 | 2331 |

Reading: a player who never touches the mechanic earns the most money per day and gets fired most
often. The night shift is the safe, slow path to rank. Mixing - take the day when you need money,
recover at night - survives most runs and scores highest. That is the shape the design wants, and
it is why the score counts rank, not just tokens.

Two bugs worth remembering, both found by measuring rather than by reading the code: an early
version gave a 17% mishap rate on the day shift instead of 3.5%, because the threshold bands of
the different events were being added together across shifts; and a *missing* day-closing routine
in the harness made the simulated game harder than the real one, so the measurements were of a
game nobody would play.

## Out of scope, on purpose

No sound design beyond two synthesised tones, no save between sessions, no second mechanic. The jam
advice is to build one mechanic and one playable level before anything else, and that is what this
is.
