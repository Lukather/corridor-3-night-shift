# Devlog 1 - the game lives on an e-reader, and that is where it comes from

Before this was a browser game, it was a screen on the wall.

At home I have an old e-ink reader that I had stopped using: six inches, sixteen shades of grey, no
backlight, and a battery that lasts weeks. It is a lovely object to look at and a terrible one to
touch, which makes it the exact opposite of what you want from a screen - unless what you want is a
window into something that keeps happening without you. So I wrote a small server that simulates an
office and renders one page of it, every five minutes, for that reader to pick up.

That is the original: **not a game you play, a game you check on.** It runs on a small server at
home, it keeps its own time - one turn every fifteen minutes, whether anyone is looking or not - and
the reader pulls a new page when it feels like it. A room, a character moving through it, and the log
of the day. The building has seven floors, and you get promoted into them.

The problem with a read-only screen is obvious: you cannot decide anything on it. So the decisions
happen somewhere else - a page on a phone, in the same paper-and-ink language - and that is where you
buy things, accept a job, or change your shift. The reader is the world; the phone is the hand.

## Everything is text pretending to be a picture

There is no game engine in the original. It is a Python script that writes HTML: the rooms are maps
of thirty cells by eight, each character is a sprite of eight by eight pixels in four tones, and the
whole thing is rendered as rectangles by whatever browser is looking at it - on the reader, on the
phone, anywhere.

That sounds like a limitation and it is actually the reason this jam entry exists. When a jam with
the theme **SHIFT** came along, porting it to a single HTML file took almost no new thinking: the
same maps, the same sprites, the same four tones. The engine changed language; the game did not
change shape.

## The shift is the whole game, on purpose

The original had four directives, weekly perks, contracts, a shop with geometric prices, an auditor
who taxes what you hoard, a rival who steals credit. The jam version keeps **one** mechanic, which is
what the jam itself advises - one mechanic and one playable level before anything else.

That mechanic is the shift. A day shift pays about twice as much and puts the rival in the building
with you; a night shift pays little and teaches fast, and the corridor at 02:40 is quiet enough to
hear the auditor coming. Changing mid-day costs you half of what is left of the day, so changing your
mind is never free.

I measured it rather than guessed it: the game ships with a harness that plays whole thirty-day runs
headlessly, and three play styles, forty runs each, say that someone who never touches the mechanic
gets fired about three times in five. The game teaches its own verb.

## How much of this was machine-made

A lot, and I would rather say it plainly. The code, the event text, the balance pass and the English
were written with an AI coding agent, working from my decisions, my layouts and the rooms I designed.
The balance numbers are not vibes: they come out of the harness, and the bugs it caught - a threshold
that was being counted twice, a simulation that was measuring a harder game than the real one - are
in the repository's design notes.

## What is not in this version

The browser release is deliberately small: no contracts, no weekly perks, no inventory, no basement
you can only open with a key that costs more than a month of work. Those live in the version at home,
which is still running, still on the wall, still counting turns while nobody watches.

That is the honest pitch: this is the same game, brought into a browser so you can actually play it,
with one mechanic kept and the rest left at home on purpose.

*Screenshots: the e-ink page and the phone page, side by side with the browser build.*
