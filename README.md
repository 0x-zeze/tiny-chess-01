# tiny-chess-01 — a 4 KB Python chess engine

A from-scratch chess engine in a single `main.py` (at most 4,096 bytes,
packed with `node cli/makefun.mjs compress` from the readable `engine.py`).

Design: 0x88 board, negamax with alpha-beta and iterative deepening,
quiescence search (captures, promotions, check evasions), transposition
table, killer moves, MVV-LVA move ordering, and an incremental
material + piece-square evaluation with a middlegame/endgame king blend
and bishop-pair bonus. The search runs to a fixed node budget per move,
never to a clock, so replays play the same moves.

## Files

- `main.py` — the packed entrypoint (the only file the grader runs).
- `engine.py` — the readable source `main.py` was packed from.
- `LICENSE` — MIT.

## Grade locally

From the kit directory:

    node cli/makefun.mjs grade-local --kit . --bot <repo> --driver process
