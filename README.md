# MCP Clone C

Este repositório é um clone do [JetBrains/mcp-jetbrains](https://github.com/JetBrains/mcp-jetbrains) que implementa um proxy MCP (Model Context Protocol) para a integração entre Claude e IDEs JetBrains.

## Sobre o JetBrains MCP Proxy Server

O servidor atua como um proxy para redirecionar solicitações do cliente para IDEs JetBrains.

## Instalação do Plugin MCP Server

https://plugins.jetbrains.com/plugin/26071-mcp-server

## Uso com Claude Desktop

Para usar com o Claude Desktop, adicione o seguinte ao seu arquivo `claude_desktop_config.json`.
O caminho completo no MacOS: `~/Library/Application\ Support/Claude/claude_desktop_config.json`, no Windows: `%APPDATA%/Claude/claude_desktop_config.json`.

```json
{
  "mcpServers": {
    "jetbrains": {
      "command": "npx",
      "args": ["-y", "@jetbrains/mcp-proxy"]
    }
  }
}
```

## Configuração

Se você estiver executando várias IDEs com o servidor MCP e quiser se conectar a uma específica, adicione à configuração do servidor MCP:
```json
"env": {
  "IDE_PORT": "<porta do servidor web embutido da IDE>"
}
```

Por padrão, nos conectamos à IDE em 127.0.0.1, mas você pode especificar um endereço/host diferente:
```json
"env": {
  "HOST": "<host/endereço do servidor web embutido da IDE>"
}
```

Para habilitar o logging, adicione:
```json
"env": {
  "LOG_ENABLED": "true"
}
```

## Como compilar
1. Testado no macOS
2. `brew install node pnpm`
3. Execute `pnpm build` para compilar o projeto
