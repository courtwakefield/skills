# copy-safe-deliverables

A [Claude Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that keeps AI commentary out of the things you paste elsewhere.

## The problem

When an LLM drafts an email, a bio, or a post, it usually wraps the draft in conversation: "Here's a draft for you!" ... "Let me know if you want it punchier." You select the reply, copy, paste — and the commentary rides along into the email, the shared doc, or the deck that goes to a VP. People rarely notice until after they've hit send.

## The fix

The solution is structural rather than a matter of careful wording. Every deliverable goes into a container with its own copy button, and nothing else goes in that container. A copy is then always a clean copy, however the user grabs it.

The skill covers:

- **Two zones per reply** — the artifact inside the container, everything else outside it.
- **Container selection by content type** — message widgets and files for prose that needs to soft-wrap, code fences for content where line breaks are meaningful and lines are short.
- **No hard-wrapping** — inserting line breaks to avoid horizontal scroll puts real newlines into the deliverable, which is a worse and quieter failure than the one being prevented.
- **One deliverable per container, one container per call** — variants get separate boxes rather than tabs, since people copy what's on screen.
- **Splitting by paste destination** — an email subject and body go to different fields, so they get different containers.
- **When not to trigger** — explanations, analysis, and brainstorming stay conversational, so that a container reliably means "this is the thing you paste."

## Installation

**Claude apps (web, desktop, mobile):** download `copy-safe-deliverables.skill` from the [Releases](../../releases) page and upload it in Settings → Capabilities → Skills.

**Claude Code:** clone into your skills directory.

```bash
git clone https://github.com/<your-username>/copy-safe-deliverables.git \
  ~/.claude/skills/copy-safe-deliverables
```

**Any other setup:** the skill is a single Markdown file. Copy the contents of `copy-safe-deliverables/SKILL.md` into your system prompt or project instructions.

## Repository layout

```
copy-safe-deliverables/
└── SKILL.md      # YAML frontmatter (name, description) + instructions
README.md
```

The `description` field in the frontmatter is what determines when the skill triggers, so edit it if you want the skill to fire more or less eagerly. It is currently written to trigger readily on anything that might leave the chat window.

## License

MIT
