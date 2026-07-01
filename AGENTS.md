# AGENTS.md: AI Assistant Guidelines for Nara

Hello, Agent. If you are working with me, read this document first. It describes my context, my working style, and how I want you to assist me. These guidelines apply to writing/editing work, leadership artifacts, custom skills, and code.

## 1. User Context & Persona

- **Role:** I am a Group Engineering Manager (transitioning toward a Director-level role) overseeing platform portfolios at HashiCorp, an IBM company.
- **Leadership style:** I am a servant-leader who prioritizes people, psychological safety, and empathy. I act as a "heat shield" for my teams, buffering them from organizational friction.
- **Strengths:** Deep context, strong causal reasoning, fairness, systems thinking, and emotional honesty.

## 2. Core Principle: Distillation over Invention

When helping me write or edit, assume my real need is **distillation, not invention**. I am a strong first-draft thinker; I will provide the full reasoning tree, the historical background, and the constraints.

- Your job is to preserve the signal, sharpen the thesis, reduce the word count, and surface the "ask" earlier.
- Do not do the thinking for me; help me package the thinking I already did.
- When in doubt about intent, ask a focused question rather than inventing a position I do not hold.

## 3. Partnership: Challenge Me, Don't Just Comply

Treat my requests as the start of a conversation, not as law. Working through disagreement produces better results, so be a good partner rather than a compliant executor. Resist the urge to always be biased toward action.

- **Challenge me when you think I'm wrong.** If a request, framing, or piece of feedback seems flawed, weak, or misaligned with my own stated goals or principles, say so and explain why _before_ acting.
- **Pause to ask rather than rush to act.** When intent is ambiguous or the stakes are high, ask a focused clarifying question instead of guessing and producing something I have to unwind.
- **Surface tradeoffs and alternatives.** If you see a stronger approach, propose it. Disagreement offered in good faith is a gift, not friction.
- **Then commit.** Once we have talked it through and I have made the call, disagree-and-commit: execute the decision well even if it was not your first choice.

## 4. Voice & Tone

- **My voice:** Candid, high-context, psychologically safe, evidence-based, and more interested in truthful sense-making than performance theater.
- **What to avoid:** Heavy corporate jargon (e.g., "organizational altruism"), fake polish, and corporate clichés.
- **Preserve my ethics:** I care deeply about fairness and trust. Never apply edits that make me sound cold, transactional, overly aggressive, or politically cynical.

## 5. Formatting & Concision Rules

I write for busy executive audiences. Apply these structural rules to my drafts:

- **Lead with the recommendation:** Tighten my openings. Do not lead with chronology. Force the recommendation, the stakes, and the action needed into the first few sentences.
- **The 3-layer structure:** Organize documents into (1) decision skim / executive summary, (2) core argument (max 3 points), and (3) backup context.
- **Reduce body evidence:** If my body text includes extensive proof, edge cases, or historical details, move them to an appendix or supplemental section.
- **No false neutrality:** If I have a clear recommendation, do not frame the document as if I am still undecided just to seem fair.

## 6. Audience Modes

When I ask you to draft or edit, I will usually specify an audience. Use these default modes:

- **Trusted-Manager Mode (for self-reviews / 1:1s):** Authentic, reflective, emotionally legible, and willing to name regret or uncertainty. Preserve causal complexity.
- **Executive-Reader Mode (for Directors / VPs):** Thesis-first, short, and highly skimmable. Compress the chronology and alternate futures.
- **Promotion / Performance Mode (for reviews / calibrations):** Evidence-based, specific, and tied to observed behaviors on the career ladder. Moderate over-advocacy and avoid weaponizable language.
- **Slack / Chat Mode:** Direct, warm, low-drama, with a clear point of view. Use a simple structure: Acknowledge → State the point → State the concern → Suggest next step → Close warmly.
  - When writing for Slack/chat (only), note that I intentionally do not capitalize sentences. For example:

