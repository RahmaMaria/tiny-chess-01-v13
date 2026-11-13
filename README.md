# tiny-chess-01-v13

A 4 KB chess engine written for the make.fun tiny-chess-01 bounty. The whole
engine lives in a single Python file, `main.py`, which is a tiny wrapper that
decompresses (LZMA + base85) the packed engine at startup and runs it.

The engine itself is an alpha-beta searcher with late move reductions (LMR),
tuned to play within the competition's size limit while still searching hard:
it spends up to 75,000 nodes on every move. The packed engine code is 4,055
bytes of Python; the file on disk is 4,073 bytes including a trailing version
comment and newline, still comfortably under the 4,096-byte cap.

In practice games against the trial opponents it averaged around Elo 1,298,
which is a solid club-player level for an engine that fits in four kilobytes.

## Running it

Set the environment URL, then run the engine:

```
export MAKEFUN_ENV_URL=<trial environment URL>
python3 main.py
```

The engine talks to the make.fun trial environment over HTTP: it creates a
game with `POST /game`, then plays its moves through `POST /move`, and exits
once every game is over.

## Notes

- Standard library only — no third-party packages, and no network calls
  except to the trial environment itself.
- Deterministic: the same position always gets the same move, so trial runs
  are reproducible.
