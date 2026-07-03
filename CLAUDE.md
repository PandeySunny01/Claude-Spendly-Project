# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project: Spendly

A Flask-based personal expense tracker web app. Most of the app logic is intentionally incomplete — it is a step-by-step learning project. The route stubs in `app.py` include comments indicating which step each belongs to.

## Running the app

```
# From expense-tracker/ (the inner directory containing app.py)
python app.py
```

Runs on `http://127.0.0.1:5001` in debug mode.

## Running tests

```
pytest
```

To run a single test file:

```
pytest tests/test_something.py
```

## Installing dependencies

```
pip install -r requirements.txt
```

Dependencies: `flask`, `werkzeug`, `pytest`, `pytest-flask`.

## Architecture

- **`app.py`** — all Flask routes. Import `get_db()` / `init_db()` from `database/db.py` when the DB layer is implemented.
- **`database/db.py`** — stub for the SQLite layer. Needs `get_db()` (connection with `row_factory` and foreign keys), `init_db()` (CREATE TABLE IF NOT EXISTS), and `seed_db()` (sample data). The DB file is `expense_tracker.db` (gitignored).
- **`templates/`** — Jinja2 templates. All pages extend `base.html`, which provides the navbar, footer, Google Fonts (DM Serif Display + DM Sans), and static asset links.
- **`static/css/style.css`** — uses CSS custom properties (`--ink`, `--paper`, `--accent`, etc.) defined in `:root`. Theme colors: dark green accent (`#1a472a`), warm paper background (`#f7f6f3`).
- **`static/js/main.js`** — empty placeholder; add client-side JS here as features are built.

## Implementation steps (per `app.py` comments)

| Step | Route/Feature |
|------|--------------|
| 1 | Database setup (`database/db.py`) |
| 3 | `/logout` |
| 4 | `/profile` |
| 7 | `/expenses/add` |
| 8 | `/expenses/<id>/edit` |
| 9 | `/expenses/<id>/delete` |

## Database

SQLite. `get_db()` should set `row_factory = sqlite3.Row` and `PRAGMA foreign_keys = ON`. The database file path is `expense_tracker.db` in the project root.

## Windows notes

Use `python` (not `python3`) on this machine. Activate the venv with:

```powershell
.\venv\Scripts\Activate.ps1
```
