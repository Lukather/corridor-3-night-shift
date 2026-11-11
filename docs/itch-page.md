# itch.io page copy

The text as it stands on the page, in your words. Three factual corrections are applied here, and one
paragraph is added: the cards. Everything else is left alone.

- **the survival numbers** were the ones measured while the duel was still a die; the cards changed
  them, and changed them differently depending on how the player uses them
- **the run length** is twelve minutes of ticking now, not ten
- **"nothing to download"** contradicted the project being a Downloadable
- **the cards** are the game's central decision and the page did not mention them at all

## Title

Corridor 3: Night Shift

## Short description (the one-liner itch shows under the title)

A small game about shifts: the ones you work, and the ones you choose.

## Description

You are the newest hire in an office building. You do not steer the work but it happens on its own,
every second, whether you watch or not. The only real decision is **which shift you are on**, and it
changes everything!

- the **day shift** pays about twice as much, and puts the Consultant in the building with you, a
  rival who takes credit for what you did
- the **night shift** pays little and teaches fast. The auditor walks the corridors at 02:40, and
  loose change turns up behind the vending machine

When it matters the clock stops and the game asks. The Consultant wants your credit: **confront him**
and you keep it, and lose a heart, or **cut a deal** and you keep your health and pay him off. The
auditor wants your tokens: **sit through it** and learn something, or **buy the clerk a coffee** for
about half the price. Something breaks with your name on the ticket: **own it** and lose a heart, or
**cover it up** quietly.

Swapping mid-day costs half of what is left of the day, and the shift you work tomorrow is a free
choice made the night before. Measured over forty runs each: a player who refuses to pay with tokens
does not finish the month on the day shift at all, and a player who pays when a heart is nearly gone
finishes thirty-one of those forty on days, and thirty-nine of them at night.

**One button.** Press Shift, or click the button. That is the whole game.

A run is about twelve minutes of ticking, longer once the cards stop the clock. The whole game is
**one HTML file**: download the zip, unzip it, open `index.html` in any browser. No install, no
account, no network.

## Controls

- **Shift key**, or the on-screen Swap button: change shift. Mid-day this costs half of the hours that
  are left.
- **Space**, or the Pause button: stop the clock. While paused you can still swap shift and shop.
- **End of day**: the game stops by itself. Read the recap, pick tomorrow's shift (free), spend your
  tokens at the vending machine, then press Go home.
- Mouse or finger for everything else. On a phone there is no Shift or Space key, so use the buttons.

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

What you are playing here is deliberately reduced to **one mechanic and a twelve-minute run** - which
is the jam's own advice - and brought to the browser so that anyone can play it. The version at home
has what this one leaves out: contracts, weekly perks, an inventory, and a basement you can only open
with a key that costs more than a month of work.

## Credits

- design, pixel rooms and the game itself: me
- code written with Hermes (AI)

## Compatibility

Any browser, desktop or mobile, from 2022 onwards, with nothing to install. On a phone you play with
the button, since there is no Shift key to press.

## Not on the page, kept here

The submission form declares the AI use as **AI Assisted / Code / Text**. This is the longer version,
if it is ever wanted on the page:

> The jam asks participants to declare their use of AI, so, plainly: the engine, the event text, the
> balance pass and the English were written with an **AI coding agent (Hermes)**, working from my
> decisions, my layouts and the rooms I designed. The balance was measured rather than guessed - the
> game ships with a harness that plays whole 30-day runs headlessly, and the numbers in
> `docs/design.md` come out of it.

For the curious, and for the submission form:

- one HTML file, no dependencies, no build step, no network. The rooms are drawn from maps of 30 cells
  by 8, each character a sprite of 8x8 pixels in four tones, with an 18-cell window that follows the
  hero. The same drawing runs on an e-ink reader at home.
- source: https://github.com/Lukather/corridor-3-night-shift
