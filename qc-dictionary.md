# Quality Criteria: Domain Dictionary

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-DICT-001 |
| CrossReference | [QC-DM-001], [QC-OC-001], [QC-DCD-001] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-02 | Accepted | Jens Tirsvad Nielsen | S07 | Initial version | — |

---

## Purpose

The Domain Dictionary keeps the Product Owner's terms and the professional IT terms apart on purpose. Its quality determines whether the Domain Model stays in the business language while the Operation Contracts, Sequence Diagrams, Design Class Diagrams and ERDs stay in precise IT terms, without the two drifting.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Every row has a PO term, its language, an IT term and a definition | Mandatory | Functional Suitability | An incomplete row cannot be applied consistently |
| 2 | Each PO term maps to exactly one IT term and the reverse (no synonyms) | Mandatory | Maintainability | Synonyms are how the two vocabularies drift |
| 3 | Every Domain Model concept has a row, and the Domain Model uses its PO term | Mandatory | Functional Suitability, Usability | Checks the Domain Model against the dictionary |
| 4 | The Operation Contracts, Sequence Diagrams, Design Class Diagrams and ERD use the IT term, not the PO term | Mandatory | Maintainability | A PO term in design artifacts is a defect |
| 5 | Definitions are written in the PO language and are one sentence | Optional | Usability | |
| 6 | "Used as PO term in" and "Used as IT term in" name artifact types that exist in the project | Optional | Maintainability | |
| 7 | Translated artifacts (`<artifact>.<language>.md`) use the PO terms of the dictionary | Mandatory | Usability, Maintainability | Applies only when the PO language is not English |

## Common Defects

- A concept in the Domain Model with no dictionary row
- The IT term used in the Domain Model, or the PO term in a design class
- Two PO terms for one IT term
- A definition copied from the IT term in the wrong language

## Traceability Rule

- Backward: Every row traces to a concept in the Domain Model checklist ([QC-DM-001]) or a term in the Business Case
- Forward: Feeds the Operation Contract ([QC-OC-001]) and Design Class Diagram ([QC-DCD-001]) checklists, which must use the IT terms

---

[QC-DM-001]: ./qc-domain-model.md
[QC-OC-001]: ./qc-operation-contract.md
[QC-DCD-001]: ./qc-dcd.md
