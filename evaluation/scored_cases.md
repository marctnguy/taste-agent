# Taste Agent for Letterboxd — Round 1 Scored Evaluation Cases

## 1. Evaluation Summary

The Round 1 evaluation used eight synthetic input rows representing seven functional tests of the Taste Agent POC.

The cases were processed through the actual n8n workflow rather than evaluated hypothetically.

### Overall Result

| Outcome | Tests |
|---|---:|
| PASS | 6 |
| PARTIAL | 1 |
| FAIL | 0 |
| Total | 7 |

The evaluation successfully validated:

- film metadata matching;
- book metadata matching;
- ambiguous-title resolution using additional metadata;
- rejection of nonexistent works;
- structured semantic output;
- separation of preference data from semantic-classification inputs.

One issue was identified: repeated LLM classification of the same work produced some variation in semantic scores.

---

## 2. Scoring Definitions

Each test receives one of three outcomes:

- **PASS** — expected behaviour was observed.
- **PARTIAL** — the core expected behaviour worked, but an issue requiring further investigation was identified.
- **FAIL** — expected behaviour was not achieved.

The test set is intended as functional POC validation rather than a statistically representative benchmark.

---

## 3. Scored Cases

### E01 — Clear Film Match: Parasite

**Input**

| Field | Value |
|---|---|
| Media type | Film |
| Title | Parasite |
| Year | 2019 |
| Rating | 4.5 / 5 |

**Expected behaviour**

The system should identify the 2019 film through TMDB, obtain usable metadata, pass the quality gate, and generate a valid semantic representation.

**Observed behaviour**

- `tmdb_match_found`: `true`
- `tmdb_match_method`: `title_and_year`
- TMDB title: `Parasite`
- Release date: `2019-05-30`
- `metadata_match_found`: `true`
- `has_description`: `true`
- `ready_for_ai`: `true`
- Structured semantic output generated successfully.

**Result: PASS**

The standard film-enrichment and classification path behaved as expected.

---

### E02 — Ambiguous Film Match: Crash

**Input**

| Field | Value |
|---|---|
| Media type | Film |
| Title | Crash |
| Year | 1996 |
| Rating | 3.5 / 5 |

**Expected behaviour**

Because multiple films share the title *Crash*, the system should use the supplied year to resolve the intended 1996 film rather than selecting another title with the same name.

**Observed behaviour**

- `tmdb_match_found`: `true`
- `tmdb_match_method`: `title_and_year`
- TMDB ID: `884`
- TMDB title: `Crash`
- Release date: `1996-07-17`
- `metadata_match_found`: `true`
- `ready_for_ai`: `true`
- Structured semantic output generated successfully.

**Result: PASS**

The matcher successfully used title and year to disambiguate the work.

---

### E03 — Invalid Film Rejection

**Input**

| Field | Value |
|---|---|
| Media type | Film |
| Title | The Purple Lighthouse of Saturn |
| Creator | Test Director |
| Year | 2022 |

This title was deliberately fabricated for the evaluation.

**Expected behaviour**

The system should fail to find a reliable TMDB match and prevent the record from being sent to the semantic classifier.

**Observed behaviour**

- `tmdb_match_found`: `false`
- `tmdb_match_method`: `unmatched`
- `tmdb_id`: `null`
- `metadata_match_found`: `false`
- `has_description`: `false`
- `ready_for_ai`: `false`

The record was routed through the negative branch of the metadata quality gate and did not reach the LLM.

**Result: PASS**

The POC failed safely rather than inventing metadata or classifying an unsupported work.

---

### E04 — Book Match: The Bell Jar

**Input**

| Field | Value |
|---|---|
| Media type | Book |
| Title | The Bell Jar |
| Creator | Sylvia Plath |
| Original year supplied | 1963 |
| Rating | 4.5 / 5 |

**Expected behaviour**

The system should identify *The Bell Jar* by Sylvia Plath through Google Books, obtain usable descriptive metadata, and pass the work to semantic classification.

**Observed behaviour**

- `google_books_match_found`: `true`
- `google_books_match_method`: `title_author`
- Google Books title: `The Bell Jar`
- Author: `Sylvia Plath`
- `metadata_match_found`: `true`
- `has_description`: `true`
- `ready_for_ai`: `true`
- Structured semantic output generated successfully.

Google Books returned a 2014 edition rather than the original 1963 publication date. The title and author nevertheless corresponded to the intended work.

**Result: PASS**

The case demonstrates successful book enrichment while also illustrating that edition-level metadata may differ from the user's original publication-year data.

---

### E05 — Invalid Book Rejection

**Input**

| Field | Value |
|---|---|
| Media type | Book |
| Title | The Imaginary Garden of Neptune |
| Creator | Test Author |
| Year | 2018 |

This title and author were deliberately fabricated.

**Expected behaviour**

The system should fail to identify a reliable Google Books match and prevent the record from reaching semantic classification.

**Observed behaviour**

- `google_books_match_found`: `false`
- `google_books_match_method`: `unmatched`
- `google_books_id`: `null`
- `metadata_match_found`: `false`
- `has_description`: `false`
- `ready_for_ai`: `false`

The record was rejected by the metadata quality gate.

**Result: PASS**

The book pipeline failed safely without generating unsupported metadata or semantic scores.

---

### E06 / E07 — Preference Separation and Classification Consistency

E06 and E07 intentionally represent the **same cultural work with opposite preference signals**.

#### Inputs

| Field | E06 | E07 |
|---|---|---|
| Media type | Film | Film |
| Title | Aftersun | Aftersun |
| Year | 2022 | 2022 |
| Rating | 1 / 5 | 5 / 5 |
| Preference class | Negative | Positive |
| Liked | False | True |

