# Proof-of-Effort-
Proof of Effort is a Non-Biometric method for extracting, analyzing and packaging cognitive signals left by a writer as they compose text.
# Proof of Effort (PoE)

**Khepri Humetric Solutions** — [seekingproof.com](https://seekingproof.com)

*A non-biometric behavioral attestation tool for written composition.*

**Status:** Beta · Patent pending

---

## Overview

PoE helps writers, educators, and anyone who needs to demonstrate that a
document was genuinely composed by a person. It runs as an extension in popular
word processors such as **LibreOffice** and **Microsoft Word**, with coding
software solutions in development. While you write, it records content-free
metadata about the composition process. This data resides as metadata **within
the document itself**; a user may optionally seal it into a portable artifact.

PoE is a **measurement tool, not a detector.** It does not render a verdict on
whether text is "AI" or "human." It measures characteristics of the composition
process, compares them to population baselines, and reports them as graded data,
so the evidence — not an opinion — travels with the work.

## What PoE records — and what it discards

- **Retained** (as content-free metadata): coarse timing and editing metadata
  describing *how* the document was composed.
- **Discarded:** semantic content (the words you write) and precise
  inter-keystroke timing exist only transiently in running memory. They are
  discarded from memory, **never stored, never transmitted, and are not part of
  the final analysis.**
- **Never created:** no biometric template, no identity fingerprint, no means of
  recognizing an individual across documents.

PoE measures the process of writing without retaining what you wrote and without
learning who you are.

## The artifact

- **Stored in-document by default:** PoE data is written as metadata within the
  document itself — **fully portable and lightweight**, travelling with the file
  wherever it goes.
- **Sealed artifact (optional):** a user may choose to generate a sealed
  artifact — a single portable file, cryptographically sealed at the moment of
  creation, carrying the **NEOHE** score and the telemetry it was derived from
  (see *Definitions*).
- **Independently verifiable:** an artifact's integrity can be confirmed offline,
  using the PoE client — **no account, no live Khepri involvement required.**
  (Generating a *new* score requires the scoring service; confirming an existing
  artifact's integrity does not.)

## What it can show

PoE attributes editing activity to positions across the whole document, not only
at the leading edge where typing is currently happening — giving a fuller
picture of how a piece was built.

## Privacy

Semantic content and precise inter-keystroke timing **never leave your
computer** — and are never stored, nor are they part of the final analysis. The
behavioral metadata PoE does use is content-free by design and carries no
biometric identifier. A plain-language Privacy Statement and the full Privacy
Policy are available on the site.

## Definitions

- **NEOHE — Non-biometric Evidence of Human Effort** (pronounced *NEE-O*): a
  measurement, on a 0.0–1.0 scale, of the degree to which a composition
  session's behavioral record is consistent with population-level reference
  patterns of authentic human composition. It is a measurement, not a verdict —
  not a determination of authorship and not a human-vs-AI judgment.
- **TDP — Temporal Density Profile:** a time-ordered representation of a
  composition session showing where and how compositional effort was distributed
  across it. It is the intermediate representation from which the NEOHE score is
  computed, and it preserves the shape of the writing process while discarding
  both the words written and any timing precise enough to identify an individual.

## Documentation

Full documentation lives at **[seekingproof.com](https://seekingproof.com)**:

- User Guide
- Installation & System Requirements
- Troubleshooting
- FAQ
- Research Foundations
- Security Whitepaper
- Privacy Statement
- Threat Model & Limitations
- Privacy Policy · Terms of Service
- Changelog

## Contact

- <info@kheprisol.com>

## Legal

PoE and the Proof of Effort method are patent pending.
© 2026 Khepri Humetric Solutions. All rights reserved.

<!-- repository license line to be decided -->
