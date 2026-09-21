# RI EMS SOAP Narrative Builder

Single file, offline SOAP narrative generator built around Rhode Island EMS protocols.
Open `index.html` in any browser. No install, no server, nothing leaves the device.

## What it does
- Checkbox and dropdown driven S, O, A, P sections with free text for anything not listed
- Structured medication rows (drug, dose, unit, route, time) and vascular access rows (IV/IO, gauge, site, attempts, patency, time)
- Completeness flags based on chief complaint and impression (for example, 12 lead missing on a chest pain call, last known well missing on a stroke)
- Copy button for pasting into ImageTrend Elite

## Note
This tool documents care; it does not replace protocol knowledge or clinical judgment. No PHI is stored.
