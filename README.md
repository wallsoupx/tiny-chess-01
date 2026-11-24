# tiny-chess-01

A 0x88 negamax engine in 4 KB of Python. `main.py` is the whole engine
(4,076 bytes as committed, Python 3.13, standard library only). It reads,
imports or execs no other file.

## How it plays

- Iterative deepening to a fixed node budget (60,000 nodes/move), never a
  clock: a replay plays the same moves.
- Negamax + alpha-beta, quiescence over captures, promotions and check
  evasions, MVV-LVA ordering, transposition table, killer moves, history,
  null-move pruning and late-move reductions.
- Eval is material + piece-square tables + bishop pair + endgame king
  term, kept incrementally; Zobrist keys from a fixed-seed LCG.
- The readable source is `engine.py` (not committed); `main.py` is the
  kit packer's compressed output of it.

## The size rule

- `main.py` at most 4,096 bytes as committed; the whole tree at most
  8,192 bytes, no file over 4,096. MIT licence.

## Grade it locally

From inside the competition's dev kit:

    makefun grade-local --kit . --bot <your repository> --driver docker

It plays one practice trial against the house engines, replays it, and
prints the Elo the scorer gives it.
