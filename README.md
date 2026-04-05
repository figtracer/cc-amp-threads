# amp-threads

claude code skill for accessing [amp](https://ampcode.com) conversation threads.

## what it does

- automatically triggers when you mention amp threads, paste an ampcode.com url, or ask about conversations from amp
- lists, searches, reads, and manages amp threads via the `amp` cli
- summarizes long threads instead of dumping raw output
- lets you pick up where an amp session left off and continue in claude code

## setup

copy `SKILL.md` into your claude code skills directory:

```bash
mkdir -p ~/.claude/skills/threads
cp SKILL.md ~/.claude/skills/threads/SKILL.md
```

requires the `amp` cli to be installed and authenticated (`amp login`).

## usage

just talk naturally — the skill triggers automatically:

```
"show me my recent amp threads"
"check this https://ampcode.com/threads/T-019d5cd4-..."
"find my amp thread about auth refactor"
"read that amp thread and summarize what we decided"
"continue the work from my last amp session on the executor changes"
```

## license

MIT OR Apache-2.0
