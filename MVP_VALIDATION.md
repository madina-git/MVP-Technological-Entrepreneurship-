# DepSentry MVP — Assignment Criteria and Validation Plan

**Course:** Technology Entrepreneurship  
**Group:** CS-2406  
**Members:** Isak Madina, Tolganay Syrym, Madina Zhunis

## 1. MVP level selected

**Selected: functional web-service MVP.** It is stronger than a visual mock-up because users can upload a dependency file, run a real check against OSV.dev, view findings, and export a report. In the assignment's maturity scale, this is closest to an **Advanced MVP** (a working product that users can try), while the implementation remains deliberately limited in scope. It is not a production SaaS because authentication and cloud storage are not implemented.

## 2. Criteria checklist

| Assignment criterion | DepSentry implementation | Status / evidence |
|---|---|---|
| Step 1 — identify the problem | Small teams struggle with complex dependency-security reports and lack clear upgrade guidance. | Addressed by readable findings and next-action guidance. |
| Step 2 — identify and narrow the audience | CS/software students, freelancers, and small development teams without dedicated security specialists. | Addressed in README and interface copy. |
| Step 3 — analyse competitors | Existing alternatives include npm audit, GitHub Dependabot, and OWASP Dependency-Check. DepSentry focuses on a simple browser flow and a clear report. | Based on prior project research; not a claim that competitors lack vulnerability detection. |
| Step 4 — SWOT | Strength: low setup friction and readable output. Weakness: no backend/auth and OSV coverage limits. Opportunity: student/small-team use and shareable reports. Threat: established free tools and user privacy concerns. | Included here as a concise MVP-level SWOT. |
| Step 5 — user path map | Open app → upload/paste manifest → parse exact versions → query OSV.dev → review severity/fix/advisory → export report → revisit local history. | Implemented in the interface; see README. |
| Step 6 — prioritised feature list | P0: upload/paste supported manifests, live vulnerability lookup, results, export. P1: local history and dashboard. P2/future: secure accounts, cloud history, teams, billing, API/CLI, compatibility-risk analysis. | P0/P1 included; P2 clearly outside MVP scope. |
| Step 7 — define MVP scope | Browser-only UI, up to 150 exact-version dependencies, live OSV.dev checks, readable findings, JSON/PDF export, local report history. No source-code upload. | Scope is explicit and bounded. |
| Step 8 — development/management method | Build–Measure–Learn / iterative prototype development. Validate the riskiest assumptions before adding features. | Appropriate for a student MVP; use the test plan below. |
| Step 9 — alpha and beta testing | Alpha checklist is provided below. Beta testing requires real participants and recorded observations. | **Pending execution** — do not report test results until tests have actually been run. |
| Working MVP / user can try it | The scan runs against the public OSV.dev API, and reports are generated from live API results. | Implemented in code; verify with the smoke-test steps before presentation. |

## 3. Hypotheses and HADI cycle

The CustDev survey included 24 respondents. It reported that 70.8% found reports difficult to understand, 45.8% were overwhelmed by warnings, 41.7% wanted upgrade recommendations, and 70.8% wanted PDF export. These results support the problem hypothesis, but the sample is small and should not be treated as proof of market-wide demand.

### Before MVP — hypotheses
- **H1:** A browser workflow without local installation will make dependency checking easier for students and small teams.
- **H2:** A short, prioritised report with plain-language summaries and fix-version information will be easier to act on than a raw advisory list.
- **H3:** A PDF/JSON report will help users show that a check was performed.
- **H4:** Users will be more comfortable when the original manifest and source code are not uploaded to a DepSentry server; package names and versions are still sent to OSV.dev for lookup.

### Action and data to collect
Ask 3–5 target users to complete a scan using their own non-confidential test manifest or the example file. Record: task completion, time to first result, parsing/API errors, whether they can identify the highest-priority issue, whether they can explain the recommended next step, whether export works, and privacy concerns. Ask each participant to rate ease of use from 1–5 and state one confusing part.

### After MVP — insight rule
Compare observed results with the hypotheses. Keep the feature if users complete the workflow and understand the report; revise parsing, labels, or remediation wording if users get stuck; do not infer willingness to pay from a usability test. Record actual participant count and actual responses in the final report. **No beta-test outcome is claimed in this file.**

## 4. Alpha test checklist

Run these checks before showing the MVP to users:

1. Open `index.html` in a modern browser and confirm all sidebar pages open.
2. Load the built-in example and run a live scan while online. Confirm the result says `OSV.dev` and contains real advisory IDs or a clear no-matching-records result.
3. Turn off the network or block `api.osv.dev`, run a scan, and confirm an error appears and no fake findings/report are saved.
4. Upload a `requirements.txt` with exact `package==version` entries; confirm it is parsed as PyPI.
5. Upload a `package-lock.json`; confirm exact versions are extracted. For ranged `package.json` entries, confirm the app asks for exact versions/lockfile rather than claiming it checked a range as an exact version.
6. Upload a `pom.xml` with concrete Maven dependency versions; confirm dependencies are parsed and sent with the Maven ecosystem.
7. Try an unsupported or malformed file; confirm a readable error appears.
8. Export JSON and check it contains project name, date, dependency list, source, and findings.
9. Use **Save PDF** and save the report from the browser print dialog.
10. Open **Reports**, reopen a saved report, refresh the page, and confirm history remains in the same browser.
11. Clear history and confirm locally saved reports disappear.
12. Check the privacy notice: it must say that the manifest is read locally but package names and versions are sent to OSV.dev.

## 5. Beta test plan

Invite 3–5 students, freelancers, or small-team developers who were not involved in building the interface. Give them the same short task without explaining each click. Do not ask them to upload confidential project files. Collect completion rate, time, errors, ease-of-use rating (1–5), report comprehension, usefulness of the fix guidance, export success, and privacy concerns. Save anonymised observations and improve the interface based on repeated issues.

## 6. MVP-level SWOT

- **Strengths:** no installation; standard manifest workflow; live public vulnerability records; readable findings; report export; source code not required.
- **Weaknesses:** no secure user accounts or cloud storage; exact versions required; browser storage is device-local; OSV results may not cover every issue.
- **Opportunities:** students, freelancers, small agencies; clearer educational reporting; later API/CLI integration after validating demand.
- **Threats:** established free scanners; API/network outages; false confidence from an empty result; privacy concerns about disclosing package names and versions to a third party.

## 7. Out of scope for this MVP

Real sign-in, cloud-synchronised history, shared workspaces, billing, team permissions, CI/CD, CLI/API, and automated compatibility testing are not implemented. The profile screen is a demo profile only. These are roadmap items, not features to claim during the presentation.
