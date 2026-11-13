# tiny-chess-01-v13

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)

A 4 KB chess engine for make.fun's tiny-chess-01 bounty: alpha-beta search
with late move reductions, 75,000 nodes per move, 4,055 bytes of Python.

## Run it

```sh
MAKEFUN_ENV_URL=<trial env url> python3 main.py
```

The engine plays the trial through the make.fun env (POST /game, /move) and
exits when every game is over. Standard library only, deterministic.
