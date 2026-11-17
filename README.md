# tiny-chess-01 — a 4 KB Python chess engine

A from-scratch chess engine in a single `main.py` (at most 4,096 bytes,
packed with `node cli/makefun.mjs compress` from the readable `engine.py`).

Design: 0x88 board, negamax with alpha-beta and iterative deepening,
quiescence search (captures, promotions, check evasions), transposition
table, killer moves, history heuristic, MVV-LVA move ordering, null-move
pruning, late-move reductions and futility pruning, and an incremental
material + piece-square evaluation with a middlegame/endgame king blend
and bishop-pair bonus. The search runs to a fixed node budget per move
(60,000 nodes), never to a clock, so replays play the same moves.

Note on v3: an earlier build added static-exchange-evaluation pruning
and a check-evasion cap in quiescence; it scored only ~1,000 Elo on the
practice trial (1W 1D 4L, four losses by checkmate), so both were reverted
— this build is the v2 search, which scored 1,279 Elo (3.0/6) on the same
trial.

## Files

- `main.py` — the packed entrypoint (the only file the grader runs).
- `engine.py` — the readable source `main.py` was packed from.
- `LICENSE` — MIT.

## Grade locally

From the kit directory:

    node cli/makefun.mjs grade-local --kit . --bot <repo> --driver process
