# Quality Criteria: C# Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-CS-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

C# code carries the design into a managed runtime where naming, nullability, disposal and async usage decide whether it stays maintainable and correct. This checklist confirms that C# code follows the C# coding conventions (Microsoft naming and design guidelines), so that it is consistent with .NET practice and with the design it implements.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Types, methods, properties and constants are `PascalCase`; parameters and locals `camelCase`; private fields `_camelCase`; interfaces start with `I` | Mandatory | Maintainability, Usability | |
| 2 | Async methods end in `Async`; exceptions end in `Exception`; one top-level type per file, named after the file | Mandatory | Maintainability, Usability | |
| 3 | Code is formatted per the project's `.editorconfig` and builds with no unexplained analyzer suppressions | Mandatory | Maintainability | |
| 4 | Nullable reference types are enabled; the null-forgiving operator (`!`) is justified in a comment | Mandatory | Reliability | |
| 5 | `IDisposable` objects are disposed with `using`; no resource leaks on exception paths | Mandatory | Reliability, Performance Efficiency | |
| 6 | Async code uses `await` throughout: no `.Result` or `.Wait()` and no `async void` outside event handlers | Mandatory | Reliability, Performance Efficiency | |
| 7 | Specific exceptions are thrown; arguments are validated at public boundaries; rethrow uses `throw;`; no empty `catch` | Mandatory | Reliability, Security | |
| 8 | Public types and members have XML documentation comments | Optional | Usability, Maintainability | |
| 9 | State is exposed through properties, not public fields; immutability (`readonly`, `init`, `record`) is preferred where it fits | Optional | Maintainability, Reliability | |
| 10 | Money uses `decimal`; points in time use `DateTimeOffset` | Mandatory | Functional Suitability, Reliability | |
| 11 | Public async APIs accept and pass a `CancellationToken` where the operation can be cancelled | Optional | Performance Efficiency, Reliability | |
| 12 | Tests cover new behaviour, are named `Method_Condition_Expected`, and do not depend on order, time or the network | Mandatory | Reliability, Maintainability | |
| 13 | Classes and members trace to the Design Class Diagram they implement; deviations are recorded | Mandatory | Functional Suitability, Maintainability | |

## Common Defects

- camelCase methods or snake_case members carried over from another language
- Nullable warnings silenced with `!` or pragmas
- `Task.Result` or `.Wait()` on the request path (deadlocks and thread starvation)
- `throw ex;` destroying the stack trace; empty `catch` blocks
- Undisposed `HttpClient`, streams or database connections
- `DateTime` used for instants, or `double` for money
- Several public types in one file, or a file name that differs from its type

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the classes and members being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ./qc-dcd.md
[QC-ADR-001]: ./qc-adr.md
