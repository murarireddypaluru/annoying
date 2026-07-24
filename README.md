# annoying — 2-Player "Catch the Fruit"

A two-player browser game built with **p5.js** / **p5.play**. Players each control a
basket and try to catch fruit falling through a jungle background. Both clients stay in
sync through a shared **Firebase Realtime Database** (player list, player count, and the
shared `gameState`).

Five fruit types fall from the top: apple, banana, melon, orange, and pineapple.

## Game flow (gameState)

The game moves through a simple **lobby → play → end** machine driven by the shared
`gameState` / `playerCount` values in Firebase:

- **Lobby** (`gameState 0`) — players join via the name form; the game waits until
  `playerCount === 2`.
- **Play** (`gameState 1`) — fruit falls, baskets move, catches are detected.
- **End** (`gameState 2`) — the round is over.

## Libraries

- [p5.js](https://p5js.org/) + p5.dom — canvas, DOM form, input
- [p5.play](https://molleindustria.github.io/p5.play/) — sprites and groups
- p5.sound, matter.js (bundled in `libraries/`)
- [Firebase](https://firebase.google.com/) 8.3.0 (App + Realtime Database) — multiplayer sync

## Controls

- **Left Arrow / Right Arrow** — move your basket horizontally

## How to run

This game needs a **Firebase Realtime Database of your own** — the committed config only
contains placeholders.

1. Create a project at <https://console.firebase.google.com> and enable **Realtime Database**.
2. Open `index.html` and replace the placeholders in `firebaseConfig`
   (`YOUR_FIREBASE_API_KEY`, `https://YOUR_PROJECT.firebaseio.com`, etc.) with your own
   project's values.
3. Serve the folder over a local web server (e.g. `python3 -m http.server`) and open it in
   two browser tabs/devices to play. Opening `index.html` directly from the filesystem may
   break Firebase and asset loading.

## Security

The original Firebase credentials were removed and replaced with placeholders. Please read
[SECURITY-NOTE.md](SECURITY-NOTE.md) before running — and remember to lock down your
Realtime Database security rules.
