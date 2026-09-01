# SECR S&T Knowledge Portal — Walkthrough

A visual walkthrough of the Phase-1 pilot of an AI knowledge portal built for
**South East Central Railway, S&T (Telecom)** — a grounded retrieval system over
the Indian Railways signalling and telecommunication manuals, where every answer
is cited to its exact clause and the engine returns *"not found"* rather than
guessing.

check here : https://gh-novel.github.io/secr-st-knowledge-portal/

## What it does

Staff ask a question in plain language. The portal answers **only** from the
indexed manuals, cites the document, clause and page for every claim, and links
each citation to the rendered page of the original manual with the exact lines
highlighted. When the manuals do not contain the answer, it says so instead of
improvising.

| | |
|---|---|
| Passages indexed | 3,239 (clause-level) |
| Retrieval hit@5 | 100% |
| Citation exactness | 97% |
| Uncited claims | 0% |
| Evaluation suite | 221 questions and conversation turns |

Indexed corpus — IRSEM 2021 · Indian Railways Telecom Manual 2021 · Model SOP 2018.

## What the walkthrough covers

| Section | Shows |
|---|---|
| **Grounded answer** | An annotated diagram of a full answer — question, cited response, clause details, citations list |
| **Conversation context** | An elliptical follow-up resolved against earlier turns before retrieval runs |
| **The printed page** | A citation opened onto the real manual page, with the cited lines highlighted |
| **Optional web lookup** | An opt-in web search, fenced and labelled, never mixed into the cited answer |
| **Refusal** | Questions outside the corpus declined rather than answered |
| **Saved answers** | An answer kept together with its full citations |
| **Light and dark** | Dark mode as a full theme, not an inverted filter |
| **In the field** | The same engine and citations on a phone |

## How an answer is built

1. **Rewrite** — elliptical follow-ups resolved into standalone questions using recent turns.
2. **Retrieve** — dense embeddings and BM25 keyword search in parallel, fused, then reranked by a cross-encoder.
3. **Gate** — calibrated thresholds decide answer-or-refuse before any generation cost is spent.
4. **Judge** — a sufficiency check asks whether the passages actually answer the question, not merely share its topic.
5. **Generate & verify** — the draft is checked back against its sources; unsupported sentences are repaired or the answer is discarded.
6. **Cite** — every claim is bound to a clause, a page, and the lines on it.

## About this repository

This repo contains **only the walkthrough page** — a static site of screenshots
and explanatory diagrams. The portal's source code and system architecture are
not published here, under the terms of the engagement.

```
index.html            the walkthrough page
style.css             styling
assets/screens/       screenshots of the running pilot
assets/logo.png       Indian Railways emblem
```

Plain HTML and CSS with no build step and no dependencies — open `index.html`
in a browser to view it.

## Access

Full deployment is in progress. Once live, access will be restricted to South
East Central Railway staff sign-in. This walkthrough is a preview, not a public
tool. The source document remains authoritative; the portal assists retrieval
and does not replace the manual.
