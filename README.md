# Corridor 3: Night Shift

A small game about shifts — the ones you work, and the ones you choose.

Built during November 2026 for [Game Off 2026](https://itch.io/jam/game-off-2026), theme: **SHIFT**.

You are the newest hire in an office building. The work happens on its own; the only real decision
is *which shift you are on*, and that changes everything: the day pays well and wears you down, the
night pays little and gives you back.

## Play

Open `index.html` in any browser. No install, no build step, no network.

- **Swap shift** with the button, or by pressing the **Shift** key. That is the whole control.
- Everything else happens by itself. You intervene at the end of the day, at the vending machine.
- A run is 30 in-game days, about ten minutes.

## The idea

The theme is read twice, on purpose. A *shift* is a period of work and it is also a change of
direction; the game is about both, and the two are the same button.

- The **day shift** pays roughly double and puts the Consultant — a rival who takes credit — in the
  building with you.
- The **night shift** pays little, teaches fast, and is quieter. The auditor walks the corridors at
  02:40, and loose change turns up behind the vending machine.
- Swapping mid-day **costs half of what is left of the day**: you cannot change direction for free.

Five hearts. A mishap, or an argument you lose, costs one; a day that ends without damage gives one
back. Thirty days, then the month closes on your rank and your tokens.

## Files

| file | what it is |
|---|---|
| `index.html` | the whole game: markup, styles, rules and the pixel art live here together |
| `docs/design.md` | the design, the tuning numbers, and the measured balance |

There is nothing else to build. The room is *drawn*, not pasted: it is a map of 30 cells by 8, each
character a sprite of 8x8 pixels, and the same sprites the game uses on the e-ink screen. No images,
no fonts, no network - the file works offline and from a local file path.

## AI disclosure

The jam asks participants to declare AI use, and this comes from a build where the AI share is
large, so it is worth stating plainly: the engine, the event text, the balance pass and the
English were written with an AI coding agent (Hermes), working from the author's decisions, layout
and pixel art. The balance was *measured* rather than guessed: a simulation harness inside
`index.html` runs whole 30-day games headlessly, under several play styles, and the numbers in
`docs/design.md` come from it.

## Origin

The setting and a first, much smaller engine existed for a few days before the jam opened, built to
put something on an old e-ink reader at home. Everything you can play here — the shift mechanic,
the day/night economy, the balance, the English text — was built during the jam.

## Licence

MIT, code and artwork together. See `LICENSE`.
