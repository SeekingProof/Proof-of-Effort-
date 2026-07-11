# Threat Model and Limitations

**Khepri Humetric Solutions**  ·  Patent Pending

*Proof of Effort (PoE) is a process-based attestation tool, not a detector and not a security guarantee. This document states plainly what PoE is designed to resist, what it does not defend against, and the assumptions its evidence rests on. It is published in the interest of accurate representation: a system whose value rests on evidentiary honesty should be equally explicit about the boundaries of that evidence.*

## Scope

This document describes the threat model for the current release of PoE: the boundaries of what its behavioral evidence can and cannot establish, and the classes of interference it is and is not built to withstand. It is written at the level of capability and boundary, not implementation. It does not describe how any measurement, defense, or scoring mechanism works, and it does not enumerate the metrics on which PoE's assessments are based; those remain undisclosed by design.

PoE produces a measurement of how closely a composition session's behavioral record aligns with population-level patterns of authentic human writing. It does not determine who wrote a document, does not establish authorship, and does not issue a verdict. The output is evidence to be interpreted by a person.

## What PoE is designed to resist

**Externally sourced text.** Content pasted or imported from outside the document, and pre-existing or template text, is recorded as unverified, because no composition behavior produced it within the session. PoE attests only to what it observed being written.

**Transcription of external text.** When a writer retypes already-formulated content rather than composing it, the behavioral record differs from authentic composition. PoE examines the document in sections and flags passages whose pattern is consistent with reproduction. Because the assessment reads the process rather than the product, the quality of the reproduced text does not change the signal.

**Browser-based spoofing tools.** PoE operates inside the local word processor. Tools that manipulate behavioral signals at the browser layer do not reach a local word-processing process and are outside PoE's operating environment.

**Artifact tampering.** A sealed artifact's integrity can be confirmed independently. Modification of a sealed artifact is detectable at verification.

**Re-identification.** PoE retains no biometric template and no identifying profile. Its transformations are one-way; the behavioral record cannot be reconstructed into a means of identifying an individual across documents.

**Synthetic or non-human input, as a scoring matter rather than a block.** PoE does not block synthetic input — it declines to reward it. PoE rewards typicality of authentic human composition across multiple independent dimensions. Input that departs from population-level norms scores poorly — surfacing to the writer as low cognitive engagement, transcription flags, or a flat or concentrated cognitive waveform on the scoring page. These are the writer-facing outputs, not the underlying signals; the discriminating metrics are neither disclosed nor visible. In testing, these multi-dimensional patterns proved extremely difficult to emulate — in part because an adversary cannot optimize against measurements they cannot observe.

## Injection: a three-layer posture

PoE never blocks keystroke injection. Its response depends on the layer:

**Software-layer injection.** PoE does not score through injected input. On detecting software injection, it halts capture entirely and notifies the writer to shut down the injecting process and restart the word processor. No attestation is produced from a session in which this occurs.

**Driver-layer or hardware-layer injection.** The current release does not address injection at the driver or hardware layer. A future release is planned to add a higher-security option that documents the presence of trusted keyboard devices. Until then, PoE makes no claim to detect or resist injection below the software layer, and this is a stated limitation.

**Always-on.** Independent of the above, the scoring model rewards authentic-composition typicality (see previous section), so input that does not resemble genuine human composition does not earn a strong result regardless of how it was introduced.

## Intended use and writing types

PoE is designed for **high-stakes prose.** Its assessment documents the typicality of the composition process against population-level norms, and it is most reliable for the extended prose composition for which those norms are well characterized.

It cannot document every kind of writing. Because PoE measures typicality, writing whose authentic process is atypical by nature falls outside what it can assess with certainty. **Creative writing is too broad a class to establish universal certainty at this time** — a writer composing a concrete poem, for example, will likely exhibit an atypical input pattern, and PoE documents typicality rather than accounting for every genre and style.

**Journaling, low-stakes work, very short documents, and stream-of-consciousness text** are outside PoE's design target. Results in these cases should be treated with lower certainty, or may not be produced at all.

## Length thresholds

PoE's certainty depends on document length:

- **Below approximately 400 words:** PoE does not return a reliable cognitive result.
- **Between approximately 400 and 600 words:** PoE can reliably determine whether a document was composed through typical human input patterns, but does not produce transcription analysis.
- **Approximately 600 words and above:** PoE produces both the composition assessment and transcription analysis. Six hundred words is the data threshold below which transcription results are not reported.

## Writer diversity and fairness

**Language background.** PoE does not read content and does not compare a writer's process against any language baseline. A writer's native language does not affect the assessment; the measure is language-independent.

**Neurodivergent writers and writers with motor differences.** Because PoE assesses composition against population-level patterns, any group whose authentic process differs from those patterns is a fairness consideration inherent to the approach. Preliminary samples from neurodivergent writers show no significant deviation from population norms. Validation across neurodivergent writers and writers with motor differences is ongoing.

## What PoE does not defend against or establish

**Authorship or identity.** PoE is not an authentication system. It does not verify who composed a document.

**The origin of ideas.** PoE measures the compositional process, not where the content came from. It does not establish whether a writer received assistance of any kind, including from AI, in forming the ideas they then composed.

**Dictation and voice-to-text.** Dictated text produces no physical-composition signal and cannot be verified as composed. Support is under consideration for future releases.

**Assistive text tools.** Heavy autocomplete and phrase- or sentence-level suggestion tools introduce text the writer did not physically produce, which can lower the measured signal or read as unverified. PoE does not prohibit these tools; it documents only what physically occurred, and their use is the writer's to disclose.

**A determined, resourced adversary.** PoE raises the cost of fabricating an authentic-looking record substantially — in testing, prohibitively — but it does not claim this is impossible. Its purpose is to make authentic composition the path of least resistance and fabrication expensive and unreliable, not to guarantee that no adversary can ever succeed.

## Residual risk and disclosed assumptions

PoE's evidence rests on stated assumptions, and those assumptions define its residual risk:

- PoE attests behavior it observed within a session; it cannot speak to anything outside that window.
- A high score reflects behavioral consistency with authentic composition, not proof of authorship, originality, or merit.
- The always-on scoring defense is empirical: it reflects what was observed to be difficult to emulate in testing, not a mathematical impossibility proof.
- Driver- and hardware-layer integrity is not established in the current release.
- **Writer-controlled capture.** Session capture is under the writer's control by design. If a writer closes a document without saving, the captured session data can be discarded. This is a deliberate open door — the writer, not the system, decides whether a session becomes a record.

PoE is one input to human judgment. It provides a specific, bounded category of evidence — behavioral process attestation — that complements rather than replaces existing academic and professional integrity processes.

---

*Khepri Humetric Solutions  ·  Patent Pending*
