# Weekly Research Brief — Commercial Awareness News Digest

This is the instruction set the scheduled Claude run follows every **Saturday night**.
Goal: produce **at least 15** draft news items for review, written in the Elite Pathfinder
voice and passed through the No-Slop filter.

---

## The job

1. Search the web for the week's most important commercial / legal / financial news.
2. Prioritise **Hong Kong** (the audience is applying to HK law firms). Include global news
   only where it clearly matters to HK clients or HK firms (e.g. US rate decisions, China
   policy, global M&A trends, cross-border regulation).
3. Spread items across **practice areas** — don't return 15 capital-markets stories. Aim for a
   mix: Corporate / M&A, Capital Markets, Banking & Finance, Disputes, Financial Regulatory,
   Competition, Employment, IP / TMT, FinTech, Real Estate, Restructuring, Tax, Funds,
   China / Cross-border, ESG.
4. **Know your reader.** These are students who may understand *nothing* about finance, law,
   or business. Explain everything like they are smart but completely new to it. Define every
   term in plain words the first time it appears (e.g. "an IPO is when a company sells its
   shares to the public for the first time"). Never assume prior knowledge.
5. For each story, write three parts:
   - **What's the news?** — a single paragraph of **4–5 full sentences** that explains the
     story from scratch, defining any jargon. This is the part that teaches them what happened.
   - **Why it matters to clients** — **3 bullet points**, each **2–3 sentences**. Spell out the
     cause-and-effect chain in simple terms. E.g. "If the US cuts interest rates, borrowing gets
     cheaper. So companies are more likely to take out big loans. That means more deal activity."
   - **Why it matters to law firms** — **3 bullet points**, each **2–3 sentences**, following
     the same simple cause→effect→why-it-matters flow, always landing on the commercial point:
     which team gets work, why a firm earns more, why a candidate should care.
6. Add a punchy, commercial headline (a little wordplay is fine; never clickbait).
7. Tag 1–2 practice areas and a region.
8. **Sources are mandatory.** Capture at least one real, working link per item that points to
   the detailed news so a student can click through and read more. Never invent a URL.

## Sources to favour

HKEX, HKMA, SFC, the Judiciary, IRD, Competition Commission, the Hong Kong government
gazette, plus reputable outlets: SCMP, Reuters, Bloomberg, FT, Law360, Hong Kong Lawyer.
Always capture at least one source URL per item. Never invent facts or quotes — if you can't
verify it, drop it.

## Voice & style (non-negotiable)

- Follow the Elite Pathfinder voice: insider, commercial, direct. Frame everything around what
  a partner actually cares about.
- Run every sentence through the **No-Slop filter**: no banned words (delve, leverage,
  navigate, landscape, foster, crucial, seamless, etc.), no "not X but Y" structure, no cliché
  openers/closers, vary sentence length, don't overuse dashes.
- This is for ambitious law students. Respect their time. Skimmable, sharp, useful.

## Output format

Append the new items to `data/digest.json` with `"status": "pending"`. Use this shape:

```json
{
  "id": "2026-W27-001",
  "status": "pending",
  "headline": "...",
  "week": "2026-W27",
  "weekLabel": "23–29 Jun 2026",
  "date": "2026-06-26",
  "region": "HK",
  "practiceAreas": ["Capital Markets"],
  "whatsTheNews": "... one paragraph, 4–5 sentences, explains everything from scratch ...",
  "clients": ["bullet 1 (2–3 sentences)", "bullet 2 (2–3 sentences)", "bullet 3 (2–3 sentences)"],
  "lawFirms": ["bullet 1 (2–3 sentences)", "bullet 2 (2–3 sentences)", "bullet 3 (2–3 sentences)"],
  "sources": [{"title": "SCMP", "url": "https://..."}]
}
```

- `id` = `<ISO-week>-<3-digit sequence>`, unique.
- `week` = ISO week code (e.g. `2026-W27`). `weekLabel` = human range, e.g. `23–29 Jun 2026`.
- Do **not** touch existing items. Only append new `pending` ones.
- After appending, report a one-line summary: how many items, which practice areas covered.

## What happens next

The founder opens `admin/admin.html`, reviews the pending queue, edits freely, approves the
keepers, then exports `published.json` and pushes it to the live site. Nothing reaches students
until approved.
