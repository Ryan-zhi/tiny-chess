# Tiny Chess — a 4K chess engine

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Ryan-zhi/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Ryan-zhi/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A complete chess engine that fits the [make.fun](https://make.fun)
**tiny-chess-01** bounty cap: the committed `main.py` is 3,838 bytes —
a `makefun compress` packing of the readable source (`engine_src.py`,
kept beside it), which the bundle sends along so the packed entry counts
as the source it was packed from.

## How it plays

- Full rules move generation on a 64-square board: castling, en passant,
  promotions, pins and check evasion — perft-verified against
  python-chess on a suite of positions.
- Negamax alpha-beta with iterative deepening under a fixed node budget
  (30,000 nodes — the engine is deterministic: no clocks, no randomness,
  so a replayed trial reproduces byte for byte).
- Quiescence search with check evasions, a transposition table, killer
  move ordering and check extensions.
- Piece-square-table evaluation with a bishop-pair bonus, scored from
  the side to move; drawn positions in the game's own history are
  recognised and steered around.
- Speaks the harness protocol: it serves `/game`, `/move` and `/resign`
  over HTTP from the environment URL, standard library only.

## Layout

- `main.py` — the engine as committed (packed).
- `engine_src.py` — the same engine as readable source (not committed;
  the bundle carries it).

MIT licensed.
