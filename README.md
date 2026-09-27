# ⚡ CAPACITY CRUNCHING

> **Stack. Optimize. Deploy. Scale.**

An arcade bin-packing retro puzzle game built with HTML5 Canvas and retro web fonts. Pack cloud compute workloads—VMs, GPUs, TPUs, GKE Nodes, and Kubernetes Pods—into datacenter racks while managing power limits, thermal throttling, and control plane overhead!

Plays on desktop with the keyboard and on phones and tablets with touch. Renders sharp at any window size and display density, with an in-game options screen for display size, text size, font style, sound, and touch buttons. Single `index.html`, no build step, no dependencies beyond three Google Fonts.

🎮 **Play Online:** [https://geoffsdesk.github.io/capacity-crunching/](https://geoffsdesk.github.io/capacity-crunching/)

---

## 🕹️ Gameplay & Features

### 🧩 Workload Pieces (Chips)
Each workload represents real-world cloud compute infrastructure with unique power draws and shapes:

| Piece | Shape / Type | Specs | Power Draw | Special Effect |
|---|---|---|---|---|
| **VM f1-micro** | 2×2 Block | 2 vCPU / 0.6 GB | **+3W** | Compact bin-packing block |
| **VM n2-std-8** | S-Piece | 8 vCPU / 32 GB | **+5W** | Standard compute shape |
| **VM m2-ultra** | Z-Piece | 416 vCPU / 12 TB | **+6W** | High-memory workload |
| **GPU A3 Mega** | T-Piece | 8× H100 / 80 GB | **+10W** | AI acceleration piece |
| **TPU v5p Pod** | 1×4 Line Piece | 8,960 Chips | **+14W** | Clears 4 lines (Tetris) |
| **GKE Node** | L-Piece | e2-standard-4 | **+7W** | **Forces a Control Plane piece next!** |
| **K8s Pod** | J-Piece | Container Wkld | **+5W** | Standard containerized unit |
| **Ctrl Plane** | 2×2 Corner | k8s Overhead | **+12W** | **Overhead! Clear row for bonus points** |

---

### ⚡ Power Rack & Thermal Systems
* **Power Draw**: Placing chips increases the datacenter's active wattage.
* **Cooling by Optimization**: Clearing lines eliminates heat and cools the system (1 line = -15W, 2 lines = -30W, 3 lines = -50W, 4 lines = -80W).
* **Thermal Throttling (100W)**: Exceeding power capacity overheats the rack, injecting grey garbage rows into the board!
* **Gigawatt Surge**: Clearing 3+ lines triggers a surge bonus, instantly zeroing out power and eliminating congested rows.

---

### 🌐 Datacenter Regions
Progressively deploy across global datacenters with escalating bin-packing challenges:
`us-central1` ➔ `us-east1` ➔ `europe-west1` ➔ `asia-east1` ➔ `us-west1` ➔ `europe-west4` ➔ `asia-northeast1` ➔ `us-east5` ➔ `australia-se1` ➔ **`GLOBAL DEPLOY`**

Every 10 lines cleared is a level-up, which migrates you to the next region. Each region has a rack condition (clean, legacy workloads, bad bin-packing, or disaster zone) that decides how much inherited junk lands on your racks when you arrive: up to a few light rows in a clean region, up to 3 dense rows in a disaster zone. Levels past 10 stay in GLOBAL. Drop speed rises 4 frames per level, from 48 frames per row at level 1 down to a floor of 3.

---

### 🧮 Scoring

| Event | Points |
|---|---|
| 1 / 2 / 3 / 4 lines | 100 / 300 / 500 / 800 × level |
| Row containing a Control Plane chip cleared | +200 × rows × level (shown as **OVERHEAD ELIMINATED**) |
| Gigawatt Surge bonus row | +200 × level |
| Soft drop | +1 per row |
| Hard drop | +2 per row |

---

### 🎮 Piece Handling

* **Lock delay**: a piece that lands waits 30 frames (half a second) before locking. Moving or rotating it restarts the wait, but only 15 times per landing; the budget refills when the piece falls to a new lowest row. This is the standard "move reset" rule and stops a piece being stalled on the stack forever.
* **Hold**: `C` swaps the active piece with the held one, once per piece.
* **Rotation**: pieces kick left, right, and up to find room when a plain rotation is blocked.
* **Game over**: Enter and Space are ignored for about three quarters of a second after the cluster overloads, and held keys are ignored, so the hard drop that ended the game cannot skip the game-over screen or submit a blank name.

---

### 🏆 Leaderboard & Personal Best
* **Your best**: the title screen and sidebar show your own best score, saved in the browser. Beating it earns **NEW HIGH SCORE RECORD** on the game-over screen.
* **Arcade name entry**: after any scoring game, enter 3-character initials with the arrow keys (or the touch bar) and submit with Enter.
* **Top 10 rankings**: 1st/2nd/3rd badges, scores, and the region reached. The list starts with ten demo entries so the board is never empty; they are not counted as your personal best.
* **Cloud sync (optional)**: with Dreamlo codes configured (see below) scores are uploaded and the board is fetched from the cloud. Submitting shows **UPLOADING SCORE...** and only fetches once the upload has finished, so the new entry is always on the board you see. Without codes, or if the cloud is unreachable, the board falls back to the browser's local copy and says so.

---

## ⌨️ Controls

| Key | Action |
|---|---|
| `←` / `→` | Move Left / Right |
| `↑` | Rotate Workload Piece |
| `↓` | Soft Drop |
| `Space` | Hard Drop |
| `C` | Hold Piece |
| `P` | Pause / Resume Game |
| `L` | View Top 10 Leaderboard |
| `O` | Open the Options screen (from the title, pause, or game-over screen) |
| `[` / `]` | Text size down / up (works on any screen) |
| `Enter` | Start Game / Confirm Score |

---

## 📱 Touch Controls

On phones and tablets an on-screen button bar appears under the game (◀ ▶ ROT ▼ DROP HOLD MENU; ◀ ▶ ▼ auto-repeat while held). The board itself also takes gestures:

| Gesture | Action |
|---|---|
| Tap | Rotate (in menus: confirm / start) |
| Drag left / right | Move one column per cell dragged |
| Drag down | Soft drop one row per cell dragged |
| Fast flick down | Hard drop |

On the Options screen, tap a row to select it and tap its left or right half to change it. On the name-entry screen, tap a slot to select it and tap its top or bottom half to change the letter. The bar can be forced on or off with the **Touch Buttons** option.

---

## 🔧 Options & Accessibility

Press `O` to open **SYSTEM OPTIONS**. Changes apply instantly and are saved in the browser.

| Option | Choices | Notes |
|---|---|---|
| **Display Size** | Fit Window / 1× / 1.5× / 2× | How large the whole game is drawn. Fixed sizes shrink to fit the window. |
| **Text Size** | Normal / Large / X-Large | Scales all text. The sidebar widens to make room; if a section no longer fits, the controls list moves under the board and the tips are hidden. |
| **Font Style** | Arcade / Readable | *Arcade* uses the pixel fonts. *Readable* swaps them for clearer ones (Silkscreen headings, a plain monospace for body text). |
| **Sound** | On / Off | Arcade sound effects. |
| **Touch Buttons** | Auto / On / Off | The on-screen button bar. *Auto* shows it on touch devices. |

The game always renders at your display's native resolution, so text stays sharp on HiDPI screens and under browser zoom (`Ctrl` `+` / `Ctrl` `-` also works as a size control).

---

## 🔬 Under the Hood

* **One file.** Everything (styles, game logic, rendering, input) lives in `index.html`. The other files in the repo are the favicon, the iOS touch icon, and the social preview image.
* **Logical canvas, native pixels.** All drawing uses a fixed logical space (580 × 720 at normal text size; the sidebar widens with larger text). Each frame the canvas is fitted to the window, or to the chosen fixed display size, and its backing store is sized by `devicePixelRatio`, so nothing is ever upscaled.
* **Fixed 60 Hz simulation.** Game logic runs on a fixed-timestep accumulator, so speed is identical on 60, 120, and 144 Hz displays. Catch-up after a stall (e.g. a hidden tab) is capped so the game does not fast-forward.
* **Flow layout.** Every screen is laid out as a vertical flow of lines, gaps, and boxes whose sizes come from the current fonts. If a screen does not fit, optional sections are dropped first (in the sidebar: the tips, then the controls list, which reappears under the board), then gaps are compressed.
* **One text path.** All text goes through a single helper that applies the text-size and font-style settings, shrinks a string (to 75%) and then condenses it to fit its allotted width, and can draw a pixel icon beside it. Icons (bolt, warning, helm, target, star) are 8 × 8 bitmaps, not emoji, so they look the same on every platform.
* **One input path.** Keyboard, touch bar, and canvas gestures all produce the same key presses, so screens, lockouts, and guards behave identically however you play.
* **Fonts.** Press Start 2P, Silkscreen, and VT323 load from Google Fonts. The game waits up to 2.5 s for them before drawing the first frame so nothing flashes in a fallback font; offline it starts anyway.

---

## ⚙️ Configuration (Dreamlo Leaderboard)

The game ships with a local-only leaderboard stored in the browser. To connect a shared cloud leaderboard:

1. Visit [Dreamlo](https://www.dreamlo.com/) and click **Get Codes**.
2. Open `index.html` and update the configuration object at the top:
   ```javascript
   const LEADERBOARD_CONFIG = {
     enabled: true,
     dreamloPublicCode: 'YOUR_PUBLIC_CODE',
     dreamloPrivateCode: 'YOUR_PRIVATE_CODE',
   };
   ```
3. Commit and push to deploy.

Two things to know before relying on it:

* **HTTPS.** The game is served over HTTPS on GitHub Pages and calls `https://www.dreamlo.com`. Dreamlo's free tier is HTTP-only, and browsers block HTTP requests from an HTTPS page, so a real cloud board needs Dreamlo's HTTPS tier or a different backend behind the same two calls (`loadLeaderboard` and `recordScore`).
* **The private code is public.** It has to ship in the page's JavaScript, so anyone can post any score. That is a limitation of Dreamlo's design, fine for a friendly board, not for anything competitive.

---

## 🖼️ Sharing

The page carries a description, theme colour, Open Graph, and Twitter card tags, so links pasted into chat apps and social sites show the title, a short description, and a 1200 × 630 preview image (`og-image.png`). The preview and the touch icon (`icon-180.png`) were rendered by the game itself so they use the real fonts and palette; `favicon.svg` is a hand-written SVG of the same four-chip motif.

---

## 🚀 Local Development

Serve the directory with any static HTTP server (opening the file directly works too, but a server matches how it is deployed):

```bash
# Using Python 3
python3 -m http.server 8080

# Using Node.js
npx serve .
```

Open `http://localhost:8080` in your web browser. The fonts load from Google Fonts, so the first load needs internet access.

There is no build step or test suite. When changing the game, the useful manual checks are: the title, play, pause, options, leaderboard, game-over, and name-entry screens at each **Text Size**, in both **Font Style**s, and at a phone-sized viewport with the touch bar showing. The repo's `.gitattributes` keeps line endings LF on every platform.
