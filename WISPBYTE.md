# Cloady = BACKGROUND WORKER (role.txt = worker)
Koi public site nahi. Sirf: catalog/crawler refresh, naye episodes ka RSS watch, AniList + trending, TMDB backfill.
Result shared database (SQL_URL) me save hota hai; Wispbyte wala web zip use 5 min me utha leta hai.
Cloady ka URL users ko kahin dikhta nahi - sirf /health (host check) aur /status (admin key) hai.

Startup file: addon.py   |  Python 3.11+  |  pip install -r requirements.txt
Env (Cloady panel):
  SQL_URL, TOKEN_SECRET, ADMIN_KEY  -> Wispbyte wale zip ke SAME
  CPU_TARGET=40 (0.5 vCPU ke hisaab se default)   BEAT_SECONDS=600
Status: GET /status with header X-Admin-Key: <ADMIN_KEY>

## Wispbyte ke liye kaam (POST /rpc/meta | stream | skip)
Sirf signed call chalti hai (TOKEN_SECRET same ho); bina signature 403. Jawab chhota JSON hota hai, isliye 100 KB/s me bhi chalta hai.
