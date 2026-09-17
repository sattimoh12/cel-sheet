# Cel Sheet

A two-phone board for collaborating on an anime feature. One page, no accounts, no server.

**Live:** https://sattimoh12.github.io/cel-sheet/

## The three phases

1. **Dump** — the reel is a list of **scenes**. Name a scene, then drop lines, locations, looks,
   beats and photos straight into it ("Write into this scene" / "Photo here"), or pick the target
   scene from the rail above the composer. Anything dropped with no scene selected lands in
   **Unfiled**; each card has a dropdown to move it later, and scenes reorder with ↑ ↓.
   Each drop is also sorted on arrival into Dialogue / Character / Setting / Visual / Sound /
   Beat / Reference, or No category. The guess is marked as a guess; every card carries all eight
   chips, so correcting it is one tap.
2. **Sealed pass** — each person goes through the reel alone, scene by scene, and marks
   In / Maybe / Out. Marks live only on that phone until you seal them, so neither person
   anchors the other.
3. **Lock** — both sealed passes side by side, each card tagged with its scene. Splits first,
   then Canon and Cut. The canon renders as plain text, scene by scene with categories inside —
   close to a treatment you can paste somewhere else.

## Sync

There is no backend. **Share** hands the other phone your whole board — a link (straight into
WhatsApp or iMessage; photos don't fit in a link) or a file (carries everything). **Merge** folds
theirs into yours: union by scene and by card, whichever version was edited last wins, deletes are
tombstoned so they don't come back, and your own sealed pass is never overwritten. Merging both
directions converges.

Everything is kept in `localStorage` on each phone. Add to your home screen for an app-like window.
