# Security & Privacy Policy

Privacy is the core promise of this project, so we treat data-leak bugs as security issues.

## Reporting a vulnerability

**Please don't open a public issue.** Instead, use GitHub's [private vulnerability reporting](../../security/advisories/new) and include:

- what you found and its impact (e.g. "resume text is sent to a remote host"),
- steps to reproduce,
- the commit or version you tested.

We aim to acknowledge reports within 7 days.

## In scope

- Any network request carrying user data (audio, transcripts, resumes, JDs, scores)
- Personal data written outside `data/`, or committed to the repository
- The Gradio server being exposed beyond `127.0.0.1` by default
- Unsafe handling of uploaded files (path traversal, code execution)

## Out of scope

- The one-time model downloads from Hugging Face / Ollama on first run
- Vulnerabilities in Ollama, Gradio, or other upstream projects — please report those upstream
