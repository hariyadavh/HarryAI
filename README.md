# HarryAI — Market Research Intelligence

HarryAI is a research-oriented market analysis web app with:
- chart screenshot analysis
- historical pattern matching
- walk-forward backtesting
- user signup/login/logout
- secure password hashing with Python's built-in scrypt
- an admin dashboard showing registered users, signup time and last login
- SQLite for local testing and PostgreSQL for persistent production storage

## Run locally

```bash
python -m venv .venv
# Windows PowerShell:
.venv\Scripts\python.exe -m pip install -r requirements.txt
.venv\Scripts\python.exe -m uvicorn backend.main:app --reload
```

Open http://127.0.0.1:8000

Default local admin (change it for any public deployment):
- Email: `admin@harryai.local`
- Password: `HarryAI_Admin_123!`

## Render deployment

Create a PostgreSQL database on Render and set these environment variables on the web service:

- `DATABASE_URL` = your Render PostgreSQL internal connection string
- `ADMIN_EMAIL` = your private admin email
- `ADMIN_PASSWORD` = a strong private admin password
- `ADMIN_NAME` = your preferred admin name
- `COOKIE_SECURE` = `true`

Build command:

```text
pip install -r requirements.txt
```

Start command:

```text
uvicorn backend.main:app --host 0.0.0.0 --port $PORT
```

Root Directory should be blank when `backend/` is at the repository root.

## Important security note

The admin dashboard never displays user passwords. Passwords are stored as salted scrypt hashes. Never commit real passwords or database credentials to GitHub. Use Render environment variables for production secrets.

The market-analysis output is for research and education, not guaranteed financial advice.
