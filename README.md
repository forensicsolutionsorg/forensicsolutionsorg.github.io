# RI EMS SOAP Narrative Builder

Single-file, offline SOAP narrative generator built around Rhode Island EMS protocols.
`index.html` is the sole canonical deployed app; open it in any browser. No install,
server, or account is required.

## What it does
- Section navigation (Patient, Subjective, Objective, Assessment, Treatment, Disposition, Review) with collapsible sections, completion/warning indicators, a quick-start panel, and a sticky summary bar
- Checkbox and dropdown driven S, O, A, P sections with free text for anything not listed
- Structured medication rows (drug, dose, unit, route, time) and vascular access rows (IV/IO, gauge, site, attempts, patency, time)
- Completeness audit with required, recommended, and not-applicable checks based on chief complaint, impression, and disposition
- Explicit reassessment vitals/notes, ECG, secondary impression, physical exam, airway/oxygen support, vascular access, and transfer/refusal/no-contact details
- Accessible tri-state symptom controls, in-page dialogs, copy error reporting, and print/PDF export with a timestamp
- Inline audit links to source fields, a Required/Recommended review panel, local draft autosave/restore, and keyboard shortcuts (Ctrl/Cmd+Enter to generate, Ctrl/Cmd+Shift+C to copy)

## Privacy and clinical note
This tool documents care; it does not replace protocol knowledge or clinical judgment.
The app does not send data to a server. Drafts and display preferences may be stored
in the browser's local storage; do not enter unnecessary PHI and clear browser storage
when appropriate. Review every generated narrative against the ePCR and source record.
