# Freedom Calculator

Lead magnet: a visitor works out their freedom number, then gets the plan as a one-page PDF after entering name and email.

## Stack

- One static file: `index.html` (HTML, CSS, vanilla JavaScript). No build step, no framework, no backend.
- PDF: jsPDF 2.5.1 from cdnjs, generated in the browser.
- Lead capture: optional POST to a webhook (GoHighLevel inbound webhook).
- State: `localStorage` in the visitor's browser.

## Settings

Both are at the top of the last `<script>` block in `index.html`:

- `WEBHOOK_URL`: empty means no POST, the PDF is still delivered.
- `PROGRAM_URL`: the link behind the cohort program CTA (placeholder for now).

## Run

Open `index.html` in a browser, or host it on any static host. It can be embedded with an iframe.
