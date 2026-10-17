# RI EMS SOAP Narrative Builder

Single-file, offline SOAP narrative generator built around Rhode Island EMS protocols.
`index.html` is the sole canonical deployed app; open it in any browser. No install,
server, or account is required.

## What it does
- Five-step workflow: Patient & history → ALS assessment → Treatment & response → Disposition → Review, with an all-fields view and sticky Back/Next controls
- Desktop mouse/keyboard layout uses compact checkbox rows, a slim header, one action bar, and a narrative side panel; touch layouts retain larger controls
- Compact ALS assessment groups mental status, airway, breathing, lung sounds, and circulation; vitals follow the core findings
- Complaint-specific symptom priorities and expandable cardiac, stroke, focused body exam, and secondary history panels; all findings remain accessible
- Live SOAP draft uses only entered findings and updates without approving a new copyable version; review the current narrative to enable copying or printing
- Record medications and IV/IO details once; these entries supply narrative wording and completeness checks without duplicate intervention checkboxes
- Protocol treatment shortcuts open medication or access entries with dose, route, time, and status left for the user to document
- Focused review puts dose concerns and the first five important gaps first, with remaining checks available and links back to the relevant fields
- Explicit “No additional symptoms reported when asked” option does not populate individual denials or normal exam findings
- Initial and reassessment vitals, ECG/monitor findings, clinical reasoning, response, transport, refusal, and no-contact documentation
- Browser-local draft autosave/restore, custom medications, dark mode, print/PDF, copy failure handling, and keyboard shortcuts (Ctrl/Cmd+Enter to review; Ctrl/Cmd+Shift+C to copy)

## Testing workflow
Serve this directory with a static HTTP server and test the working branch before merging to `main` (GitHub Pages). Check desktop and mobile entry, complaint changes, medication/access entry and removal, draft restore, audit links, no-contact/refusal, and copy/print protection after edits. This repository has no build step or package dependencies.

## Privacy and clinical note
This tool documents care; it does not replace protocol knowledge or clinical judgment.
The app does not send data to a server. Drafts and display preferences may be stored
in the browser's local storage; do not enter unnecessary PHI and clear browser storage
when appropriate. Review every generated narrative against the ePCR and source record.
