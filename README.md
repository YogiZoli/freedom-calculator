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

## Reliability and troubleshooting

- The PDF tool loads from `vendor/` first, then from two CDNs. If none loads, the visitor sees what to do and a Try again button.
- A lead is posted as JSON, then as a form post if the browser blocks that. If both fail it is kept in the visitor's browser (up to 5 leads, 7 days) and sent again on the next visit or when the connection returns. Every lead carries a `submissionId`, so a duplicate can be spotted.
- The thank-you screen always says whether the visitor still has to wait or can close the page, and offers an "Open the PDF in a new tab" link in case the download did not start.
- "Something not working? Show details" at the bottom of the page opens a step by step log (also printed to the browser console with the `[freedom-calculator]` prefix). Ask the visitor to press Copy report and send it.
