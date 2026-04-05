# amp-threads

claude code skill for fetching and browsing [amp](https://ampcode.com) conversation threads.

## what it does

- lists recent amp threads with titles, dates, and visibility
- searches threads by keyword, file path, or repo
- reads full thread conversations as markdown
- exports threads as json
- manages threads (rename, label, archive, share, delete)
- shows token usage for threads

## setup

copy `SKILL.md` into your claude code skills directory:

```bash
mkdir -p ~/.claude/skills/threads
cp SKILL.md ~/.claude/skills/threads/SKILL.md
```

requires the `amp` cli to be installed and authenticated (`amp login`).

## commands

### list

```
/threads list
/threads list --include-archived
```

### search

```
/threads search auth
/threads search "race condition"
/threads search file:src/auth/login.ts
/threads search EvmFactory repo:github.com/foundry-rs/foundry
```

### read

```
/threads read T-019d5cd4-492f-7298-90ae-a79f59bc5543
/threads read https://ampcode.com/threads/T-019d5cd4-...
```

### export

```
/threads export T-019d5cd4-...
```

### usage

```
/threads usage T-019d5cd4-...
```

### rename

```
/threads rename T-019d5cd4-... "new thread name"
```

### label

```
/threads label T-019d5cd4-... bug priority
```

### archive / unarchive

```
/threads archive T-019d5cd4-...
/threads unarchive T-019d5cd4-...
```

### share

```
/threads share T-019d5cd4-... --visibility public
/threads share T-019d5cd4-... --support "need help with this"
```

### delete

```
/threads delete T-019d5cd4-...
```

## license

MIT OR Apache-2.0
