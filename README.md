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

**＋ Tab** at the end of the rail adds your own category — Music, Editing, whatever the film needs.
Custom tabs get their own colour, sit before No category, and travel with the board like scenes do.
The × beside one deletes it (twice, to confirm) and its cards fall back to unsorted. The on-device
classifier only knows the seven built-ins, so cards land in your own tabs by tapping.

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

Turn it on from the project sheet and both phones keep that project in step on their own — no
tapping Merge. It runs on the `cel-sheet` Firebase project (Spark / no-cost, Firestore in the
`eur3` European multi-region). The header shows `● live`, `… syncing` or `! sync failed`.

**Each project is paired on its own.** A project reads *this phone only* in the project list until
somebody Shares it once; that first link is what pairs it. A new project never appears on the other
phone by itself.

**The database only ever holds ciphertext.** The board is gzipped and then encrypted with AES-GCM
on the phone before it is pushed. The key is a 32-character secret that lives in the **fragment**
of the share link (`#m=…`) and in localStorage — a URL fragment is never sent to a server, so the
key reaches the other phone without passing through Google, GitHub, or whatever app carried the
message. A stored board document is exactly `{v, iv, e, at}`: no titles, no dialogue, no names.
Photos are encrypted the same way in a `photos` subcollection, because a Firestore document caps
at 1 MiB.

The room id (20 characters, the document address) and the key travel together in that one link, so
**treat a share link as the whole board** — anyone who gets it can read and write that project.
Losing the key only loses the cloud copy; both phones still hold the board. With sync off, nothing
leaves the phone.

If a project reads **re-pair** instead of *synced*, it was paired before encryption existed: it has a
room but no key, so it cannot sync. Tap **Re-pair** in the project sheet — it mints a fresh room and
key, keeps the board, and abandons the old room. Then send one new Share link; the old link is dead.

The project sheet also shows the **build stamp** and a **Reload page** button, because a page added
to the iOS home screen holds on to old HTML; the button reloads with a fresh query string to break
that cache. If two phones disagree, check the build stamp on both first.

The security rules allow reads and writes on `boards/{room}` only when the room id is exactly 20
characters and the document is the encrypted shape, under 900 KB. Plaintext writes, extra fields,
short ids and oversized blobs are all refused.

### About the Firebase API key in this file

The `FB` config near the top of `index.html` is public by design — a Firebase web config is a
project identifier, not a credential, and it has to reach the browser to work. GitHub's secret
scanner flags the format because Google uses the same shape for Maps and Cloud keys that *are*
sensitive. There is nothing to rotate. What actually protects a board is the room key, which is
never in this repo.

## Share and Merge

With or without live sync, boards also move by hand. **Share** hands the other phone your whole board — a link (straight into
WhatsApp or iMessage; photos don't fit in a link) or a file (carries everything). **Merge** folds
theirs into yours: union by scene and by card, whichever version was edited last wins, deletes are
tombstoned so they don't come back, and your own sealed pass is never overwritten. Merging both
directions converges.

Everything is kept in `localStorage` on each phone. Add to your home screen for an app-like window.
