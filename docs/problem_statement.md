# Problem Statement: Court Decision Summarizer

## 1. Context

Lawyers and legal staff routinely work with court decision texts: they prepare short briefs for internal reports, handoffs to colleagues, positioning on similar matters, or client responses. Decision texts are often long; a significant share of time goes into extracting claims, facts, and outcomes in the structure their organization expects.

## 2. Current state (as-is)

Today, processing **one case** (one court decision → structured summary in the accepted format) is done **manually**:

| Parameter | Observed value |
|-----------|----------------|
| Typical time per case | **5 to 10 minutes** |
| Complex cases | **up to 20 minutes** |
| Additional effort | In some cases, **consulting legislation** is required (checking norms, aligning reasoning with current versions of statutes), which increases duration and interrupts workflow |

Manual work includes:

- reading the full decision text;
- mentally or in writing marking sections (claim, circumstances, holding, etc.—depending on the team template);
- drafting a concise summary without unnecessary procedural filler;
- when needed—revisions after internal review or follow-up questions to colleagues.

There is no shared team standard for summaries, or it is implemented inconsistently (Word templates, copy-paste, personal notes). Summary quality and structure depend on the individual and their workload.

## 3. Problem

**High repeatable effort** at scale: even at 5–10 minutes per document, total cost grows linearly; at 20 minutes on a complex case plus time on legislation, cost grows **non-linearly**, with risk of a bottleneck in legal operations.

**Inconsistent format:** without fixed generation rules, each lawyer shortens text differently, which makes comparing matters, handing off cases, and quality control harder.

**No single place for interactive refinement:** edits and clarifications often happen outside the primary tool (email, separate files), breaking the link between the source decision, the summary, and revision history.

**Confidentiality:** decision texts and summaries are sensitive; using cloud services without control over data location blocks adoption of generic LLM tools.

## 4. Target state

A lawyer should be able to:

1. Paste court decision text into a **local application** on their own computer.
2. Receive a **structured summary** using configurable blocks (claim, circumstances, holding, etc.) in **substantially less time** than the typical 5–10 minutes of manual work.
3. Refine or correct the summary in a **dialog** with the system, edit text manually, or apply phrase **templates**.
4. Return to recent cases from **history** without re-reading the decision from scratch.
5. Avoid sending data to third parties except an explicitly configured LLM endpoint (with local or corporate model deployment—no external transfer).

Consulting legislation remains the **lawyer’s responsibility**; the MVP does not replace legal judgment or guarantee that norms are up to date, but it reduces time spent on **initial structuring** of the decision, freeing time for statutory analysis where it is actually needed.

## 5. Proposed solution (MVP)

**Court Decision Summarizer** — a local web application with an LLM:

- initial check that input is sufficient (so summaries are not built on incomplete text);
- summary generation using configurable **blocks** and instructions;
- dialog-based refinement that respects manual edits;
- templates, case history, and statistics on tokens and processing time;
- model and LLM connection changes via configuration without rewriting case logic.

Full requirements: [technical_specification.md](technical_specification.md).

## 6. Expected impact (hypotheses to validate after rollout)

| Metric | Baseline (today) | MVP target (guidance) |
|--------|------------------|------------------------|
| Time to draft summary | 5–10 min (typical), up to 20 min (complex) | Measure after pilot; aim for **at least 50% reduction** on typical cases |
| Structure consistency | Depends on individual | Summary always uses the configured number and order of blocks |
| Reopening a case | Re-read the decision | Restore from history + dialog |
| Data | Scattered files / chats | Local storage on the user’s PC |

For summary quality criteria and evaluation methodology, see [evaluation.md](evaluation.md) (when populated).

## 7. Constraints and assumptions

- MVP targets **pasted decision text** (no OCR/PDF in the first version).
- **Legal accuracy** of the summary remains the lawyer’s responsibility; the system is an assistive tool.
- Citations to law and legislative checks are **out of scope** for the MVP; when needed, the lawyer does this outside the app, using the prepared summary.
- Summary language matches case language; dialog language follows the user’s language in chat (see technical spec §1.5).

## 8. Related documents

| Document | Purpose |
|----------|---------|
| [technical_specification.md](technical_specification.md) | Full MVP technical specification |
| [evaluation.md](evaluation.md) | Quality evaluation methodology |
| [prompt_engineering.md](prompt_engineering.md) | Prompts and versions |
| [../README.md](../README.md) | Repository overview |
