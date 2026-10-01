# Quality Criteria: C Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-CL-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

C gives no safety net: memory, bounds and error handling are the programmer's job. This checklist confirms that C code follows the C coding conventions (naming with module prefixes, explicit ownership, checked errors), so that it is maintainable and free of the defects that cause crashes and vulnerabilities.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Functions and variables are `snake_case`; public symbols carry the module prefix; macros and enum constants are `UPPER_SNAKE` | Mandatory | Maintainability, Compatibility | |
| 2 | No reserved identifiers (leading underscore plus uppercase, double underscore) | Mandatory | Portability, Reliability | |
| 3 | Code compiles cleanly with the project's warning flags and the declared C standard | Mandatory | Reliability, Portability | |
| 4 | Code is produced by the project's formatter; braces are used on every control-flow body | Mandatory | Maintainability | |
| 5 | Every return value that can fail, including allocation, is checked | Mandatory | Reliability | |
| 6 | Every acquired resource (memory, file, lock) has one owner and is released on every exit path | Mandatory | Reliability, Performance Efficiency | |
| 7 | Every buffer is passed with its length; bounded functions (`snprintf`) are used, never `gets`, `sprintf` or `strcpy` | Mandatory | Security, Reliability | |
| 8 | No undefined behaviour: no signed overflow, use after free, out-of-bounds access or uninitialised reads | Mandatory | Reliability, Security | |
| 9 | Headers are self-contained, guarded, and expose only what callers need; internals are `static` | Mandatory | Maintainability, Compatibility | |
| 10 | Mutable global state is avoided, or is `static` and documented | Optional | Maintainability, Reliability | |
| 11 | Error reporting (status codes, `errno` use) is documented in the header | Optional | Usability, Reliability | |
| 12 | Tests cover new behaviour and run under address and undefined-behaviour sanitizers in at least one build | Optional | Reliability, Security | |
| 13 | Modules and functions trace to the Design Class Diagram or design artifact they implement | Mandatory | Functional Suitability, Maintainability | |

## Common Defects

- Unchecked `malloc` or `fopen` results
- Missing `free` or `close` on an early-return or error path
- Buffer sized without a length parameter; `strcpy` or `sprintf` on external input
- Public function or type without the module prefix, colliding across modules
- Macros doing the work of `static inline` functions or `enum`
- Identifiers starting with an underscore and an uppercase letter
- Undefined behaviour hidden by a build that happens to work

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the modules and operations being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ./qc-dcd.md
[QC-ADR-001]: ./qc-adr.md
