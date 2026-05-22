Project: Shareceipt — developer guidance for AI coding agents

Summary
- Small, static single-page web app (no server-side). UI in `index.html`, behavior in `script.js`, styles in `styles.css` and design-* CSS files.
- Receipt OCR/analysis relies on a client-side call to Google Generative Language API (Gemini) using an API key stored in `localStorage` under `apiKey`.

Big Picture / Architecture
- Single-page app: DOM + jQuery drive state. `FriendManager` (in `script.js`) is the central state manager: friends (Map), items (Map), DOM update and calculation logic.
- No backend persistence: all state is in-memory and in `localStorage` only for `apiKey`. Refresh loses data.
- External integrations:
  - Google Generative Language API endpoint used in `FriendManager.analyzeReceipt()`.
  - Browser `navigator.share()` used for sharing results.
  - Clipboard writes for copying individual summaries.

Key files to inspect when making changes
- index.html — overall layout, element IDs and buttons the JS binds to (e.g. `#receipt-upload-btn`, `#friends-list`, `#items-list`, `#total-amount-input`).
- script.js — core logic. Look for `class Friend`, `class Item`, `class FriendManager`. Most change points live here (UI binding, calculation, and receipt analysis prompt).
- styles.css, design-components.css, design-tokens.css — styling system and tokens.
- README.md — user-facing notes, API key instructions.

Project-specific conventions & patterns (actionable)
- DOM-centric updates: the app expects element IDs/classes to remain stable. If you rename or refactor elements, update selectors in `script.js` accordingly.
- State model: `FriendManager.friends` and `FriendManager.items` are Maps keyed by numeric IDs (see `Friend.nextId` and `Item.nextId`). Prefer updating model objects and calling `updateFriendList()` / `updateItemsList()` rather than directly mutating DOM.
- Receipt parsing protocol: `analyzeReceipt()` constructs a prompt (`promptMsg`) and expects the model reply to contain a ```json block with { items:[{name,amount}], total }. The code extracts with a regex — keep output structure stable or update regex parsing.
- API key storage: `localStorage.getItem('apiKey')` is the single source. Invalid-key handling clears this key.

Local dev & testing (how to run quickly)
- This is static: open `index.html` in a browser or run a local server for CORS/modern feature parity:
  - Python: `python3 -m http.server 8000` then visit `http://localhost:8000`.
  - Or use any static server (VS Code Live Server recommended).
- To test receipt upload behavior, set a valid Google API key via the key button in the UI (or `localStorage.setItem('apiKey', '<KEY>')` in the console).

Examples of common edits and where to make them
- Change OCR prompt or model endpoint: edit prompt text and endpoint URL in `FriendManager.analyzeReceipt()` inside `script.js` (search for `promptMsg` and the `generativelanguage.googleapis.com` URL).
- Add a persistent save: implement an export/import JSON routine that serializes `friendManager.friends` and `friendManager.items` and store in `localStorage` or a small backend; update UI buttons in `index.html` and add handlers in `script.js`.
- Modify item split logic: update `calculate()`, which contains `calculatePercentage` and `calculateShare` inner functions.

Notes for AI agents (concise)
- Preserve existing DOM IDs/classes unless intentionally refactoring; show diff for DOM changes and update selectors across `script.js`.
- When changing the receipt-output format, update both the prompt and the regex that extracts the triple-backtick JSON in `analyzeReceipt()`.
- Use the browser to manually verify: set `localStorage.apiKey` and exercise `#receipt-upload-input` with sample images; verify the UI populates items and totals.
- Avoid adding new heavy dependencies without justification; this project is purposely dependency-light (jQuery + Bootstrap + FontAwesome are already used).

If anything here is unclear or you want examples expanded (e.g., specific lines to change or test images), tell me which area to expand.
