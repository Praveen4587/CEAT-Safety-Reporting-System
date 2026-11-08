# CEAT SafeTrack - Render + Supabase

## What changed
- Added hosted PostgreSQL support using `DATABASE_URL` (Supabase Session Pooler).
- Kept SQLite as the local-development fallback.
- Added Render `Procfile` and `render.yaml`.
- Removed photo upload and photo evidence UI/handlers.
- Kept CEAT branding, department templates and system-data monthly exports.

## Deploy to Render
1. Push this folder's contents to a GitHub repository.
2. In Render choose **New + → Web Service**, connect the repository.
3. Build command: `pip install -r requirements.txt`
4. Start command: `python app.py serve --host 0.0.0.0 --port $PORT`
5. Add `DATABASE_URL` in Render Environment Variables. Use Supabase **Session Pooler**:
   `postgresql://postgres.<project-ref>:<NEW_PASSWORD>@<POOLER_HOST>:5432/postgres?sslmode=require`
6. Save and deploy. Never commit the real connection string or password.

The first hosted start creates the PostgreSQL tables automatically. Run the app's
existing administrator setup only after the database connection is confirmed.

## Local run
- Windows: run `START_SERVER.bat` or `python app.py serve`.
- Local mode uses `data/safetrack.db` when `DATABASE_URL` is not set.

## Important limitations
- SMTP email OTP and forgot-password OTP are not implemented/configured in this release.
- Render Free services may sleep. Free hosting is for demonstration/testing only.
- Do not use real CEAT employee data until CEAT IT approves the hosting and security.
