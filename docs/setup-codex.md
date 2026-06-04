# Подключение direct-mcp к OpenAI Codex

## 1. Настройка MCP-сервера (проектный конфиг)

Создайте или проверьте файл `.codex/mcp.json` в корне проекта:

```json
{
  "mcpServers": {
    "lidfly": {
      "url": "https://lidfly.ru/mcp/v3",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Замените `YOUR_API_KEY` на ваш API-ключ из [личного кабинета direct-mcp](https://lidfly.ru).

## 2. Альтернатива — глобальный конфиг через CLI

Если проектный `.codex/mcp.json` не подхватывается (известная проблема в ранних версиях `codex-cli`), добавьте сервер глобально:

```bash
codex mcp add lidfly -- \
  npx -y mcp-remote https://lidfly.ru/mcp/v3 \
  --header "Authorization: Bearer YOUR_API_KEY"
```

Проверка:

```bash
codex mcp list --json
codex mcp get lidfly --json
```

## 3. Запуск

```bash
codex -C /path/to/your/project
```

Или откройте папку проекта в Codex App.

## 4. Проверка подключения

В сессии напишите:

```
проверь MCP и покажи список tools
```

Ожидаемо:
- Сервер `lidfly` виден
- Доступны 6 meta-инструментов v3: `search_tools`, `get_tool_schema`, `call_tool`, `call_write_tool`, `get_methodology`, `subscription_status`
- Провайдерский каталог (`get_campaigns`, `vk_get_campaigns`, `wordstat_top_requests`, `workspace_get_context` и др.) в списке не виден — AI находит инструменты через `search_tools` и вызывает через `call_tool` / `call_write_tool`

## 5. Инструкции для агента

Codex читает `AGENTS.md` из корня проекта, который ссылается на `CLAUDE.md` с правилами работы с API.

Ваши бизнес-настройки — в `PROJECTS.md`.

## 6. Навыки (Skills)

В папке `.codex/skills/` лежат готовые навыки:

| Навык | Описание |
|-------|---------|
| `seo-optimizer` | SEO-аудит и оптимизация страниц |

Навыки активируются автоматически по контексту запроса.