**Expected behaviour**

Both records should resolve to the same film and receive the same source metadata.

Because explicit preference signals are deliberately excluded from the semantic classifier input, changing the rating should not systematically alter the semantic interpretation of the work.

The paired case also provides an initial test of repeated-classification consistency.

**Observed metadata behaviour**

Both cases resolved to:

- TMDB ID: `965150`
- TMDB title: `Aftersun`
- Release date: `2022-10-21`
- identical TMDB overview;
- identical genre metadata;
- `metadata_match_found`: `true`;
- `ready_for_ai`: `true`.

The only intentional differences were the user preference fields.

No evidence was observed that the rating, like status, or preference class was passed into the semantic-classification prompt.

#### Semantic Consistency

The two independent LLM calls did not produce completely identical vectors.

Of the **62 semantic dimensions**:

- **49 remained identical**
- **13 differed**
- approximately **79% were identical**

Observed differences were generally one scoring increment (`0.25`).

Examples included:

| Dimension | E06 | E07 |
|---|---:|---:|
| dysfunctional_relationships | 0.75 | 0.50 |
| slow_burn | 1.00 | 0.75 |
| moderate | 0.25 | 0.50 |
| romantic | 0.75 | 0.50 |
| comforting | 0.50 | 0.25 |
| experimental | 0.50 | 0.25 |
| maximalist | 0.25 | 0.00 |
| dialogue_heavy | 0.25 | 0.50 |
| surreal | 0.25 | 0.00 |
| accessible | 0.75 | 0.50 |
| abstract | 0.25 | 0.50 |
| niche | 0.25 | 0.50 |
| contained | 0.50 | 0.75 |

**Result: PARTIAL**

The architectural preference-separation requirement passed: the same work received identical metadata and preference information was not used as semantic-classification input.

However, repeated classification of identical source content showed measurable LLM variance.

There is no evidence in this test that the differences were caused by the changed rating. The more appropriate interpretation is that repeated LLM calls are not fully deterministic.

**Production implication**

Semantic representations should be generated once per canonical work and stored for reuse rather than regenerated separately for every user's interaction with that work.

Round 2 should also evaluate repeated-classification consistency systematically.

---

### E08 — Ambiguous Film/Year Match: The Thing

**Input**

| Field | Value |
|---|---|
| Media type | Film |
| Title | The Thing |
| Creator | John Carpenter |
| Year | 1982 |
| Rating | 4 / 5 |

**Expected behaviour**

The system should use the supplied title and year to identify the intended 1982 film rather than another work with the same or similar title.

**Observed behaviour**

- `tmdb_match_found`: `true`
- `tmdb_match_method`: `title_and_year`
- TMDB ID: `1091`
- TMDB title: `The Thing`
- Release date: `1982-06-25`
- `metadata_match_found`: `true`
- `ready_for_ai`: `true`
- Structured semantic output generated successfully.

**Result: PASS**

The film matcher correctly resolved the intended work.

---

## 4. Criteria-Level Results

| Evaluation Criterion | Result | Evidence |
|---|---|---|
| Metadata matching | PASS | Valid films and books resolved correctly |
| Safe rejection | PASS | Both fabricated works were rejected before AI classification |
| Schema compliance | PASS | All six classified records returned the required structured semantic taxonomy |
| Semantic plausibility | PASS | Manual review found no major contradictory or unsupported classification |
| Preference separation | PASS | Rating and like signals were kept outside semantic-classification inputs |
| Repeated classification consistency | PARTIAL | 13/62 dimensions differed for repeated classification of *Aftersun* |

---

## 5. Issues Identified

### 5.1 Repeated LLM Classification Variance

The primary issue discovered during evaluation was semantic variance between repeated classifications of identical source content.

This does not prevent the POC from constructing a Taste Model, but repeatedly generating semantic vectors for the same cultural work could introduce unnecessary inconsistency between users or over time.

**Round 2 response:**

- classify canonical works once;
- persist semantic vectors;
- reuse stored representations;
- test repeated classifications across a larger evaluation set;
- investigate model and configuration choices that improve consistency.

---

### 5.2 Book Edition Metadata

The Google Books result for *The Bell Jar* corresponded to the intended title and author but returned a 2014 edition rather than the original 1963 publication date.

This highlights a distinction between:

- identifying the correct **work**; and
- identifying the exact **edition**.

For the Taste Agent use case, work-level semantic classification is currently the primary requirement.

Production implementation should nevertheless preserve source publication data separately where edition accuracy matters.

---

## 6. Round 1 Evaluation Conclusion

The evaluation supports the technical feasibility of the core Round 1 pipeline.

The POC successfully demonstrated:

- cross-media routing between film and book records;
- external metadata enrichment;
- title/year and title/author matching;
- safe rejection when metadata could not be validated;
- strict structured semantic classification;
- separation between content classification and explicit user preference signals.

The evaluation also identified a concrete limitation rather than treating the POC as production-ready: repeated LLM classification can introduce variation into semantic vectors.

This leads to a clear architectural recommendation for the MVP:

> **Classify each canonical cultural work once, store its semantic representation, and reuse that representation when constructing user Taste Models.**

The Round 1 evaluation therefore supports proceeding to the next stage of the project while moving the evaluation focus from **"Can the system construct the representation?"** to:

> **"Does the representation produce better film recommendations?"**

That question will be evaluated in Round 2 through recommendation benchmarking, cross-media ablation testing, and LangSmith-based evaluation.
