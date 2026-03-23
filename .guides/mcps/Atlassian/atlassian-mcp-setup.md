# Guía de Configuración: Atlassian MCP (Jira/Confluence)

## 📌 Descripción
Este servidor MCP conecta tu Asistente de IA directamente con tu instancia de Jira y Confluence. Permite a la IA:
*   Leer User Stories y Criterios de Aceptación.
*   Crear Tickets de Bugs.
*   Buscar documentación en Confluence.

**Paquete Oficial:** `@modelcontextprotocol/server-atlassian`

## 🛠️ Requisitos Previos

1.  **Cuenta de Atlassian:** Acceso a un sitio de Jira/Confluence en la nube.
2.  **API Token:** No uses tu contraseña. Necesitas un token.
    *   Ve a [id.atlassian.com/manage-profile/security/api-tokens](https://id.atlassian.com/manage-profile/security/api-tokens).
    *   Crea un token llamado "MCP-Key" y **cópialo**.

## ⚙️ Configuración

Agrega esta entrada a tu archivo de configuración MCP (`claude_config.json` o similar).

### Variables de Entorno Requeridas
El servidor necesita estas variables. Puedes ponerlas en tu `.env` o pasarlas en la configuración del cliente.

*   `JIRA_BASE_URL`: Tu URL (ej: `https://mi-empresa.atlassian.net`)
*   `JIRA_EMAIL`: Tu correo de login (ej: `yo@empresa.com`)
*   `JIRA_API_TOKEN`: El token que creaste.

### Ejemplo de Configuración JSON

```json
"atlassian": {
  "command": "npx",
  "args": [
    "-y",
    "@modelcontextprotocol/server-atlassian"
  ],
  "env": {
    "JIRA_BASE_URL": "https://tu-sitio.atlassian.net",
    "JIRA_EMAIL": "tu-email@dominio.com",
    "JIRA_API_TOKEN": "ATATT3xD..." 
  }
}
```

## 🧪 Verificación

Pídele a tu IA:
> "Busca en Jira el ticket con clave PROJ-1 y dime su estado."

Si responde con el título y estado del ticket, ¡la conexión es exitosa!

## ⚠️ Solución de Problemas

**Error 401/403 (Unauthorized):**
*   Verifica que el email sea EXACTAMENTE el mismo que usas para loguearte.
*   Asegúrate de que el token no haya expirado o sido revocado.

**Error "Resource not found":**
*   Verifica la `JIRA_BASE_URL`. No debe tener `/jira` al final, solo el dominio base.