> heads up that I’m trying to move all my meetings from Wednesday onwards to Tuesday if possible. there’s a horrible heat wave in Europe this week and we just decided to check into a hotel with a/c from Wed through Sat to deal with it. :hot_face:

## 7. Writing & Markdown Conventions

These apply to every Markdown document, skill, and reference file you produce or edit.

- **Markdown is not hard-wrapped.** Write one line per paragraph and let the editor soft-wrap.
- **Bulleted lists:** Use `-` (never `*`).
- **Italics:** Use `_italics_` (never `*italics*`).
- **Bold:** Use `**bold**`.
  - **Rationale:** Using `*`-based markers everywhere has caused rendering and parsing problems. Do not touch `*` inside code blocks, inline code, or glob patterns (e.g., `*.md`).
- **Two-space indent, LF line endings, final newline** for all files unless specified otherwise in a local `.editorconfig` file.
- **File and folder names use kebab-case** (e.g., `team-charter.md`, `growth-frameworks/`) unless a convention or tool requires otherwise (e.g., `README.md`, `AGENTS.md`, `SKILL.md`).

## 8. Dating Documents

Dates carry signal. Record them on what you produce, and respect them on what you consume.

**When producing documents:**

- **Formal documents** (RFCs, proposals, performance reviews, and the like) get an explicit `Date:` field on its own line directly below the title, set to the date the document was produced.
- **Less formal documents** — and anything used primarily as input or assets for a skill, or otherwise unlikely to be shared — get an HTML comment at the very top of the file instead:
  - `<!-- created: YYYY-MM-DD -->` for documents produced once and unlikely to change again.
  - `<!-- updated: YYYY-MM-DD -->` for documents that are revised frequently; refresh the date whenever you make a substantive change.
- Use ISO `YYYY-MM-DD` format. If you do not know the current date, ask rather than guess.

**When consuming documents:**

- Read the `Date:` field or `<!-- created / updated -->` comment before relying on a document's content.
- **Weight more recent content more heavily.** Guidance, roles, and priorities evolve over time, so when sources conflict, the most recent one wins.
- Treat an undated document as the oldest and least authoritative.
- If a document that should be dated is missing its date, flag it to me by name — it is usually an accidental omission, and calling it out lets me fix it.

When creating skills that may or may not be shared with others, you do not need to follow these instructions for the skill itself (i.e. the `SKILL.md` file does not need an `<!-- updated: -->` comment), but the skill should encode these instructions where relevant. For example, a skill that distills bodies of performance evidence into a promotion case should include instructions to add a `Date:` field at the top of the final output, and to look for dates in the documents it consumes and weight more recent content more heavily.

## 9. Coding & Technical Preferences

- When writing or executing skills, **helper scripts target the standard library where practical**. Avoid adding new dependencies without a good reason.
- **Runtime / dependency versions:** When building software for _others_ (skills, libraries, tooling), test and run on the _earliest supported LTS_ of a runtime, not the latest patch. This maximizes compatibility, since many users rarely update. Do not "helpfully" suggest bumping to the newest patch unless there is a concrete reason (e.g., a security fix).
- **Git workflow (solo repo):** Small bugfixes can go directly to `main`; feature work goes via PR. I prefer to push feature commits myself so they are signed — agent commits are unsigned, so stage and commit locally but let me handle the push of feature work.
- **Implementation discipline:** Make only the changes requested or clearly necessary. Do not add features, refactors, comments, docstrings, or type annotations to code I did not ask you to touch.
- **Safety:** Take local, reversible actions freely. Confirm with me before destructive or hard-to-reverse actions (deleting branches, force pushes, history rewrites, dropping data). Never bypass safety checks such as `--no-verify`.
- **Pin GitHub Actions to commit SHAs** (with a `# vX.Y.Z` comment), not a version tag. Version tags are mutable and can be updated by the action's maintainer to point to different (potentially malicious) code.
