# ⚡ CAPACITY CRUNCHING

> **Stack. Optimize. Deploy. Scale.**

An arcade bin-packing retro puzzle game built with HTML5 Canvas and retro web fonts. Pack cloud compute workloads—VMs, GPUs, TPUs, GKE Nodes, and Kubernetes Pods—into datacenter racks while managing power limits, thermal throttling, and control plane overhead!

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

---

### 🏆 Global & Local Leaderboard
* **Arcade Name Entry**: Enter your 3-character initials using retro arcade arrow controls upon achieving a high score.
* **Top 10 Rankings**: Live rank board displaying Gold/Silver/Bronze badges, scores, and highest regions reached.
* **Dreamlo Cloud Sync**: Real-time cloud scores with seamless `localStorage` fallback.

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
| `Enter` | Start Game / Confirm Score |

---

## ⚙️ Configuration (Dreamlo Leaderboard)

The game includes built-in offline `localStorage` leaderboard support. To connect your own live multi-player cloud leaderboard:

1. Visit [Dreamlo](https://www.dreamlo.com/) and click **Get Codes**.
2. Open `index.html` and update the configuration object at the top:
   ```javascript
   const LEADERBOARD_CONFIG = {
     enabled: true,
     dreamloPublicCode: 'YOUR_PUBLIC_CODE',
     dreamloPrivateCode: 'YOUR_PRIVATE_CODE',
   };
   ```
3. Commit and push to deploy!

---

## 🚀 Local Development

Simply serve the directory with any static HTTP server:

```bash
# Using Python 3
python3 -m http.server 8080

# Using Node.js
npx serve .
```

Open `http://localhost:8080` in your web browser.
