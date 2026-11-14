# DepSentry usability test kit

## Status

No participant test results are recorded yet. Do not mark the test complete, report a success rate, or attribute a design change to users until at least five real participants have completed the tasks below and their anonymous observations have been recorded.

## Participants and safety

- Recruit at least five students, freelancers, or small-team developers who did not build DepSentry.
- Use participant IDs (`P01` to `P05`) rather than names or contact details.
- Ask participants to use the included example or a non-confidential manifest. Do not ask for source code, secrets, or private package names.
- Explain that package names and exact versions are sent to the public OSV.dev service; scan data and feedback are stored only in that browser.
- Record consent and stop if a participant does not want to continue.

## Test task

Give each participant this task without pointing out the controls:

> Check the provided dependency list, find the highest-priority result, explain what DepSentry recommends doing next, save or export the report, and find the report again in history.

Record whether the participant can:

1. Find New scan and load a sample file or enter exact-version dependencies.
2. Recognize validation or API errors and distinguish them from a completed scan.
3. Identify the scan source and understand that “No matching records” is not proof of safety.
4. Find a vulnerability ID, severity, affected version, and available OSV.dev fix threshold.
5. Explain the update recommendation and its compatibility caveat.
6. Export a report and reopen it from Reports.
7. Find the local profile and settings, and understand that there is no sign-in or cloud account.

Do not treat an OSV.dev outage as a participant failure. Record it as an environment issue and repeat the live-API portion when service is available.

## Blank participant record

Copy this section once per participant. Leave fields blank until a real session has taken place.

| Field | Observation |
|---|---|
| Anonymous participant ID | |
| Date (optional) | |
| Completed the scan task? (yes / partly / no) | |
| Time to first result | |
| Manifest type used | |
| Validation or network error encountered | |
| Identified highest-priority result? | |
| Correctly explained the next action? | |
| Understood “No matching records” limitation? | |
| Export and report reopen successful? | |
| Ease of use (1–5) | |
| Most confusing or missing part (participant's words) | |
| Privacy concern or comment | |
| Observer notes (no identifying data) | |

## Feedback form template

Use the in-app **Quick feedback** form after a report is open, or collect these answers on paper:

1. Is it clear what to update first? **Yes / Partly / No**
2. Is the Low risk / May break label useful and understandable? **Yes / Partly / No**
3. What is confusing or missing? **Free text**
4. How easy was the task? **1 (very difficult) – 5 (very easy)**
5. Did the result make it clear that no matching advisory does not guarantee safety? **Yes / Partly / No**
6. Did you have any privacy concerns about sending package names and versions to OSV.dev? **Free text**

Feedback in the app is local to the browser. The **Export feedback CSV** control exports locally stored responses; it does not transmit them.

## Review after five sessions

Complete only after actual sessions:

- Participants completed: `___ / 5`
- Most common point of confusion: `___`
- Repeated error or blocker: `___`
- Evidence (anonymous observation IDs): `___`
- Change made in response, if any: `___`
- Retest result: `___`
- Follow-up needed: `___`

Do not invent missing responses. If fewer than five sessions take place, state the actual count and keep the remaining sessions pending.
