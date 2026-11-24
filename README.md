# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/wallsoupx/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/wallsoupx/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 0x88 negamax engine in 4 KB of Python. `main.py` is the whole engine
(4,076 bytes as committed, Python 3.13, standard library only). It reads,
imports or execs no other file.

## Run it

```sh
python3 -P -s main.py
```

## How it plays

- Iterative deepening to a fixed node budget (80,000 nodes/move), never a
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

---

<sub>Entered on [make.fun](https://make.fun/?ref=yx7q7cp0&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
