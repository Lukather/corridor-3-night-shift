# itch.io page copy

Paste-ready text for the submission. Rewrite it in your own voice where you want to.

## Title

Corridor 3: Night Shift

## Short description (the one-liner itch shows under the title)

A small game about shifts: the ones you work, and the ones you choose.

## Description

You are the newest hire in an office building. You do not steer the work - it happens on its own,
every second, whether you watch or not. The only real decision is **which shift you are on**, and it
changes everything.

A day is twelve bells long. What a bell pays you, and what it costs you, is the whole game:

- **day shift**: 8 to 16 tokens a bell, and 3 experience. The money is here. So is the Consultant, a
  rival who takes credit for what you did: he turns up about one bell in 22, and you win that
  argument about half the time at the bottom of the ladder, 85% of the time at the top.
- **night shift**: half the pay, 4 to 8 tokens a bell, but twice the learning, 6 experience. It is
  quieter, and it taxes what you hoard: the auditor walks the corridors at 02:40, about one bell in
  17, and takes 15% of whatever you are holding over 300 tokens. Loose change turns up behind the
  vending machine about one bell in 13.

So the day is where the money is, and the night is where you learn and where you survive longer.
Swapping mid-day costs half of what is left of the day, so changing direction is never free - and it
matters: a player who stays on day shifts is fired about four times in five, while nights alone last
the whole month about half the time.

Five hearts: a mishap, or an argument you lose, costs one; a day that ends without damage gives one
back. Thirty days, then the month closes on your rank and your score.

I measured all of this rather than guessed it; the numbers come out of a harness that plays whole
30-day runs headlessly, and they are in the repository.

**One button.** Press Shift, or click the button - that is the whole game.

A run is about ten minutes. The whole game is **one HTML file**: download the zip, unzip it, open
`index.html` in any browser. No install, no account, no network.

## Controls

- **Shift key**, or the on-screen button: change shift
- mouse or finger for everything else

## Made for Game Off 2026

The theme is **SHIFT**, and it is read twice on purpose. A shift is a period of work; a shift is
also a change of direction. In this game the two are the same button, and the whole economy hangs
off the choice between them.

## Where it comes from

This is the browser release of a game whose real home is not a browser.

The original runs on a small server at home and lives on an e-ink reader: the screen *is* the game -
a room, a character moving through it, the log of the day - and because e-ink cannot be tapped
usefully, the decisions happen on a phone. One button, glanceable, always on, part of a wall: that is
the shape the whole thing was built around.

What you are playing here is deliberately reduced to **one mechanic and a ten-minute run** - which is
the jam's own advice - and brought to the browser so that anyone can play it. The version at home has
what this one leaves out: contracts, weekly perks, an inventory, and a basement you can only open
with a key that costs more than a month of work.

## AI disclosure

The jam asks participants to declare their use of AI, so, plainly: the engine, the event text, the
balance pass and the English were written with an **AI coding agent (Hermes)**, working from my
decisions, my layouts and the rooms I designed. The balance was measured rather than guessed - the
game ships with a harness that plays whole 30-day runs headlessly, and the numbers in
`docs/design.md` come out of it.

## Credits

- design, pixel rooms and the game itself: me
- code written with Hermes (AI)

## Compatibility

Any browser, desktop or mobile, from 2022 onwards, with nothing to install: it is one file, and it
works offline, straight from the unzipped folder. On a phone you play with the button, since there is
no Shift key to press.

## Technical note (for the curious)

One HTML file, no dependencies, no build step, no network. The rooms are drawn from maps of 30
cells by 8, each character a sprite of 8x8 pixels in four tones, with an 18-cell window that
follows the hero. The same drawing runs on an e-ink reader at home.

## Source

https://github.com/Lukather/corridor-3-night-shift
