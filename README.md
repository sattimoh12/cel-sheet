# Cel Sheet

A two-phone board for collaborating on an anime feature. One page, no accounts, no server.

**Live:** https://sattimoh12.github.io/cel-sheet/

## Projects

The name at the top is the project. Tap it to rename it, switch between films, or start a new one.
Each project keeps its own scenes, cards, passes and decisions, and Share/Merge only ever move the
project you have open — a board someone sends you that this phone has never seen arrives as its
own project rather than mixing into the one you're looking at.

## Filtering

A rail under the phase tabs filters by category, with a live count on each chip. Tap **Character**
to see only character cards, tap **Visual** as well to see both, tap **All** to come back. The
filter follows you into the sealed pass and the Lock, and each phone remembers its own.

## The three phases

1. **Dump** — the reel is a list of **scenes**. Name a scene, then drop lines, locations, looks,
   beats and photos straight into it ("Write into this scene" / "Photo here"), or pick the target
   scene from the rail above the composer. Anything dropped with no scene selected lands in
   **Unfiled**; each card has a dropdown to move it later, and scenes reorder with ↑ ↓.
   Each drop is also sorted on arrival into Dialogue / Character / Setting / Visual / Sound /
   Beat / Reference, or No category. The guess is marked as a guess; every card carries all eight
   chips, so correcting it is one tap. A pasted URL becomes a live link on the card (and usually files itself under Reference).
2. **Sealed pass** — each person goes through the reel alone, scene by scene, and marks
   In / Maybe / Out. Marks live only on that phone until you seal them, so neither person
   anchors the other.
3. **Lock** — both sealed passes side by side, each card tagged with its scene. Splits first,
   then Canon and Cut. The canon renders as plain text, scene by scene with categories inside —
   close to a treatment you can paste somewhere else.

## Live sync

Turn it on from the project sheet and both phones keep this project in step on their own — no
tapping Merge. It runs on Firebase (free tier); paste a web config into the `FB` constant at the
top of `index.html` to switch it on. The room id is a 20-character random string stored with the
board, so sending one Share link is what joins the other phone; after that it is automatic.
Anyone who knows a room id can read and write that board, so treat the id as the secret.
Photos sync in their own subcollection because a Firestore document caps at 1 MiB.

## Share and Merge

With or without live sync, boards also move by hand. **Share** hands the other phone your whole board — a link (straight into
WhatsApp or iMessage; photos don't fit in a link) or a file (carries everything). **Merge** folds
theirs into yours: union by scene and by card, whichever version was edited last wins, deletes are
tombstoned so they don't come back, and your own sealed pass is never overwritten. Merging both
directions converges.

Everything is kept in `localStorage` on each phone. Add to your home screen for an app-like window.
