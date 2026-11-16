# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/hhhtdy4-collab/Tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/hhhtdy4-collab/Tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine that fits in 4 KB of Python. Negamax alpha-beta search with
quiescence, killer-move and MVV-LVA ordering, and piece-square-table
evaluation. It searches to a fixed node budget (30,000 nodes), never a
clock, so every game replays move for move. `main.py` is the whole engine;
it plays a full gauntlet of games over HTTP against the environment server
named by `MAKEFUN_ENV_URL`.

Two fancier variants were built and tested during development — quiescence
with check evasions, and null-move pruning at a higher node budget. Both
scored worse or ran too close to the trial wall-clock limit, so the simpler
configuration above is the one entered.

## Practice results

Local practice gauntlets (6 games each against the kit's house engines,
Elo anchors 855–1596):

- Trial 0: 2 wins, 1 draw, 3 losses (2.5 points, about Elo 1191)
- Trial 1 (colours swapped, different openings): 1 win, 1 draw, 4 losses
  (1.5 points)

Move generation is verified by perft: perft(3) from the start position is
8902, matching the known value.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8791 python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=zj702qgy&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
