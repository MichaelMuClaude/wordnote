# wordnote

A small desktop sticky note for learning words. It shows picture cards (a picture of a thing with its
word, phonetics and meaning) one after another, so you can learn English passively while you work. When
you already know a word, click **Got it** and the card moves to a `known` folder and stops coming back.

![wordnote showing a card](docs/screenshot.png)

The cards are the 1271 everyday-word cards from
[wordcards](https://github.com/MichaelMuClaude/wordcards): download `wordcards-v1-cards.zip` (771 nouns)
and `wordcards-v1.1-set2-cards.zip` (500 more: people, actions, adjectives ...) from its Releases page,
unzip the pictures into `~/word-images/learning`, and start wordnote. Any folder of pictures works,
though; the app does not care what is on them.

It started as a copy of [frame](https://github.com/MichaelMuClaude/frame), the desktop photo frame, and
shares its code: [egui](https://github.com/emilk/egui), a resizable borderless window, controls that
only appear while the pointer is over the card, Move and Undo.

## Using it

```
wordnote [--interval SECONDS] [--normal] [FOLDER...]
```

- Default card folder: `~/word-images/learning`; the slideshow changes every 10 seconds.
- **Got it** (top right, or the Delete key) moves the card to the `known` folder next to the card folder
  (`~/word-images/known`). An **Undo** button stays for 8 seconds. To use another folder, add
  `known=/some/folder` to `~/.config/wordnote/settings.txt`.
- **Move** (top left) moves a card to any other folder, for example one for pictures that came out wrong.
- **Previous** (left edge) goes back one card. The slideshow waits while the pointer is over the card.
- Drag the card to move the window, drag the paper edges to resize it. Right-click for the menu and
  Settings.
- On X11 the window sits below all other windows, like a desktop widget. `--normal` makes it an ordinary
  window; on Wayland it is always an ordinary window.

Got it moves your real files. It is a move, not a delete, and Undo works, but try it on a copy first.

## Building

You need a recent Rust toolchain and the libheif development files (1.17 or newer).

```
# Debian / Ubuntu
sudo apt install libheif-dev
cargo build --release
```

The binary is `target/release/wordnote`.

## Status

Tried only on Linux with an X11 session. The Windows build and Wayland behaviour have not been tested.

## License

MIT, see [LICENSE](LICENSE).
