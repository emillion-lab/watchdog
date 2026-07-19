# 🐕 watchdog

Централен мониторинг на emillion-lab. Всеки ден в 05:00 UTC проверява:

1. **Достъпност** — всички deploy-нати страници връщат HTTP 200
2. **Свежест на данните** — скрейперите (BAK автобуси/полети, Gramofonche) са commit-вали в рамките на прага си
3. **Валидност** — JSON файловете с данни се парсват

## При проблем
- Workflow-ът fail-ва → GitHub праща имейл (Settings → Notifications → Actions трябва да е включено)
- Отваря се/допълва се issue с етикет `watchdog` и списък на счупеното

## Настройка
Всичко се управлява от [`targets.json`](targets.json) — добавяй/махай URL-и и файлове за следене без да пипаш workflow-а.

- `url_checks` — списък страници за HTTP проверка
- `freshness_checks` — repo + path + max_hours (колко стари може да са данните)
- `json_validity_checks` — raw URL-и на JSON файлове

## Ръчно пускане
Actions → watchdog → Run workflow
