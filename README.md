# Tower of Hanoi: The 20-Minute Challenge!

An interactive, educational web application that teaches **Stacks (LIFO)**, **Recursion**, and **Algorithmic Complexity** through the classic Tower of Hanoi puzzle — wrapped in a continuous 20-minute challenge with a countdown timer.

Built as a Data Structures & Algorithms coursework project. Zero dependencies, zero build step — just open `index.html`.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 🎮 Live Demo

Open [`index.html`](index.html) in any modern browser — no server, no install required.

Or run a local server:

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

---

## ✨ Features

### Core Game
- **Three pegs** — Peg A (Source), Peg B (Spare), Peg C (Target)
- **Color-coded disks** — Green (1), Purple (2), Red (3), Orange (4), Cyan (5)
- **Three difficulty levels** — 3 disks (7 moves), 4 disks (15 moves), 5 disks (31 moves)
- **Strict LIFO enforcement** — only top disk movable, larger disk can never sit on smaller
- **Robust error handling** — illegal moves blocked with clear explanations; move counter never incremented on invalid attempts

### 20-Minute Continuous Challenge
- Countdown starts at **20:00** on "Start Challenge"
- Timer **never pauses** — not for hints, undo, restart, difficulty changes, or Learning Mode
- **Warning alerts** at 05:00 (amber) and 01:00 (red)
- **Time's-up overlay** halts all gameplay and autoplay, showing a final summary modal
- Early finishers can advance to higher difficulties using remaining time

### Interactive Controls
- Click-to-select source peg → click target peg
- **Hint** — suggests the optimal next move
- **Undo** — reverts the last valid move
- **Restart Puzzle** — resets the board (timer keeps running)
- Live **move counter** and **minimum possible moves** (`2ⁿ − 1`)
- Sequential **move history log**

### Step-by-Step Learning Mode
- Playback controls: **Previous / Next / Autoplay / Pause**
- Full **optimal 7-step solution** for 3-disk mode
- Playback is isolated from the global timer
- Inline pedagogical annotations on `2ⁿ − 1`, stack push/pop mapping, and recursive decomposition

### Responsive UI
- Fluid layout from classroom projectors → desktops → mobile touchscreens

---

## 🧱 Data Structures & Algorithms

### Stack ADT
Each peg is modeled as a LIFO stack with explicit primitives — `push`, `pop`, `peek`, `isEmpty` — all **O(1)**.

```js
class Stack {
  constructor(name = '') { this.name = name; this.items = []; }
  push(item) { this.items.push(item); }              // O(1)
  pop()      { return this.items.pop(); }            // O(1)
  peek()     { return this.items.at(-1) ?? null; }   // O(1)
  isEmpty()  { return this.items.length === 0; }     // O(1)
  size()     { return this.items.length; }           // O(1)
}
```

### Recursive Solver
```js
function solve(n, from, to, via) {
  if (n === 1) {
    moves.push({ from, to });          // Base case
  } else {
    solve(n - 1, from, via, to);       // Move n-1 to spare
    moves.push({ from, to, disk: n }); // Move largest directly
    solve(n - 1, via, to, from);       // Move n-1 to target
  }
}
```

### Complexity
- **Recurrence:** `T(n) = 2·T(n−1) + 1`, with `T(1) = 1`
- **Minimum moves:** `Sₙ = 2ⁿ − 1` (proved by induction)
- **Time complexity:** `O(2ⁿ)` — exponential
- **Stack operations:** `O(1)` each

---

## 📁 Repository Structure

```
tower-of-hanoi/
├── index.html                              # The complete game (single file, zero deps)
├── docs/
│   ├── Demo_Script.html                    # Styled presentation script (open in browser)
│   ├── Demo_Script.docx                    # Presentation script (Word)
│   ├── Tower_of_Hanoi_Technical_Report.pdf # Technical report
│   └── Tower_of_Hanoi_Technical_Report.docx
└── README.md
```

---

## 🚀 Getting Started

1. Clone the repo:
   ```bash
   git clone https://github.com/<your-username>/tower-of-hanoi.git
   cd tower-of-hanoi
   ```
2. Open `index.html` in your browser. That's it.

---

## 📜 Course Deliverables

| Deliverable | Description | Weight |
|---|---|---|
| **1** | Source code & live web application | 50 |
| **2** | 10-minute video presentation & live demo | 25 |
| **3** | Technical report (`docs/`) | 25 |

---

## 📄 License

Released under the [MIT License](LICENSE).

---

<p align="center">Built for Data Structures & Algorithms coursework — Stacks · Recursion · Complexity</p>
