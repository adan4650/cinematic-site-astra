# Optional browser setup

Use the session's connected Higgsfield tools when they support the media operation. Use existing Codex browser capabilities for browser tasks. Add Chrome DevTools MCP only when you need it; the repository's default configuration does not load a browser server.

## Chrome DevTools MCP

Install a supported Node.js version with npm and Google Chrome. Confirm both `node --version` and `npx --version` work in the shell that launches Codex.

Merge the table in [.codex/chrome-devtools.example.toml](../.codex/chrome-devtools.example.toml) into [.codex/config.toml](../.codex/config.toml). Preserve unrelated settings and do not duplicate an existing server table. The official package is `chrome-devtools-mcp`, without an Anthropic namespace.

Start a new Codex session in the trusted repository and inspect the available MCP tools. If your client does not read project configuration, use its documented MCP setup interface. Do not change global configuration unless that is your intended scope.

The example uses `@latest` for setup convenience; a maintained shared installation can pin a version after testing it. On Windows, if direct `npx` startup fails, use the commented `cmd /c npx` alternative in the example. Do not enable both variants in the same table.

## Authentication

An automation browser can use a different profile from your everyday browser. Open Higgsfield through the selected tool and sign in in that browser when required. Being signed into a different Chrome or Edge window does not establish that the automation session is authenticated.

The repository contains no browser credentials or API keys. Do not copy cookies, authentication tokens, or credentials into these files. A connected Higgsfield plugin and a browser session are separate ways to access the service; use whichever is available and appropriate.

## Troubleshooting

| Symptom | Next step |
| --- | --- |
| `npx` not found | Install Node with npm or correct that shell's PATH; a standalone Node executable is not enough |
| Skill not listed | Reopen a session in the repository root or explicitly ask the agent to read the skill file |
| Astra model unavailable | Select an Astra model your account supports and adjust the project model default |
| Browser opens signed out | Sign into the browser launched or connected by that tool |
| Model/settings unavailable | Check the service's current capabilities; choose a supported option with the user |
| Generation still pending | Retain the existing job ID and check it; avoid duplicate submissions |
| No browser or media tools | Build with a poster and run the supplied video prompt manually |

Sources: [official Chrome DevTools MCP](https://github.com/ChromeDevTools/chrome-devtools-mcp), [client configuration](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/main/docs/client-configurations.md), [browser profiles](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/main/docs/advanced-usage.md), and [Codex MCP](https://developers.openai.com/codex/mcp).
