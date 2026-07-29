---
name: meeting-extract
description: Extract Decisions, Commitments, Preferences, and Key Insights from a meeting transcript into the Obsidian vault. Creates a meeting note in "04 - Meetings", creates/updates canonical People/Company/Project notes, adds commitments as checkboxes on person pages, updates the relevant MOC, and archives the raw transcript. Invoke when the user drops a transcript (Fathom/Granola) and wants it turned into linked vault notes. Args: optionally the transcript filename or client name (e.g. "/meeting-extract Ativacao Nina").
---

# Meeting Extract → Second Brain

Turn a raw meeting transcript into structured, interlinked vault notes. Follow the steps in order and stop at each **CHECKPOINT** before continuing.

## 0. Load context (always)

- Read `USER.md`, `SOUL.md`, `IDENTITY.md`, `CLAUDE.md` at the vault root.
- **Use the REAL folder names**, not CLAUDE.md's scheme. They are:
  `00 - Inbox`, `01 - People`, `02 - Projects`, `03 - Companies`, `04 - Meetings`, `05 - Knowledge`, `06 - MOCs`, `07 - Archive`.
- **Language: Portuguese** for all note content (per USER.md), even if the request is in English.
- List existing notes in People/Projects/Companies/Meetings/MOCs so you can dedupe (never create a duplicate canonical note — search first).

## 1. Locate the transcript

- Look in `00 - Inbox` first. If the user passed a name/client as an argument, match it there.
- If more than one candidate and it's ambiguous, ask which one.
- Read the **entire** transcript (transcripts are long and paginate — page through to the end; decisions and action items are often in the last third).

## 2. Identify attendees and sides — CHECKPOINT ⛔

- List every real participant. Map each to their **company** and **role**.
- Transcription tools mangle names (e.g. "Ian"/"Iazê"/"Arian" = **Yan Simmer**; "Dr. Marques" = **Marcos**). Normalize to the canonical person; note the alias in the person page.
- Separate **smartside.ai** people from **client** people. Watch for co-hosts with no `@client.com` tag.
- **If a person's side/affiliation is NOT explicit in the transcript, DO NOT assert it.** Make the lightest defensible claim and add a `⚠️ A confirmar` note (Transparência value from SOUL.md). Never fabricate an employer or role.
- Note people referenced but absent (they may own decisions/commitments and still need a page).

**⛔ CHECKPOINT — before writing anything, state to the user:** the meeting date, the attendee→side mapping (flagging any uncertainty), the client/project this belongs to, and the filename you'll use. Proceed once it looks right (or the user corrects you).

## 3. Enforce data isolation (absolute rule from IDENTITY.md)

- Each client is an isolated compartment. **Never reference one client's data, context, or people inside another client's notes.**
- Only exception: smartside.ai's own reusable internal assets (the CRM product, stack, workflows) may appear across clients.
- A shared internal index like `Clientes MOC` listing client *names* is fine; cross-referencing client *content* is not.

## 4. Extract the four sections

Read the transcript for signal, skip small talk. Populate:

1. **DECISIONS** — what was decided, **by whom**, and **why**. Separate firm decisions from "pending confirmation" and "in development / decided-not-yet-delivered".
2. **COMMITMENTS** — who promised what, **by when**. Group by owner (smartside vs client). Convert relative dates to absolute (e.g. "próxima semana" → the actual week; "segunda" → the dated Monday). Anchor each to the meeting note.
3. **PREFERENCES** — how people want to work and communicate (channels, cadence, tone, escalation).
4. **KEY INSIGHTS** — frameworks (e.g. SPIN), strategic shifts, non-obvious observations, risks, product/tier structures.

Capture `ACTION ITEM:` markers from the transcript as commitments.

## 5. Write the meeting note (canonical)

- File: `04 - Meetings/YYYY-MM-DD Title.md` using the **meeting's actual date** (from the transcript), not necessarily today. If today ≠ meeting date, use the meeting date and say so.
- Frontmatter: `type: meeting`, `date`, `tags`, `attendees` (wikilinks), `project`, `company`, `source` (link to transcript), `recording` (URL).
- Body: the four sections. Bullets, concise, no filler.
- Link every attendee `[[Name]]`, the `[[Project]]`, the `[[Company]]`.

