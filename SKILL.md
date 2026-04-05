---
name: threads
description: "Fetch and manage Amp (ampcode) conversation threads. List, search, read, export, rename, label, archive, share, delete threads and check usage."
---

# threads

Fetch and manage Amp conversation threads using the `amp` CLI.

The `amp` binary is at `~/.amp/bin/amp`. Always pass `--no-color` to strip ANSI codes.

## Identifying threads

Thread IDs look like `T-019d5cd4-492f-7298-90ae-a79f59bc5543`.

Users may provide:
- A full thread ID: `T-019d5cd4-492f-7298-90ae-a79f59bc5543`
- An ampcode URL: `https://ampcode.com/threads/T-019d5cd4-492f-7298-90ae-a79f59bc5543` — extract the thread ID from the path
- A thread title or topic — search first with `amp threads search`, then use the matching ID
- A partial ID — try it directly, amp may accept it

## Commands

Parse the args string to determine which command to run. If no args are provided, default to `list`.

---

### `list [--include-archived]`

List recent threads.

```bash
amp threads list --no-color
```

Add `--include-archived` if the user wants archived threads too.

---

### `search <query> [--limit N]`

Search threads by keyword, file path, or repo.

```bash
amp threads search "<query>" --json --no-color
```

Query syntax:
- Keywords: bare words or quoted phrases — `auth` or `"race condition"`
- File filter: `file:path` — `file:src/auth/login.ts`
- Repo filter: `repo:url` — `repo:github.com/owner/repo`
- Combine with implicit AND: `auth file:src/foo.ts repo:amp`

Use `--json` for structured output. Use `-n <limit>` to cap results.

---

### `read <threadIDOrURL>`

Fetch the full conversation as markdown.

```bash
amp threads markdown <threadID> --no-color
```

If output is very long, present a summary of the conversation structure first (number of messages, key topics), then show the most relevant parts. Ask the user which section they want to see if it's ambiguous.

When the user wants to "continue" or "pick up" an amp thread, read it first and summarize the key context and conclusions so they can continue the work here in Claude Code.

---

### `export <threadIDOrURL>`

Export thread as full JSON payload (includes tool calls, metadata, timestamps).

```bash
amp threads export <threadID> --no-color
```

---

### `usage <threadIDOrURL>`

Show token/cost usage for a thread.

```bash
amp threads usage <threadID> --no-color
```

---

### `rename <threadIDOrURL> <newName>`

Rename a thread. Quote names with spaces.

```bash
amp threads rename <threadID> "<newName>" --no-color
```

---

### `label <threadIDOrURL> <labels...>`

Add labels to a thread (additive, does not remove existing labels).

```bash
amp threads label <threadID> label1 label2 --no-color
```

---

### `archive <threadIDOrURL>`

Archive a thread.

```bash
amp threads archive <threadID> --no-color
```

### `unarchive <threadIDOrURL>`

Unarchive a thread.

```bash
amp threads archive <threadID> --unarchive --no-color
```

---

### `share <threadIDOrURL> [--visibility <v>] [--support [message]]`

Change thread visibility or share with Amp support.

```bash
# change visibility
amp threads share <threadID> --visibility public --no-color

# share with support
amp threads share <threadID> --support "need help debugging this" --no-color
```

Visibility options: `private`, `public`, `unlisted`, `workspace`, `group`.

---

### `delete <threadIDOrURL>`

Permanently delete a thread. **Ask for confirmation before running this.**

```bash
amp threads delete <threadID> --no-color
```

---

## Guidance

- When the user says "my amp threads", "ampcode threads", references an ampcode.com URL, or asks about a conversation they had in amp, use this skill.
- Always extract thread IDs from URLs before passing to amp commands. The URL format is `https://ampcode.com/threads/<threadID>`.
- For destructive operations (delete), always confirm with the user first.
- When reading long threads, don't dump the entire raw output. Summarize the conversation flow and highlight conclusions, decisions, and action items.
- If a command fails, check that `amp` is installed and the user is logged in (`amp login`).
