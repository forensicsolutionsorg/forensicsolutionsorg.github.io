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
- An opt-in OpenAI draft workflow that turns free-form patient notes into a reviewable SOAP draft using the configured lowest-cost model (`gpt-6-luna`); it sends notes only when requested, uses the site's Cloudflare Worker instead of exposing an OpenAI API key, and never replaces the structured record automatically

## Deploying the AI service

The static site calls `ai-worker`, a Cloudflare Worker that holds the OpenAI key as a
Cloudflare secret. It limits a client address to 10 drafts per minute. Adjust the
`NARRATIVE_RATE_LIMITER` binding in `ai-worker/wrangler.jsonc` if that limit does not
fit your expected traffic, and add Cloudflare WAF rules or user authentication before
raising it.

1. Install and authenticate Wrangler: `npm install --global wrangler && wrangler login`.
2. From `ai-worker`, set the secret: `wrangler secret put OPENAI_API_KEY`.
3. Deploy: `wrangler deploy`. Cloudflare prints the worker URL.
4. Replace `AI_PROXY_URL` in `index.html` with
   `https://<worker-name>.<your-subdomain>.workers.dev/v1/narrative`.
5. If the production site's origin is not `https://medicsoap.com`, update
   `ALLOWED_ORIGIN` in `ai-worker/wrangler.jsonc` and redeploy.

Do not put the OpenAI API key in `index.html`, a Cloudflare Worker variable, or git.

## Privacy and clinical note
This tool documents care; it does not replace protocol knowledge or clinical judgment.
The structured workflow does not send data to a server. The optional AI workflow sends
the notes you submit to this site's Cloudflare Worker, which forwards them to OpenAI, so
use it only when your organization permits that disclosure of PHI. Free-form AI notes are
not included in local draft autosave. Drafts and display preferences may otherwise be
stored in browser local storage; do not enter unnecessary PHI and clear browser storage
when appropriate. Review every generated narrative against the ePCR and source record.
