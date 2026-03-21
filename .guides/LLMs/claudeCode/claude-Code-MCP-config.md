# Configuración de MCPs para Claude Code

## ¿Qué es MCP?
El **Model Context Protocol (MCP)** es un estándar abierto que permite a los asistentes de IA (como Claude) conectarse de forma segura a tus datos y herramientas locales (bases de datos, repositorios, servidores de archivos, etc.).

## Requisitos
- **Claude Code CLI** instalado y autenticado.
- **Node.js** v18+ instalado.

## Instalación de Servidores MCP Comunes

En este curso utilizaremos principalmente los MCPs de sistema de archivos, PostgreSQL (Supabase) y herramientas de QA.

### 1. Instalar Servidores

Instalaremos los servidores MCP necesarios globalmente o en tu proyecto:

```bash
# Servidor de Sistema de Archivos (para que Claude lea/escriba mejor)
npm install -g @modelcontextprotocol/server-filesystem

# Servidor de PostgreSQL (para bases de datos)
npm install -g @modelcontextprotocol/server-postgres
```

### 2. Configurar `claude_config.json`

Claude Code busca un archivo de configuración para saber qué servidores MCP iniciar.

1. Ubica o crea el archivo de configuración:
   - **Windows:** `%APPDATA%\Claude\claude_config.json`
   - **Mac/Linux:** `~/.config/claude/claude_config.json`

2. Edita el archivo con la siguiente estructura:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "C:\\Users\\admin\\Mi unidad\\Ecosistemas\\EcoInnova" 
      ]
    },
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://user:password@localhost:5432/mydb"
      ]
    }
  }
}
```
*(Ajusta las rutas y cadenas de conexión a tu entorno real)*.

## Verificación

Para verificar que Claude está detectando los MCPs:

1. Inicia Claude Code:
   ```bash
   claude
   ```

2. En el prompt, escribe:
   ```text
   /mcp list
   ```
   Deberías ver una lista de los servidores conectados (ej: `filesystem`, `postgres`) y las herramientas disponibles.

## Uso en el Curso

### Conectar a Supabase (PostgreSQL)
Para probar la base de datos con MCP:
1. Obtén tu string de conexión de Supabase (Settings -> Database -> Connection String).
2. Agrégalo al `claude_config.json` bajo la clave `postgres`.
3. Pídele a Claude: *"Muestrame las tablas de la base de datos"*.

### Conectar a GitHub
Si necesitas que Claude interactúe con issues o PRs:
1. Instala el servidor MCP de GitHub (si está disponible/configurado).
2. Asegúrate de tener el token `GITHUB_TOKEN` en tus variables de entorno.

## Solución de Problemas

**Error: "Connection refused" o "Server not found"**
- Verifica que el comando `npx` funciona en tu terminal.
- Asegúrate de que las rutas en `args` sean absolutas y existan.
- En Windows, usa doble barra invertida `\\` para las rutas en el JSON.

**Los cambios en `claude_config.json` no se aplican**
- Reinicia la sesión de Claude Code (sal con `exit` y vuelve a entrar).
