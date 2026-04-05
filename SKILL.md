---
name: threads
description: "Access Amp (ampcode) conversation threads. Triggers when the user mentions amp threads, ampcode, or references an ampcode.com URL."
---

# threads

Access Amp conversation threads via the `amp` CLI (`~/.amp/bin/amp`). Always pass `--no-color`.

## When to trigger

Activate this skill whenever the user:
- Mentions "amp", "ampcode", or "amp thread"
- Pastes an `ampcode.com` URL — extract the thread ID from the path (`https://ampcode.com/threads/<threadID>`)
- Asks about a conversation they had in another coding agent
- Wants to continue, review, or reference work from an amp session

## Thread IDs

Thread IDs look like `T-019d5cd4-492f-7298-90ae-a79f59bc5543`. Users may provide a full ID, a URL, or just describe the thread by topic — in that case, search first.

## Available commands

All commands below are run via `amp threads <subcommand> --no-color`.

| Intent | Command |
|---|---|
| See recent threads | `amp threads list --no-color` |
| Find a thread by topic | `amp threads search "<query>" --json --no-color` |
| Read a thread | `amp threads markdown <threadID> --no-color` |
| Export as JSON | `amp threads export <threadID> --no-color` |
| Check token usage | `amp threads usage <threadID> --no-color` |
| Rename | `amp threads rename <threadID> "<name>" --no-color` |
| Add labels | `amp threads label <threadID> label1 label2 --no-color` |
| Archive | `amp threads archive <threadID> --no-color` |
| Unarchive | `amp threads archive <threadID> --unarchive --no-color` |
| Share / change visibility | `amp threads share <threadID> --visibility public --no-color` |
| Delete (confirm first!) | `amp threads delete <threadID> --no-color` |

Search query syntax: bare words, quoted phrases, `file:path`, `repo:url`. Combine with implicit AND.

## How to present results

- **Listing**: show the table as-is.
- **Reading**: don't dump raw output. Summarize the conversation — key questions, decisions, conclusions, action items. Show specific sections on request.
- **Continuing work**: when the user wants to pick up where an amp thread left off, read it, summarize the context and outcomes, then proceed with the work here.
- **Destructive ops**: confirm before deleting.
