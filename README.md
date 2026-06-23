# Commercial Awareness News Digest

A Finimize-style weekly news digest for Elite Pathfinder students. Each item explains
**what the news is**, **why it matters to clients**, and **why it matters to law firms** —
HK-first, in the Elite Pathfinder voice.

Three parts, all free, all running on the Claude **subscription** (no API credits):

```
research  →  admin (approve)  →  publish  →  students see it
 (Claude)      (you)            (GitHub)      (Squarespace)
```

## The pieces

| Folder | File | What it is |
|--------|------|-----------|
| `research/` | `prompt.md` | Instructions the weekly Claude run follows to draft 15+ items |
| `data/` | `digest.json` | Full working store (pending + published + rejected). **Private — never published.** |
| `data/` | `published.json` | Approved-only export. This is what goes live. |
| `admin/` | `admin.html` | Your local review tool: approve / amend / delete |
| `frontend/` | `digest.html` | The student-facing page embedded in Squarespace |

## Weekly flow

1. **Saturday night** — a scheduled Claude cloud run executes `research/prompt.md`, searches the
   week's news, and appends 15+ `pending` items to `data/digest.json`.
2. **You review** — open `admin/admin.html` in Chrome, click *Open digest.json*, edit anything,
   **Approve** the keepers, **Save to file**, then **Export published.json**.
3. **Publish** — the exported `published.json` is pushed to the GitHub host.
4. **Students** — the Squarespace embed fetches `published.json` and renders the digest,
   filterable by week and practice area. Nothing appears until you approve it.

## To preview right now

Double-click `frontend/digest.html` — it renders with sample data so you can judge the design.
(Standalone it uses inlined fallback data; in production it fetches `published.json`.)

## Setup still to do (needs you)

- [ ] Create a free GitHub account + repo to host `published.json` (publishing target).
- [ ] Confirm the Claude plan supports scheduled cloud agents, then wire up the Saturday routine.
- [ ] Drop the `frontend/digest.html` markup into a Squarespace Code Block and point
      `PUBLISHED_URL` at the GitHub URL.

## Design

Matched to the Vacation Scheme Academy lessons: monochrome palette, **Inter** + **Playfair
Display**, generous white space, editorial cards. See `frontend/digest.html` `:root` tokens.
