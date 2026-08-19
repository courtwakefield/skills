---
name: copy-safe-deliverables
description: Put any text the user will paste somewhere else — emails, Slack messages, memos, posts, bios, commit messages, job descriptions, ad copy, prompts, SQL, meeting invites, press releases — inside its own copy-button container, with all commentary kept outside it. Use this whenever the user asks you to write, draft, revise, polish, shorten, rewrite, or "clean up" something that is destined for an inbox, a document, a form field, a ticket, or another human's eyes. Default to using it whenever there is any chance the output leaves the chat window, even if the user did not ask for a special format.
---

# Copy-Safe Deliverables

## The problem this solves

When you write a draft and wrap it in conversational framing — "Here's a draft for you!", "Let me know if you want it punchier" — the user selects the whole reply, copies, and pastes. Your commentary rides along into the email, the shared doc, or the deck that goes to a VP. This is embarrassing for the user in a way that is entirely preventable, and they usually don't notice until after they've hit send.

The fix is structural, not a matter of being careful with wording: **the deliverable goes in a container that has its own copy button, and nothing else goes in that container.** Then a copy is always a clean copy, no matter how the user grabs it.

## The core rule

Every reply that contains a deliverable has two zones:

- **Inside the container**: the finished artifact, exactly as it should appear in its destination. Nothing else.
- **Outside the container**: greetings, rationale, options, caveats, questions, next steps, notes about what you changed.

If you find yourself writing "Here's the..." or "Feel free to adjust..." inside a container, that's the signal you've crossed the line.

## Choosing the container

The deciding question is whether the content's line breaks are meaningful, because that determines whether a non-wrapping container is acceptable.

**A message-composition tool**, if one is available in the environment — the best default for prose a person will read: emails, Slack messages, texts, bios, posts, short blurbs. It soft-wraps, separates subject from body, and offers copy or open-in-app buttons. Reach for this first for anything message-shaped.

**A created file / artifact** — use for prose too long or too formatted for a message widget: multi-page documents, anything needing headings, bold, or tables preserved, real .docx/.xlsx/.pptx deliverables, or content containing its own code fences. Files render wrapped and formatted with their own copy and download affordances. Present the file rather than dumping its text into the reply.

**Fenced code block** — correct when line breaks carry meaning and lines are naturally short: code, SQL, JSON, YAML, config, commit messages, a subject line, a headline, a URL, a single-line snippet. Use the real language tag for code, or `text` for short plain strings.

### Never hard-wrap prose to make it fit

Fenced blocks do not soft-wrap. A 500-character paragraph on one line becomes a horizontal scrollbar, which is bad on desktop and worse on a phone.

The tempting fix — inserting line breaks every 80 characters so it looks tidy — is a trap. Those newlines are real characters that get copied, so the user pastes a bio into LinkedIn or an email body and gets ragged breaks mid-sentence that they then have to hunt down and delete. That's a worse failure than the one this skill exists to prevent, because it's silent and it's *inside* the deliverable.

Wrapping must be visual only. If prose would scroll sideways in a fence, that's the signal to move it to a wrapping container, not to reformat the text.

If no wrapping container is available in the environment, a fence is still better than loose text — keep the paragraph on one line, accept the scroll, and mention that the block is scrollable. Preserve the paste; the scrollbar is the lesser cost.

## Rules for what goes inside

**One deliverable per container — and one container per call.** Two variants of a headline means two containers, each independently copyable, with the labels *outside* or between them. Never put "Option A" and "Option B" in the same block: the user can only copy both.

This applies to tools that accept multiple variants in a single call. It's tempting to pass all the options at once and let the widget tab between them, but that buries every option after the first — people copy what's on screen and often don't notice there's a second tab. Issue a separate container for each version instead, with a line of your own text between them naming what each one is for. The extra containers cost a little vertical space and buy the user a visible, side-by-side choice. Reserve the multi-variant form for cases where the user explicitly asked for a compact set to flip through.

**Split by paste destination, not by document structure.** An email subject line goes in one field and the body in another, so they get separate containers. A blog post's title, meta description, and body are three separate paste targets, so three containers. If two pieces will always be pasted together, keep them together.

**Preserve placeholders, drop instructions.** `[Client name]` and `[date]` belong inside — they're part of the artifact and the user will fill them. "Swap in their actual title here" is a note to the user and belongs outside.

**No decoration.** Don't add horizontal rules, emoji, or a "Subject:" label the user didn't ask for. Don't add a signature block unless they gave you one. Everything inside the container should survive a paste with zero editing.

**Revisions get a fresh, complete container.** When the user asks for a change, reissue the entire deliverable in a new container rather than showing a diff or just the changed paragraph. Describe what changed outside the container. The user should never have to assemble a final version from pieces across your replies.

## When this doesn't apply

Don't containerize things meant to be read in the chat: explanations, analysis, brainstormed lists, answers to questions, coaching, comparisons, or your reasoning about a draft. Wrapping conversational content in a code block makes it harder to read and dilutes the signal — a container should reliably mean "this is the thing you're going to paste."

Genuinely ambiguous cases (a list of subject-line ideas the user might use as-is, or might just be browsing) can go either way. Containerizing is the safer error: an unnecessary code block is mildly awkward, while a leaked "Let me know what you think!" in a client email is not.

## Examples

**Example 1 — a simple draft**

Prompt: "Write a short email asking my team to submit expense reports by Friday."

Wrong (commentary and deliverable share one selection):

> Sure! Here's a friendly reminder email:
> Hi team — Just a reminder that expense reports are due Friday...
> Let me know if you want it firmer!

Right — the subject and body go into a message-composition widget, which keeps them in separate fields and wraps the body. All commentary stays in the reply:

> [message widget: subject "Expense reports due Friday", body "Hi team, / A quick reminder that expense reports for this month are due end of day Friday..."]

I kept this light since it's a routine reminder. Say the word if you want a firmer version for repeat offenders.

Without a message tool available, the subject line goes in a fence (short, single line) and the body goes in a created file (prose that needs to wrap).

**Example 2 — variants**

Prompt: "Give me two versions of a LinkedIn headline, one safe and one bold."

Headlines are short single lines, so fences are fine here. Each version gets its own container so the user copies exactly one — and if these were paragraphs going into a message tool, that would be two separate calls, not one call with two variants:

Safe:
```text
Operations leader helping healthcare teams ship faster without breaking compliance
```

Bold:
```text
I fix the operational mess between "we should automate this" and "it's live"
```

**Example 3 — not a deliverable**

Prompt: "What's a good structure for a project kickoff email?"

This is advice about writing, not the thing being pasted — answer conversationally in prose, with no container. If the user follows up with "okay, write it for me," that reply gets a container.

## Before sending, check

- Could the user select my entire reply, paste it, and end up with words that aren't part of the deliverable? If yes, the containers aren't doing their job.
- Is the content inside each container complete and final, requiring no cleanup after paste?
- Does each container correspond to exactly one paste destination?
- Is any option hidden behind a tab or toggle where the user might miss it?
- Does any paragraph of prose sit in a non-wrapping fence where it will scroll sideways?
- Did I add any line break that isn't part of the deliverable itself?
