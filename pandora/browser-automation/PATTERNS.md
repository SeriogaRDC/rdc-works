# Browser Automation Patterns That Survive SPAs
*Hard-won lessons from driving logged-in web apps (banks, exchanges, AI chat UIs) via Chrome DevTools Protocol.*

## The rules we learned the hard way

1. **Click, don't guess.** Finding the real nav link and clicking it beats constructing URLs — SPAs 404 on deep links their router doesn't recognize.
2. **React owns `value`.** Setting input.value directly does nothing. Use the native setter + dispatch `input`/`change` events, or focus + `Input.insertText`.
3. **Labels eat clicks.** A checkbox that "won't click" usually wants its `<label>` clicked, not the input.
4. **Short sockets.** Open websocket, do ONE thing, close. Long-lived CDP connections in busy kernels timeout.
5. **Vision is the fallback that always works.** When DOM scripting fails (shadow DOM, canvas, captchas), screenshot + coordinate math (viewport-scaled!) unblocks everything.
6. **The page keeps writing.** Capture UI text AFTER the "done" state — streaming responses mean your first grab is always stale.
7. **Screenshots first on new sites.** `Page.captureScreenshot` before touching anything = know what the human sees.

## Stack

Plain Python: `websocket-client` + `requests` against `127.0.0.1:9222`. No Selenium, no Playwright — less abstraction, fewer surprises, full control.

## Proven against

- React/Next.js dashboards (bank, exchange)
- Chat UIs with streaming responses (5 different AI vendors)
- GeoIP-gated flows, 9-grid captchas (solved via vision)
- File upload flows, agreement checkboxes, modal dialogs
