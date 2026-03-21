# Guía de Instalación de Gemini CLI

## Descripción
Gemini CLI es la herramienta de línea de comandos oficial de Google para interactuar con los modelos de IA Gemini. Permite ejecutar prompts, mantener conversaciones y trabajar con archivos directamente desde la terminal.

## Requisitos Previos

- **Node.js**: Versión 18 o superior
- **npm**: Gestor de paquetes de Node.js (incluido con Node.js)
- **Cuenta de Google Cloud**: Para obtener la API key de Gemini

## Instalación

### Paso 1: Verificar Node.js y npm

Verifica que tienes Node.js instalado:

```bash
node --version
npm --version
```

Si no tienes Node.js instalado, descárgalo desde [nodejs.org](https://nodejs.org/)

### Paso 2: Instalar Gemini CLI

Instala el paquete globalmente usando npm:

```bash
npm install -g @google/gemini-cli
```

### Paso 3: Verificar la instalación

Comprueba que la instalación fue exitosa:

```bash
gemini --version
```

### Paso 4: Configurar la API Key

1. Obtén tu API key desde [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Configura la variable de entorno:

**En Windows (PowerShell):**
```powershell
$env:GEMINI_API_KEY = "tu-api-key-aqui"
```

**En Windows (Command Prompt):**
```cmd
set GEMINI_API_KEY=tu-api-key-aqui
```

**En Linux/Mac:**
```bash
export GEMINI_API_KEY="tu-api-key-aqui"
```

Para hacerlo permanente, agrega la variable a tu archivo de configuración del shell (`.bashrc`, `.zshrc`, etc.)

## Uso Básico

### Ejecutar un prompt simple
```bash
gemini "Explica qué es la inteligencia artificial"
```

### Modo interactivo
```bash
gemini
```

### Trabajar con archivos
```bash
gemini -f archivo.txt "Resume este documento"
```

## Problemas Comunes y Soluciones

### ❌ Error: Cannot find package 'tinycolor2'

**Síntoma:**
```
Error [ERR_MODULE_NOT_FOUND]: Cannot find package 'tinycolor2' imported from 
C:\Users\admin\AppData\Roaming\npm\node_modules\@google\gemini-cli\dist\src\ui\themes\theme.js
```

**Causa:**
Este error ocurre cuando la instalación global de `@google/gemini-cli` tiene dependencias faltantes o corruptas. Puede suceder por:
- Interrupciones durante la instalación inicial
- Actualizaciones incompletas de npm
- Problemas de caché de npm
- Conflictos de versiones de paquetes

**Solución:**

1. **Reinstalar el paquete globalmente:**
   ```bash
   npm install -g @google/gemini-cli
   ```

2. **Si el problema persiste, limpiar caché y reinstalar:**
   ```bash
   npm cache clean --force
   npm uninstall -g @google/gemini-cli
   npm install -g @google/gemini-cli
   ```

3. **Verificar que funciona:**
   ```bash
   gemini --version
   ```

### ❌ Error: API key not found

**Síntoma:**
```
Error: GEMINI_API_KEY environment variable not set
```

**Solución:**
Asegúrate de haber configurado la variable de entorno `GEMINI_API_KEY` correctamente (ver Paso 4 de instalación).

### ❌ Error: Permission denied

**Síntoma:**
```
Error: EACCES: permission denied
```

**Solución en Windows:**
Ejecuta PowerShell o Command Prompt como Administrador.

**Solución en Linux/Mac:**
```bash
sudo npm install -g @google/gemini-cli
```

### ❌ Gemini CLI no responde o es muy lento

**Causas posibles:**
- Conexión a internet lenta
- Límites de rate de la API
- Problemas con el servidor de Gemini

**Soluciones:**
1. Verifica tu conexión a internet
2. Espera unos minutos y vuelve a intentar
3. Revisa el estado de los servicios de Google Cloud

## Comandos Útiles

### Listar modelos disponibles
```bash
gemini --list-models
```

### Usar un modelo específico
```bash
gemini -m gemini-pro "Tu pregunta aquí"
```

### Guardar la salida en un archivo
```bash
gemini "Genera un ejemplo de código Python" > output.txt
```

### Modo verbose (para debugging)
```bash
gemini --verbose "Tu pregunta"
```

## Actualización

Para actualizar Gemini CLI a la última versión:

```bash
npm update -g @google/gemini-cli
```

## Desinstalación

Si necesitas desinstalar Gemini CLI:

```bash
npm uninstall -g @google/gemini-cli
```

## Recursos Adicionales

- **Documentación oficial**: [Google AI for Developers](https://ai.google.dev/)
- **Repositorio GitHub**: [@google/generative-ai-js](https://github.com/google/generative-ai-js)
- **API Reference**: [Gemini API Docs](https://ai.google.dev/api)
- **Community**: [Google AI Discord](https://discord.gg/google-ai)

## Notas de Versión

- **Fecha de este documento**: Marzo 2026
- **Versión de Node.js recomendada**: v22.x o superior
- **Última actualización de troubleshooting**: Incluye solución para error de dependencias faltantes (tinycolor2)

---

## Consejos para el Curso

1. **Siempre verifica la instalación** antes de comenzar a trabajar
2. **Guarda tu API key de forma segura** - nunca la compartas públicamente
3. **Experimenta con diferentes modelos** para entender sus capacidades
4. **Usa el modo verbose** cuando necesites hacer debugging
5. **Mantén actualizado** el CLI para tener las últimas características

## Anexo: Troubleshooting Avanzado

### Verificar la instalación global de npm

```bash
npm list -g @google/gemini-cli
```

### Ver la ruta de instalación

```bash
npm root -g
```

### Reinstalación completa (Windows)

```powershell
# Desinstalar
npm uninstall -g @google/gemini-cli

# Limpiar caché
npm cache clean --force

# Reinstalar
npm install -g @google/gemini-cli

# Verificar
gemini --version
```

---

**¿Encontraste algún otro problema?** Documenta el error y la solución para ayudar a otros estudiantes del curso.
