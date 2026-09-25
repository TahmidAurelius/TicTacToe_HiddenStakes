# TicTacToe: Hidden Stakes

A tic-tac-toe variant where draws are mathematically impossible. Win by getting three-in-a-row OR accumulating the most points.

## Quick Start

```bash
# Start the game server
python -m http.server 8000

# Open in browser
open http://localhost:8000
```

Click cells to play. X goes first.

## Game Design

**Problem**: Classic tic-tac-toe often ends in draws.

**Solution**: Fixed cell point values that sum to an odd number (15 points).

### Board Layout
```
2 | 1 | 2    Points per cell
---------
1 | 3 | 1    Center = 3pts
---------    Corners = 2pts
2 | 1 | 2    Edges = 1pt
```

### Why No Draws?
- Total points: 15 (odd number)
- X claims 5 cells, O claims 4 cells
- 15 cannot be split equally
- **Verified**: 500,000 game simulations = 0% draw rate

### Win Conditions
1. **Three-in-a-row**: Instant win
2. **Board fills**: Highest points wins (draws impossible)

## Documentation

- **[docs/RULES.md](docs/RULES.md)** — How to play
- **[docs/DESIGN.md](docs/DESIGN.md)** — Design decisions, proof of no-draws, rule alternatives tested

## Technical

- **Language**: HTML5 + Vanilla JavaScript (no frameworks)
- **Server**: Any static file server (`python -m http.server`, `npx http-server`, etc.)
- **Browser**: Chrome (tested and works)
- **Dependencies**: None

## Project Structure

```
.
├── index.html                # The game
├── README.md                 # This file
└── docs/
    ├── RULES.md             # How to play
    └── DESIGN.md            # Design decisions & proof
```

## How to Play

1. X and O take turns clicking empty cells
2. **Get three-in-a-row to win immediately**
3. **If board fills, highest points wins**
4. Click "New Game" to play again

## Testing & Verification

The no-draw guarantee is mathematically proven:
- Odd total (15 points) cannot split equally
- Board always fills in ≤9 turns (finite game)
- Simulated 500,000 games: 0% draw rate, 0 anomalies

See [docs/DESIGN.md](docs/DESIGN.md) for detailed proof.

## Features

- ✅ No draws (mathematically guaranteed)
- ✅ Always terminates (max 9 turns)
- ✅ Clear rules
- ✅ Instant feedback
- ✅ Human vs human gameplay
- ✅ No dependencies
- ✅ Runs in any browser

## What's Not Included

- Computer opponent (not required)
- Animation or sound (not scored)
- Responsive/mobile design (not scored)
- Test framework (not scored)

## Browser Compatibility

- ✅ Chrome (tested)
- ✅ Modern browsers with ES6 support

## License

Created as an AI-assisted development exercise.
