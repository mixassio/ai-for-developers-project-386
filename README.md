### Hexlet tests and linter status:
[![Actions Status](https://github.com/mixassio/ai-for-developers-project-386/actions/workflows/hexlet-check.yml/badge.svg)](https://github.com/mixassio/ai-for-developers-project-386/actions)

## Docker и деплой

Корневой `Dockerfile` собирает единый образ: Fastify-бэкенд раздаёт API
(`/admin`, `/public`) и собранный фронтенд-SPA (`/`) на одном порту из
переменной окружения `PORT`. Приложение стартует автоматически (`CMD node dist/index.js`).

Локальная проверка:

```bash
docker build -t calendar-of-calls .
docker run --rm -e PORT=8080 -p 8080:8080 calendar-of-calls
# открыть http://localhost:8080 — SPA; API доступен по /public и /admin
```

### Деплой на Render

1. В дашборде Render: **New → Blueprint** и подключите этот репозиторий —
   Render прочитает `render.yaml` и создаст веб-сервис из `Dockerfile`.
2. Render автоматически задаёт переменную `PORT`; приложение её читает —
   ничего настраивать не нужно.
3. После сборки сервис получит публичную ссылку вида
   `https://<имя-сервиса>.onrender.com`.