## 6. Create / update satellite notes

For each, **search before creating**; update the existing canonical note instead of duplicating.

- **People** (`01 - People/<Name>.md`): one per attendee (+ pivotal absentees). Frontmatter `type: person`, `company`, `role`, `links`. Body: company, role in project, a `## Compromissos` section with commitments **as checkboxes** `- [ ] … — [[meeting note]]`, and a `## Reuniões` list. If the person already exists, **append** a new project-grouped commitments block and the meeting link (additive only — never delete existing content).
- **Company** (`03 - Companies/<Name>.md`): relationship, segment, stack, people, projects, meetings.
- **Project** (`02 - Projects/<Name>.md`): scope, key rules, in-development, open items, platforms, related notes.
- **MOC** (`06 - MOCs/`): update the relevant MOC (e.g. `Clientes MOC`) — add the new cluster, remove the item from any "to document" list.

## 7. Safety & cleanup

- **Never delete a note.** Superseded material → `07 - Archive`.
- Additive edits to existing pages are fine when the task explicitly calls for them (adding commitments/meeting links). Ask before edits that touch >20 files or that remove/rewrite existing content.
- After processing, **ask** before moving the raw transcript from `00 - Inbox` → `07 - Archive` (don't move silently).

## 8. Report back

Summarize files created/updated, and proactively flag (per IDENTITY.md): quality/data issues found in the transcript, deadline/delivery risks, Shiva-program risk, anything below the agreed quality bar, and any affiliation you had to guess.

---

## Good vs. bad output

### Commitment — GOOD
```markdown
## Compromissos
- [ ] Corrigir docs/fluxos: timeout 14→5 min, horário 09h18, +4º follow-up — [[2026-07-03 Knewin - Ativação Nina]]
```
Owner is clear, action is specific, deadline/context captured, linked to its source meeting, rendered as a checkbox.

### Commitment — BAD
```markdown
## Commitments
- Fix the docs and follow up on some things soon.
```
Vague ("some things", "soon"), English (vault is PT), no owner, no link, not a checkbox, no date resolution.

---

### Decision — GOOD
```markdown
- **Método de qualificação = SPIN Selling.** Por: smartside. Motivo: método validado, padrão em pré-vendas.
```
States what, by whom, and why — the three things a decision must carry.

### Decision — BAD
```markdown
- They'll use SPIN.
```
No owner, no rationale, and mixes a decision with unrelated notes.

---

### Attendee mapping — GOOD
> Vanessa Ribeiro — placed on smartside (Customer Success) **with a ⚠️ confirm note**, because her side wasn't explicit in the transcript (no `@client.com` tag).

Honest about uncertainty; makes the lightest defensible claim.

### Attendee mapping — BAD
> Vanessa Ribeiro — Knewin, Head of Marketing.

Invents an employer and a title the transcript never stated — violates Transparência and corrupts the canonical person note.

---

### Data isolation — GOOD
A Knewin meeting note references only Knewin people, products (Dino, CC Clipping), and stack.

### Data isolation — BAD
A Knewin note says "similar to what we built for Ebramed's funnel" — leaks one client's context into another's compartment.

---

## Quick checklist
- [ ] Read USER/SOUL/IDENTITY/CLAUDE + used real folder names
- [ ] Read the WHOLE transcript
- [ ] Attendee→side map confirmed at CHECKPOINT (uncertainty flagged)
- [ ] Data isolation respected
- [ ] 4 sections extracted; dates made absolute; small talk skipped
- [ ] Meeting note created (named by meeting date), all links resolve
- [ ] People/Company/Project created or updated (deduped, additive)
- [ ] Commitments are checkboxes on person pages
- [ ] Relevant MOC updated
- [ ] Asked before archiving the transcript
- [ ] Reported back with proactive flags
