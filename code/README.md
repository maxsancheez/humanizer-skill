# tells.py

A standard-library Python script that runs Pass 1 of the humanizer skill: it finds the tells and quotes each one. It does not rewrite anything.

## Run it

```bash
python3 tells.py samples/ai_draft.txt samples/humanized.txt
```

Or pipe text in:

```bash
pbpaste | python3 tells.py -
```

Exit code is `0` when no tells are found and `1` otherwise, so you can use it as a pre-publish check in a script or git hook.

## Files

- `tells.py`: the detector. Patterns live in the `PATTERNS` list at the top; add your own there.
- `samples/ai_draft.txt`: a deliberately tell-heavy paragraph written for this demo.
- `samples/humanized.txt`: the same content rewritten by hand following the skill's Pass 2 rules.

## Limits

- Regexes are blunt. "Studies show" is flagged as unnamed authority even when a citation follows it.
- It counts tells, it doesn't detect AI. A person can write "pivotal" and a model can write clean prose.
- Sentence-level checks (same opener, back-to-back questions) use a naive sentence splitter and will miss some cases.
