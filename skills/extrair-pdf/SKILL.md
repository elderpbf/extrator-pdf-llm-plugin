---
name: extrair-pdf
description: Extract the text of a PDF on the user's computer, scanned pages included. Use when the user asks to read, summarize, analyze, search or quote a PDF file on their machine (a petição, sentença, processo, contrato, laudo), or gives a path ending in .pdf.
---

The Extrator PDF para LLM app does the extraction on the user's own computer. Documents never leave
the machine; only the extracted text reaches this conversation.

1. Get the PDF's absolute path. If the user named a file without a path, ask for it, or look for it
   in the folder they are working in.
2. Call the `extract_pdf` tool of the `extrator-pdf-llm` server with that path. Keep the default
   `mode` (`sidebyside`): it writes the .txt next to the PDF and never touches the PDF. Never pass
   `mode: replace` unless the user explicitly asked to replace the original, because it sends the
   PDF to the Recycle Bin.
3. For a long PDF (hundreds of pages), pass `includeText: false` and read the .txt named in `output`
   in parts, instead of taking the whole text at once.
4. Read `status`:
   - `done`: work from the text. Mention the .txt path once, so the user can find it.
   - `encrypted`: the PDF is password-protected; ask the user to remove the password and try again.
   - `failed`: relay `error` in plain words. If it says no account is active, tell the user to open
     the Extrator PDF para LLM, sign in, and ask again.

If the `extrator-pdf-llm` server is missing or does not start, the app is not installed on this
computer: tell the user to install it from the Microsoft Store,
https://apps.microsoft.com/detail/9P08Z6RD6SG6 (Windows only), and sign in. As a fallback when the app is
installed but the server is unavailable, the same extraction runs in a terminal:
`extrator-pdf-llm extract "C:\path\file.pdf" --json` prints the summary with the .txt path.
