# Подключение direct-mcp к Gemini CLI

## 1. Настройка MCP-сервера

В корне проекта уже есть файл `.gemini/settings.json`:

```json
{
  "mcpServers": {
    "lidfly": {
      "type": "http",
      "url": "https://lidfly.ru/mcp/v3",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Замените `YOUR_API_KEY` на ваш API-ключ из [личного кабинета direct-mcp](https://lidfly.ru).

## 2. Запуск

Откройте терминал в папке проекта и запустите:

```bash
gemini
```

Gemini CLI автоматически прочитает `.gemini/settings.json`.

## 3. Проверка подключения

В сессии напишите:

```
покажи мои кампании
```

Gemini должен обнаружить сервер `lidfly` (6 meta-инструментов v3) и через них показать ваши кампании.

## 4. Инструкции для агента

Gemini CLI читает `GEMINI.md` из корня проекта, который ссылается на `CLAUDE.md` с правилами работы с API.

Ваши бизнес-настройки — в `PROJECTS.md`.
