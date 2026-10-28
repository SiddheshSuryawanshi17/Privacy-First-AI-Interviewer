# Adding a new interview role

Roles such as **AI/ML Engineer** or **Cybersecurity Analyst** are the most-requested addition. A role is just a name plus some text in five places — no new modules needed.

Use the **exact same role string** everywhere (e.g. `"AI/ML Engineer"`); it's used as a dictionary key across the app.

## Checklist

| # | File | What to add |
|---|---|---|
| 1 | `app.py` → `ROLES` | The role name, so it appears in the role dropdown |
| 2 | `app.py` → `_get_fallback_question()` | 5 hand-written questions, used when the LLM is unavailable or returns nothing (roles without an entry fall back to Backend questions — Frontend, DevOps and Cloud still need theirs!) |
| 3 | `llm/prompts.py` → `_ROLE_CONTEXT` | One "Focus areas: …" sentence that steers Gemma's questions |
| 4 | `utils/ats.py` → `ROLE_KEYWORDS` | ~20 lowercase skill keywords for offline ATS scoring |
| 5 | `utils/ats.py` → `role_jd_map` (inside `calculate_ats_score`) | A one-line template job description |
| 6 | `utils/resume.py` → both default `roles_list` lists | The role name, so resume/JD auto-detection can pick it |

## Example: AI/ML Engineer

```python
# llm/prompts.py — _ROLE_CONTEXT
"AI/ML Engineer": (
    "Focus areas: ML fundamentals (bias/variance, regularization), model evaluation metrics, "
    "feature engineering, deep learning architectures, training at scale, MLOps and model serving, "
    "data leakage, and responsible AI."
),
```

```python
# utils/ats.py — ROLE_KEYWORDS
"AI/ML Engineer": [
    "python", "pytorch", "tensorflow", "scikit-learn", "pandas", "numpy",
    "machine learning", "deep learning", "nlp", "computer vision", "transformers",
    "feature engineering", "model evaluation", "mlops", "mlflow", "docker",
    "sql", "statistics", "llm", "fine-tuning",
],
```

## Test it

1. Add a case to `tests/test_role_detection.py` (role detection) and `tests/test_ats.py` (keyword scoring).
2. Run `python -m pytest tests/`.
3. Start the app, pick the new role, and do a short 3-question session to sanity-check the questions.

## Ideas for roles

AI/ML Engineer · Cybersecurity Analyst · Data Engineer · Data Analyst · Mobile (Android/iOS) · Embedded Systems · Product Manager · QA / SDET
