# Security Overview

**Khepri Humetric Solutions**  ·  Patent Pending

*This document explains, at a conceptual level, how a Proof of Effort (PoE) artifact establishes trust: what it is, how its integrity is protected, what survives without Khepri, and what PoE never collects. It is a companion to the [Threat Model and Limitations](THREAT_MODEL.md), which states what PoE can and cannot withstand, and to the [Research Foundations](RESEARCH_FOUNDATIONS.md), which establishes the science. This document describes properties and capabilities, not implementation; it does not disclose the scoring methodology, the internal artifact structure, or the metrics on which assessments are based.*

## The trust question

PoE exists to answer a narrow question: can a writer produce durable, checkable evidence that a document was genuinely composed by a person? A useful answer has to be trustworthy in a specific sense — the evidence must be tamper-evident, it must not expose the writer, and confirming it must not depend on trusting the vendor's word. This document describes how PoE is built to meet those three requirements.

## What the artifact is

When a writer scores a document, PoE produces an attestation record. By default this record lives as metadata inside the document itself, travelling with the file; a writer may also seal it into a separate, self-contained artifact file. Either way, the record carries three things: the behavioral evidence of the composition session, the NEOHE score derived from that evidence, and a cryptographic integrity seal. The score is sealed *into* the record alongside the telemetry it came from — it is part of the artifact, not a value kept elsewhere.

Two properties of the record matter for trust. First, it is **content-free**: it contains no document text. Second, it is **non-identifying**: it contains no biometric template and no material from which an individual could be recognized. Because the record holds neither the words written nor anything that identifies the writer, there is little in it to expose even in the event of disclosure — a property that distinguishes process-attestation evidence from systems that retain document text or identity data.

## Integrity and tamper-evidence

The artifact is cryptographically sealed using established, industry-standard primitives — specifically, AES-256 encryption with HMAC-based integrity protection. These are widely used, well-understood constructions that any qualified party can recognize and audit, not a proprietary or home-grown scheme. The seal makes the record **tamper-evident**: modification, reordering, or splicing of the sealed session data is detectable when the artifact is checked. A one-way fingerprint binds the proof to the specific document it attests to, linking the two without storing the document's text.

We describe this as tamper-*evident* rather than tamper-*proof* deliberately. The guarantee is detection, not impossibility: an altered artifact does not silently pass as genuine — it fails verification. That is the property a recipient actually needs.

## What survives without Khepri — and what requires it

This boundary is worth stating precisely, because it is easy to get wrong in both directions.

**The artifact is self-contained, and the score travels inside it.** The NEOHE score is sealed into the artifact itself, alongside the behavioral telemetry it was derived from — it is not a value that exists only on Khepri's servers. If Khepri's infrastructure were unavailable, the attested score remains present in, and recoverable from, the artifact, and its integrity remains independently verifiable. A recipient can confirm that the artifact is structurally intact, that its sealed contents — including the score — have not been altered since generation, and that its seal is valid, without contacting Khepri and regardless of whether Khepri is still operating. The evidence, and its result, do not evaporate if the vendor does.

**Producing a score, however, requires Khepri.** Scoring a document for the first time, and re-running the scoring engine to compute a score from telemetry, both take place in Khepri's infrastructure. The scoring methodology is not carried in the client or the artifact, so an independent party cannot re-run it offline. The honest distinction is between *recovering and verifying the score already sealed into an artifact* — which is offline and vendor-independent — and *generating a score in the first place*, which is not.

## Why scoring runs on the server

Scoring happens in Khepri's infrastructure rather than on the writer's device, for two reasons that both serve the user. It keeps the analytical methodology off the device, where it cannot be extracted, inspected, and reverse-engineered by someone trying to defeat it — which directly protects the integrity of everyone's scores. And it ensures every session is assessed against the same population-level reference, so results are consistent rather than dependent on a local copy that could drift or be tampered with.

## Measurement, not injection resistance

It is worth being precise about what PoE does and does not do here, because the distinction is easy to blur.

PoE does not resist injection. It has no knowledge of whether input arrives from a keyboard, a software process, or a hardware device, and it has no knowledge of the user's intent in using any such tool. PoE measures one thing: how closely the telemetry of a session resembles population-level patterns of authentic human composition. Whether a given tool was used, and why, is outside what PoE observes or judges.

What follows from accurate measurement is a byproduct, not a designed defense. Because any injector — software or hardware — must generate its input algorithmically, and because algorithmically generated input tends to be atypical against human baselines, such input generally scores poorly. This is not PoE detecting or blocking the injector; it is PoE measuring input that happens not to resemble human composition. The resistance is to a *deceptive outcome* — input offered as authentic human effort that was not — and only insofar as that input fails the measurement. A person using an injector for legitimate reasons is neither flagged nor judged; PoE is not adjudicating tools or motives.

The practical consequence for the honest reader: PoE's value against deceptive automation is not that it stops automation, but that automated input has to survive the same measurement as everything else, and — in testing — mechanical input does not do so convincingly. Injection PoE cannot see at the point of capture is not thereby laundered into a good score; it still faces a typicality measurement it cannot observe. PoE's injection posture and its limits are detailed in the [Threat Model and Limitations](THREAT_MODEL.md).

## What PoE never collects or retains

The security of a system is only as good as the sensitivity of what it holds. PoE is built to hold as little as possible:

- **No document content.** The words a writer types are never stored and never transmitted, and are not part of the analysis. Only content-free behavioral metadata is used.
- **No precise keystroke timing.** The fine-grained inter-keystroke timing that can identify individuals exists only transiently in memory during a session and is discarded; it is never stored, never transmitted, and not part of the final analysis. What remains are coarse, aggregate characteristics from which individual keystrokes cannot be reconstructed.
- **No biometric template and no enrollment.** PoE builds no per-person profile and requires no prior sample. There is no stored identity to breach, and nothing that recognizes a writer across documents.
- **No device binding.** The artifact is owned by the writer and carried in their document, not held in a vendor database keyed to a person or machine.

Because these things are never captured or retained, they cannot be leaked, subpoenaed, or misused — the strongest form of data protection is not holding the data at all.

## What this document does not claim

PoE is a beta product and a bounded evidence tool. This overview describes tamper-evidence, content-freeness, vendor-independent integrity checking, and a measurement that atypical input does not readily pass — not perfect or unbreakable security, and not a guarantee against every adversary. The limits of PoE's evidence, and the threats it does and does not defend against, are stated plainly in the [Threat Model and Limitations](THREAT_MODEL.md). PoE is one input to human judgment, not a security product that resolves questions on its own.

---

*Khepri Humetric Solutions  ·  Patent Pending*
