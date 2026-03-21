# Guía de Instalación de GitHub Copilot CLI

## Descripción
**GitHub Copilot CLI** es una extensión oficial para la herramienta de línea de comandos de GitHub (`gh`). Lleva la potencia de Copilot directamente a tu terminal, permitiéndote generar comandos de shell, explicaciones y scripts usando lenguaje natural.

## Requisitos Previos

- **GitHub CLI (`gh`)**: Versión 2.0 o superior.
- **Suscripción activa**: GitHub Copilot Individual o Business.
- **Cuenta de GitHub**: Autenticada en tu terminal.

## Instalación

### Paso 1: Instalar GitHub CLI (`gh`)

Si aún no tienes el CLI base de GitHub:

**Windows (winget):**
```powershell
winget install --id GitHub.cli
```

**Mac (Homebrew):**
```bash
brew install gh
```

**Linux:**
Consulta las instrucciones oficiales según tu distribución.

### Paso 2: Autenticación

Inicia sesión con tu cuenta de GitHub que tiene acceso a Copilot:

```bash
gh auth login
```
*Sigue los pasos en pantalla (selecciona HTTPS o SSH según prefieras).*

### Paso 3: Instalar la Extensión Copilot

Una vez autenticado, instala la extensión oficial:

```bash
gh extension install github/gh-copilot
```

### Paso 4: Actualizar (Opcional pero recomendado)

Si ya lo tenías instalado, asegúrate de tener la última versión:

```bash
gh extension upgrade gh-copilot
```

## Uso Básico

Copilot CLI tiene dos modos principales: `suggest` (sugerir comandos) y `explain` (explicar comandos).

### 1. Sugerir Comandos (`gh copilot suggest`)

Pídele que genere un comando complejo por ti:

```bash
gh copilot suggest "Lista todos los archivos PDF mayores a 10MB en la carpeta actual"
```

Copilot te ofrecerá:
- El comando sugerido.
- Una explicación de qué hace.
- La opción de copiarlo al portapapeles o ejecutarlo directamente.

### 2. Explicar Comandos (`gh copilot explain`)

¿No entiendes qué hace un comando críptico que encontraste en internet? Pregúntale a Copilot:

```bash
gh copilot explain "tar -xzvf archivo.tar.gz -C /tmp"
```

## Configuración de Alias (Power User)

Escribir `gh copilot suggest` cada vez es tedioso. Configura alias cortos (`??` para sugerir, `wt` para explicar).

**En PowerShell / Bash / Zsh:**

Ejecuta este comando para ver las instrucciones de configuración automática para tu shell:

```bash
gh copilot alias -- console
```

Copia y pega el bloque de código que te proporcione en tu archivo de perfil (`.bashrc`, `.zshrc`, `$PROFILE`).

**Ejemplo de uso con alias:**

```bash
# Sugerir
?? "Elimina todas las ramas de git excepto main"

# Explicar
wt "git reset --hard HEAD~1"
```

## Solución de Problemas

**Error: "You are not subscribed to GitHub Copilot"**
- Verifica que tu cuenta tenga una suscripción activa en [GitHub Settings](https://github.com/settings/copilot).
- Asegúrate de haber hecho login con la cuenta correcta: `gh auth status`.

**Error: "Extension not found"**
- Verifica tu conexión a internet.
- Actualiza `gh` a la última versión.

## Uso en el Curso

Utilizaremos Copilot CLI para:
1. **Recordar sintaxis de Git:** "Cómo deshacer el último commit sin borrar cambios".
2. **Generar comandos de testing:** "Ejecuta solo los tests que contengan 'login' con pytest".
3. **Manejo de archivos:** "Busca recursivamente archivos .log y bórralos".
