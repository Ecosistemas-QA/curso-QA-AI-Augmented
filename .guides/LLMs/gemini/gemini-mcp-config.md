# Configuración de MCPs para Gemini CLI

## Descripción
Aunque Gemini CLI es una herramienta potente, su capacidad para interactuar con herramientas externas se potencia mediante el **Model Context Protocol (MCP)**. Esta guía te muestra cómo conectar servidores MCP (como bases de datos o sistemas de archivos) a tu flujo de trabajo con Gemini.

## Requisitos
- **Gemini CLI** (`@google/gemini-cli`) instalado.
- **Node.js** v18+ instalado.
- Una **API Key de Gemini** configurada.

## Estrategia de Conexión

A diferencia de Claude que tiene soporte nativo automático, para Gemini utilizaremos un **Archivo de Configuración de Herramientas** o una herramienta puente como **Context7** (según se defina en los laboratorios del curso).

A continuación, configuraremos el estándar basado en archivos JSON.

### 1. Instalar Servidores MCP

Primero, necesitamos los servidores que exponen las herramientas.

```bash
# Ejemplo: Servidor de Sistema de Archivos
npm install -g @modelcontextprotocol/server-filesystem

# Ejemplo: Servidor de Base de Datos (Postgres/Supabase)
npm install -g @modelcontextprotocol/server-postgres
```

### 2. Crear el archivo `mcp-config.json`

En la raíz de tu proyecto (o en tu carpeta de usuario), crea un archivo llamado `mcp-config.json`. Este archivo le dice a Gemini qué herramientas están disponibles.

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "./"
      ]
    },
    "playwright": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-playwright"
      ]
    }
  }
}
```

### 3. Ejecutar Gemini con MCP

Dependiendo de la versión del CLI y el wrapper del curso, usarás una bandera para indicar la configuración.

**Opción A (Soporte Nativo/Wrapper):**
```bash
gemini --mcp-config ./mcp-config.json "Navega a google.com y dime el título"
```

**Opción B (Vía Variables de Entorno):**
Configura la ruta globalmente para no repetirla:

**En Warp (PowerShell):**
```powershell
$env:MCP_CONFIG_FILE = "C:\Ruta\a\tu\mcp-config.json"
gemini "Analiza la base de datos y lista los usuarios"
```

## Servidores MCP del Curso

Para configurar las herramientas específicas (Testing, BD, Jira), consulta las **Guías Centralizadas** donde encontrarás los comandos de instalación y variables de entorno necesarias:

*   **[Guía de PostgreSQL / Supabase](../../mcps/Databases/postgres-mcp-setup.md)**
*   **[Guía de Playwright (UI Testing)](../../mcps/Testing/playwright-mcp-setup.md)**
*   **[Guía de Atlassian (Jira)](../../mcps/Atlassian/atlassian-mcp-setup.md)**

Una vez que tengas los comandos `npx ...` de esas guías, agrégalos a tu `mcp-config.json` como se muestra arriba.

## Verificación

Para probar si la conexión funciona, intenta un comando que requiera una herramienta externa:

```bash
gemini "Usa la herramienta de filesystem para listar los archivos en esta carpeta"
```

Si Gemini responde con la lista de archivos, ¡el MCP está conectado correctamente!

## Solución de Problemas

**Error: "Tool not found"**
- Verifica que el nombre del servidor en el JSON coincida con lo que Gemini intenta llamar.
- Asegúrate de haber instalado el paquete npm del servidor (`npm install -g ...`).

**Error: "Connection failed"**
- Revisa que los comandos en `args` sean correctos y ejecutables desde tu terminal.
- Si usas Windows, verifica el escape de las rutas (`\\` en lugar de `\`).
