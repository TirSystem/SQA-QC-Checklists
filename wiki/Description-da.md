# Beskrivelse

🌐 [English](Description) · **Dansk** · [Bahasa Melayu](Description-ms)

## Hvad en tjekliste indeholder

Hver `qc-<type>.md` har samme form:

| Afsnit | Indhold |
| --- | --- |
| `## Metadata` | `ID` (fx `QC-US-001`), `CrossReference` til relaterede tjeklister, `DomainLanguages` |
| `## Version History` | Dato, status, forfatter, reviewer, ændring |
| `## Purpose` | Hvorfor artefakttypen findes, og hvad tjeklisten beskytter |
| `## Quality Criteria Checklist` | Den nummererede kriterietabel |
| `## Common Defects` | De fejl, reviewere faktisk finder |
| `## Traceability Rule` | Hvad artefaktet skal spore *tilbage* til og *frem* til |

## Kriterietabellen

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 2 | Written in "As a / I want / So that" form | Mandatory | Usability | |

- **Mandatory**: grundniveauet, hver instans skal opfylde.
- **Optional**: avanceret; kan udskydes med en begrundelse.
- **ISO/IEC 25010-egenskab**: hvilken produktkvalitetsegenskab kriteriet
  beskytter (Functional Suitability, Reliability, Usability, Maintainability,
  Security, Compatibility, ...). Den lader en reviewer se, *hvilken slags*
  kvalitet et ikke-bestået kriterium bringer i fare, ikke blot at det fejlede.

## ID'er og versioner

- En tjeklistes ID er `QC-` plus kortkoden for den artefakttype, den dækker: `QC-BC-001`, `QC-UC-001`, `QC-ERD-001`.
- Versionen er uafhængig af ethvert reviewet dokument og stiger kun, når selve tjeklisten revideres.
- Tjeklisten `qc-language-domain.md` (`QC-LANG-001`) er **tværgående**: den gælder ud over typens egen tjekliste for ethvert dokument skrevet på Product Ownerens sprog.

## Sporbarhed

Tjeklister henviser til hinanden. *Traceability Rule* i en user story-tjekliste
peger tilbage på tjeklisterne for use case-diagram, use case og business case og
frem mod accepttests. En reviewer bruger det til at sikre, at et dokument ikke
svæver frit af de dokumenter, det afhænger af.

## Et review, trin for trin

1. Vælg tjeklisten for artefakttypen (plus `QC-LANG-001`, hvis sproget er relevant).
2. For hvert kriterium: notér `Pass`, `Fail` eller `N-A` med dokumentation.
3. Giv en dom: **Go**, **Go-with-conditions** eller **No-Go**.
4. Ret eller begrund hvert ikke-bestået kriterium, og re-review derefter delta'et.
5. Reviewer er aldrig forfatteren.

Postformatet (en `RC-*`-reviewpost) er defineret af
[frameworket](https://git.tirsystem.com/TirSystem/sqa-qc-framework); uden for
frameworket duer enhver tabel med de samme kolonner.

## Tjeklister for kildekode

`qc-programming-*`-tjeklisterne forudsætter, at dit team har skrevet sine
kodekonventioner ned for sproget. De kontrollerer, at koden **følger dem**; de
pålægger ikke en egen stil.

## Licens

CC BY-SA 4.0. Del og tilpas, også kommercielt, hvis du krediterer TirSystem og
udgiver din tilpasning under samme licens.
