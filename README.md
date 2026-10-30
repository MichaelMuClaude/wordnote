# GlanceCards（词卡）

A small desktop card window for learning words. It shows picture cards (a picture of a thing with its
word, phonetics and meaning) one after another, so you can learn English passively while you work. When
you already know a word, click **Got it** and the card moves to a `known` folder and stops coming back.

**中文说明**：词卡（GlanceCards）是一个桌面小窗口，轮流显示英语单词图片卡片（图 + 单词 + 音标 + 中文），
干活时随手瞄几眼就能记单词。认识的点右上角的"认识了"，这张卡就移到 `known` 文件夹，不再出现。界面是中文的
（需要系统里有中文字体，没有的话自动用英文）。右键 → "设置…" 里可以选窗口是悬浮在其他窗口之上、普通窗口，
还是沉在其他窗口之下（像桌面小部件）。卡片见 [wordcards](https://github.com/MichaelMuClaude/wordcards)。

![GlanceCards showing a card](docs/screenshot.png)

The cards are the 2271 everyday-word cards from
[wordcards](https://github.com/MichaelMuClaude/wordcards): download `wordcards-v1-cards.zip` (771 nouns),
`wordcards-v1.1-set2-cards.zip` (500 more: people, actions, adjectives ...),
`wordcards-v1.2-set3-cards.zip` (500 more: animals, nature, food, tools, feelings ...) and
`wordcards-v1.3-set4-cards.zip` (500 more: world foods, tech, vehicles, characters ...) from its Releases page,
unzip the pictures into `~/word-images/learning`, and start GlanceCards. Any folder of pictures works,
though; the app does not care what is on them.

It started as a copy of [frame](https://github.com/MichaelMuClaude/frame), the desktop photo frame, and
shares its code: [egui](https://github.com/emilk/egui), a resizable borderless window, controls that
only appear while the pointer is over the card, and Undo.

## Using it

```
glancecards [--interval SECONDS] [--top | --normal | --bottom] [FOLDER...]
```

- Default card folder: `~/word-images/learning`; the slideshow changes every 10 seconds.
- **Got it** (认识了, top right, or the Delete key) moves the card to the `known` folder next to the card folder
  (`~/word-images/known`). An **Undo** button stays for 8 seconds. To use another folder, add
  `known=/some/folder` to `~/.config/glancecards/settings.txt`.
- **Previous** (left edge) goes back one card. The slideshow waits while the pointer is over the card.
- Drag the card to move the window, drag the edges to resize it. Right-click for the menu and
  Settings (设置).
- **Window position**, in Settings: float above other windows, an ordinary window, or below all other
  windows like a desktop widget (X11 only; this is the default there, and on Wayland the window is an
  ordinary window). The choice is saved. `--top`, `--normal` and `--bottom` on the command line override it
  for that run.
- **Language**: the interface is in Chinese when a font with Chinese characters is found (Noto Sans CJK,
  WenQuanYi, Microsoft YaHei, PingFang ...), otherwise in English.

Got it moves your real files. It is a move, not a delete, and Undo works, but try it on a copy first.

## Building

You need a recent Rust toolchain and the libheif development files (1.17 or newer).

```
# Debian / Ubuntu
sudo apt install libheif-dev
cargo build --release
```

The binary is `target/release/glancecards`.

## Status

Tried only on Linux with an X11 session. The Windows build and Wayland behaviour have not been tested.

## License

MIT, see [LICENSE](LICENSE).
