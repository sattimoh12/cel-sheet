# Cel Sheet

A two-phone board for collaborating on an anime feature. One page, no accounts, no server.

**Live:** https://sattimoh12.github.io/cel-sheet/

## The three phases

1. **Dump** — throw in lines, locations, looks, beats, photos. Each drop is sorted on arrival
   into Dialogue / Character / Setting / Visual / Sound / Beat / Reference, or No category.
   The guess is marked as a guess; every card carries all eight chips, so correcting it is one tap.
2. **Sealed pass** — each person goes through the reel alone and marks In / Maybe / Out.
   Marks live only on that phone until you seal them, so neither person anchors the other.
3. **Lock** — both sealed passes side by side. Splits first, then Canon and Cut.
   The canon renders as plain text, grouped by category.

## Sync

There is no backend. **Share** hands the other phone your whole board — a link (straight into
WhatsApp or iMessage; photos don't fit in a link) or a file (carries everything). **Merge** folds
theirs into yours: union by card, whichever version was edited last wins, deletes are tombstoned
so they don't come back, and your own sealed pass is never overwritten. Merging both directions
converges.

Everything is kept in `localStorage` on each phone. Add to your home screen for an app-like window.
