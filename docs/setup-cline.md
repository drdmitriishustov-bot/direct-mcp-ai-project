# Подключение direct-mcp к Cline

## 1. Требования

- VS Code с расширением [Cline](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev)

## 2. Настройка MCP-сервера

В корне проекта уже есть файл `.cline/mcp_settings.json`:

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

## 3. Открытие проекта

1. Откройте VS Code с установленным Cline
2. File → Open Folder → выберите папку проекта
3. Cline автоматически прочитает `.cline/mcp_settings.json`

## 4. Проверка подключения

Откройте панель Cline и напишите:

```
покажи мои кампании
```

Cline должен обнаружить сервер `lidfly` (6 meta-инструментов v3) и через них показать ваши кампании.

## 5. Альтернативный способ — через UI

1. Откройте панель Cline
2. Нажмите на иконку настроек (шестерёнка)
3. Перейдите в раздел MCP Servers
4. Добавьте сервер:
   - Name: `lidfly`
   - URL: `https://lidfly.ru/mcp/v3`
   - Headers: `Authorization: Bearer YOUR_API_KEY`

## 6. Инструкции для агента

Cline читает `CLAUDE.md` из корня проекта как системные инструкции. Ваши бизнес-настройки — в `PROJECTS.md`.
