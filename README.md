# Sort Express — Playable Ad Prototype

A working playable ad concept built for the Circle Games Product Intern
(Task 1.3). Rather than submitting a static wireframe, the flow is implemented as a real,
playable ad.

**Live demo:* https://zeydusht.github.io/sort_express_playable/

## The mechanic

It reproduces the core loop of Circle Games' *Sort Express*: drag an item out of one cubby
and drop it into a cubby that already holds two of the same kind. The three collect, and
that cubby refills with new items from the back.

## Three rules enforced in code

The ad is authored, not random. Everything below is deliberate:

1. **The player cannot lose.** The timer freezes at four seconds and never reaches zero.
2. **The player cannot be punished.** A wrong drop does nothing at all — no time lost.
3. **The board cannot dead-end.** Refills always bring a pair whose third copy is already
   somewhere on the board, so a one-move solution always exists. Verified across 3,000
   simulated runs.

A hint hand appears after 1.6 seconds of inactivity and animates from the source item to
the slot that solves the board.

## Two variants

A toggle at the top switches between:

- **A — timer visible.** Frames the game as skill under pressure.
- **B — no timer.** Pressure comes only from the board filling up.

Both are built from the same template, which is what makes running the test cheap. The
end card reports the signals captured during play: time to first drag, playtime, number of
drags, shelves cleared, hint count.

## Technical notes

- Single HTML file, ~35 KB, no external assets or dependencies.
- Item art embedded as base64 WebP.
- Pointer events for drag, so it works on touch and mouse.
- MRAID store call included, with a plain fallback for desktop preview.
- Respects `prefers-reduced-motion`.

## Assets

Item art is taken from the live *Sort Express* build for the purposes of this case study.
In real production these would come from the client. Not intended for distribution.
