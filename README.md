# tiny-chess-blade

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/youthmy11-ai/tiny-chess-blade/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/youthmy11-ai/tiny-chess-blade/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Deterministic <=4 KB Python 3.13 chess engine (`0x88` bit-compact search, Zobrist TT, quiescence, killer/MVV-LVA ordering, fixed deterministic node budgets).

## Practice Gauntlet

- `main.py` size: `4093 bytes` (compressed from `src/engine.py` `8376 bytes` via `makefun compress`)
- Practice gauntlet (`16 wins, 1 draw, 1 loss` across 18 games, mean Elo `1858`, peak Elo `2112`):
  - `trial-0`: Elo `1809` (`5W-1D-0L`, `479` spare plies, wall `595.03s` / `715.04s`, 100% deterministic across 2 runs; beats `nodes-500k`)
  - `trial-1`: Elo `2112` (`6W-0D-0L`, 6/6 checkmates including `nodes-500k`, `561` spare plies, wall `727.14s`)
  - `trial-2`: Elo `1654` (`5W-0D-1L`, 5 checkmates, `563` spare plies, wall `544.94s`)

## Architecture

`0x88` board + 64-bit bitboard occupancy/pawn masks (`P, O`), incremental PST + Zobrist hashing, PVS alpha-beta with TT, null-move, LMR, razoring, futility, SEE-guarded capture sorting, and endgame mop-up.

## Run it

```sh
python3 -P -s main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
