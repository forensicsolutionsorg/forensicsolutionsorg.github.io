# RI EMS ALS Narrative Builder

Single-file SOAP narrative generator built around Rhode Island EMS protocols, with a focus on detailed ALS documentation.
`index.html` is the sole canonical deployed app; open it in any browser. No install,
server, or account is required.

## What it does
- Builds a detailed, sentence-based SOAP narrative from entered information; it does not use AI or infer care
- Documents ALS assessment, procedures, medications, vascular access, treatment response, reassessment vitals, and disposition
- Section navigation (Patient, Subjective, Objective, Assessment, Treatment, Disposition, Review) with completion indicators and a sticky summary bar
- Checkbox and dropdown driven sections with free text for additional clinical details
- Structured medication rows (drug, dose, unit, route, time) and vascular access rows (IV/IO, gauge, site, attempts, patency, time)
- Completeness audit with required, recommended, and not-applicable checks based on chief complaint, impression, and disposition
- Explicit reassessment vitals/notes, ECG, secondary impression, physical exam, airway/oxygen support, vascular access, and transfer/refusal/no-contact details
- Accessible tri-state symptom controls, in-page dialogs, copy error reporting, and print/PDF export with a timestamp
- Inline audit links to source fields, local draft autosave/restore, and keyboard shortcuts (Ctrl/Cmd+Enter to generate, Ctrl/Cmd+Shift+C to copy)

## Privacy and clinical note
This tool documents care; it does not replace protocol knowledge or clinical judgment.
The app does not send data to a server. Drafts and display preferences may be stored
in the browser's local storage; do not enter unnecessary PHI and clear browser storage
when appropriate. Review every generated narrative against the ePCR and source record.
