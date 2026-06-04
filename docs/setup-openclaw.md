# Подключение direct-mcp к OpenClaw

## 1. Настройка

Скопируйте пример конфига:

```bash
cp .openclaw/openclaw.example.json .openclaw/openclaw.json
```

Отредактируйте `.openclaw/openclaw.json` — замените `YOUR_API_KEY` на ваш API-ключ:

```json
{
  "skills": {
    "entries": {
      "yandex-direct": {
        "enabled": true,
        "env": {
          "LIDFLY_TOKEN": "YOUR_API_KEY"
        }
      }
    }
  }
}
```

API-ключ получите в [личном кабинете direct-mcp](https://lidfly.ru). Под v3 это единый ключ LidFly — один эндпоинт `https://lidfly.ru/mcp/v3` покрывает Директ, VK, Вордстат, Workspace и публикацию.

> **Важно:** Файл `.openclaw/openclaw.json` содержит ваш токен — не коммитьте его в git. В репозитории лежит только `.openclaw/openclaw.example.json` с плейсхолдером.

## 2. Навыки (Skills)

В папке `.openclaw/skills/yandex-direct-campaign-builder/` лежит готовый навык для создания и управления кампаниями Яндекс Директа. Он автоматически активируется, когда вы спрашиваете про кампании, объявления, статистику.

## 3. Проверка подключения

Запустите OpenClaw и напишите:

```
покажи мои кампании
```

OpenClaw должен вызвать MCP-сервер через навык `yandex-direct-campaign-builder`.

## 4. Инструкции для агента

Правила работы с API описаны в навыке `.openclaw/skills/yandex-direct-campaign-builder/SKILL.md`.

Ваши бизнес-настройки — в `PROJECTS.md`.
