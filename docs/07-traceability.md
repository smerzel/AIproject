# 07 — איפה כל דרישה יושבת

| דרישה | יחידה באפיון | קוד עיקרי | בדיקה |
|---|---|---|---|
| נושא: משרות ומועמדים | כל המערכת | `docs/00-vision.md` | `tests/test_architecture.py` (אין שפת טיסות) |
| התחברות | כניסה והרשאה | `app/views/auth.py`, `app/commands/identity.py`, `app/google_auth.py` | `tests/test_identity.py`, `tests/test_doors_google.py` |
| שלושה תפקידים | כניסה והרשאה | `app/security.py`, `app/views/auth.py`, `app/views/jobs.py`, `app/views/dashboard.py`, `app/templates/jobs/_pending.html`, `app/views/applications.py` | `tests/test_identity.py`, `tests/test_jobs.py`, `tests/test_doors_google.py`, `tests/test_access_and_tools.py` |
| חיפוש | איתור משרות, התאמה סמנטית | `app/queries/jobs.py`, `app/queries/semantic.py` | `tests/test_jobs.py`, `tests/test_semantic_agent.py` |
| דף פרטים | איתור משרות, החלטת גיוס, הערכה חוזרת | `app/views/jobs.py`, `app/views/applications.py` | `tests/test_ranking_rescreen.py` |
| טבלה או כרטיסים | איתור משרות, לוח בקרה, דירוג מועמדים | `jobs/table.html`, `jobs/ranking.html`, `app/queries/jobs.py`, `app/queries/ranking.py` | `tests/test_jobs.py`, `tests/test_ranking_rescreen.py` |
| לוח משרות פתוחות ונרשמים | לוח בקרה | `app/views/dashboard.py` | `tests/test_apply_dashboard.py` |
| הזנת נתונים | מחזור חיי משרה, הגשת מועמדות, החלטת גיוס, הערכה חוזרת | `app/commands/jobs.py`, `app/commands/applications.py` | `tests/test_jobs.py`, `tests/test_apply_dashboard.py`, `tests/test_ranking_rescreen.py`, `tests/test_decision_email.py` |
| סוכן בתהליך נפרד | הערכת סוכן, תתי-סוכנים | `agent/worker.py` (קריאה מהמסד), `agent/deep_agent.py`, `agent/mcp_client.py` | `tests/test_deep_agent.py` |
| סדרת מסמכי אפיון | — | `docs/` | — |
| מתכון Flask מהאתר skills.sh | — | `.agents/skills/flask-python`, `skills-lock.json` | — |
| מתכון מקומי וחוק קבוע לסוכן הקוד | — | `.cursor/skills/`, `.cursor/rules/sdad.mdc` | — |
| אתר ב-Flask | — | `wsgi.py`, `app/` | כל הבדיקות |
| מסד בענן (Somee) | — | `app/db.py`, `scripts/check_db.py` | בדיקת SQL Server ב-GitHub |
| חיפוש לפי משמעות של קורות חיים | הגשת מועמדות, התאמה סמנטית, הערכת סוכן, דירוג מועמדים | `agent/rag.py`, `app/queries/semantic.py`, `app/queries/ranking.py` | `tests/test_semantic_agent.py`, `tests/test_ranking_rescreen.py` |
| כתיבה בנפרד מקריאה | — | `commands/`, `queries/`, `views/` | `tests/test_architecture.py` |
| כל שינוי נשמר כאירוע | הערכה חוזרת | `app/event_store.py`, `app/projections.py`, `app/replay.py` | `tests/test_mcp_and_replay.py`, `tests/test_ranking_rescreen.py` |
| שירות חיצוני דרך MCP | הערכת סוכן, החלטת גיוס | `agent/mcp_client.py` קורא לחיפוש Tavily ולשליחת Gmail; `agent/notifier.py`, `app/queries/notifications.py`, `scripts/gmail_auth.ps1` | `tests/test_decision_email.py` (Gmail מוחלף בבדיקה) |
| שני כלים שקוראים קורות חיים | הערכת סוכן | `mcp_studio/extract_resume_profile.py`, `mcp_studio/evaluate_requirement_coverage.py`, `mcp_studio/tools.json` | `tests/test_mcp_and_replay.py`, `tests/test_access_and_tools.py` |
| סוכן עם שני עוזרים, חיפוש משמעות וחיפוש רשת | הערכת סוכן, תתי-סוכנים | `agent/deep_agent.py`, `agent/worker.py` | `tests/test_deep_agent.py` |
| הקוד ב-GitHub | — | [smerzel/AIproject](https://github.com/smerzel/AIproject), `.github/workflows/tests.yml` | הבדיקות ב-GitHub |
