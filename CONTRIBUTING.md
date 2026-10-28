# Contributing

Thanks for helping make interview practice private and free! Whether it's a typo fix or a whole new interview role, contributions are welcome.

## Ways to help

- 🧭 **Add an interview role** (AI/ML, Cybersecurity, Data Engineering, Mobile…) — follow [docs/adding_a_role.md](docs/adding_a_role.md)
- 🐛 **Fix a bug** — check [issues labelled `bug`](../../issues?q=is%3Aissue+is%3Aopen+label%3Abug)
- 🌱 **Pick a starter task** — look for [`good first issue`](../../issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)
- 💬 **Improve prompts** — better questions and fairer scoring in `llm/prompts.py`
- 🎨 **UI / accessibility** — `app.py` and `theme.css`
- 📚 **Docs & translations**

Not sure where to start? Open an issue and ask — we're happy to help.

## Development setup

```bash
# Fork on GitHub, then:
git clone https://github.com/<your-username>/Privacy-First-AI-Interviewer.git
cd Privacy-First-AI-Interviewer
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

ollama pull gemma4:4b && ollama serve   # in another terminal
python app.py                           # http://127.0.0.1:7860
```

## Workflow

1. **Open or claim an issue** first for anything bigger than a small fix, so work isn't duplicated.
2. **Branch** from `main` with a descriptive name: `feat/cybersecurity-role`, `fix/timer-reset`, `docs/windows-setup`.
3. **Make your change** and add or update tests in `tests/`.
4. **Run the tests** — they're fully mocked, no Ollama or mic needed:
   ```bash
   python -m pytest tests/ -k "not e2e"   # fast loop (~1 min)
   python -m pytest tests/                # full suite before pushing (~8 min)
   ```
5. **Commit** using [Conventional Commits](https://www.conventionalcommits.org/), matching the existing history:
   `feat: add Cybersecurity interview role`, `fix: reset timer on skip`, `docs: add Windows setup notes`
6. **Open a pull request** against `main` and fill in the template. Screenshots or a short clip help a lot for UI changes.

## Guidelines

- **Privacy first.** Never add calls to cloud APIs, analytics, or telemetry. New network access (e.g. a model download) must be one-time and documented in the README.
- **Never commit personal data.** Everything in `data/` (session DB, PDF reports, voices) is git-ignored — keep it that way. Use synthetic resumes in tests.
- **Degrade gracefully.** Optional components (VAD, TTS, ATS library) fall back instead of crashing; follow the same pattern.
- **Keep it CPU-friendly.** The app should stay usable on a normal laptop.
- **Style:** follow the surrounding code — type hints, module docstrings, `logging` instead of `print`.
- **Big files** (videos, models, datasets) don't belong in git — link to them instead.

## Reporting bugs and security issues

- Bugs and feature ideas: use the [issue templates](../../issues/new/choose).
- Security or privacy problems: please follow [SECURITY.md](SECURITY.md) instead of opening a public issue.

By contributing you agree your work is released under the [Apache 2.0 License](LICENSE) and that you'll follow the [Code of Conduct](CODE_OF_CONDUCT.md).
