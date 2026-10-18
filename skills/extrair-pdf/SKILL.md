---
name: extrair-pdf
description: Extract a PDF's text on the user's computer, OCR included, to read, summarize or quote it.
---

Call `extract_pdf` (server `extrator-pdf-llm`) with the PDF's absolute Windows path; ask for it if missing.
- A file attached to the chat is not on the computer: use the attachment, or ask the user to add its folder with "+".
- Never pass `mode: replace` unless asked: it sends the PDF to the Recycle Bin.
- Long PDF: `includeText: false`, then read the .txt named in `output` in parts.
- `encrypted`: ask the user to remove the password. `failed`: relay `error`; if no account is active, tell them to open the Extrator and sign in.
- Server missing: if a shell is available, run `extrator-pdf-llm extract "<path>" --json` and read the .txt in `output`; otherwise the app is not installed: https://apps.microsoft.com/detail/9P08Z6RD6SG6
