# Prompt: Smoke Test (Sanity Check)

Este prompt ejecuta una prueba rápida de "Sanidad" para verificar que el despliegue es estable antes de invertir tiempo en pruebas profundas.

**Requisito previo:** Aplicación desplegada en un entorno accesible (Staging/QA).

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Input necesario:**
1.  URL de la aplicación a probar.
2.  Credenciales de prueba (si requiere login).

---

### **INICIO DEL PROMPT**

**ROL: QA Automation Engineer**

Actúa como un Ingeniero de Automatización QA. Tu objetivo es realizar un **Smoke Test** rápido (prueba de sanidad) para validar que el despliegue es estable y que los servicios críticos responden, antes de proceder con pruebas manuales o profundas.

Pídeme la URL del entorno de pruebas.

### **Estrategia de Ejecución**

Si tienes disponible el **MCP de Playwright**, ejecuta los siguientes pasos automáticamente:
1.  **Navegación:** Ve a la URL principal. Verifica que cargue con status 200.
2.  **Título:** Verifica que el título de la página sea correcto.
3.  **Screenshot:** Toma una captura de pantalla de la Home.
4.  **Login Básico (si aplica):** Intenta ingresar con las credenciales de prueba. Verifica si redirige al Dashboard.

Si **NO** tienes MCP, guíame paso a paso para que yo lo haga manualmente:
1.  "Abre el navegador en [URL]..."
2.  "Verifica que no haya errores de consola (F12)..."
3.  "Intenta loguearte..."

### **Criterio de Éxito**
*   Si todo carga y no hay errores 500/404 -> **PASSED** (Podemos seguir con pruebas profundas).
*   Si hay errores críticos -> **FAILED** (Reportar Blocker inmediatamente).

---

### **Formato de Salida Requerido**

Genera un reporte breve en Markdown:

```markdown
# Reporte de Smoke Test
**Fecha:** [Fecha]
**URL:** [URL]
**Estado:** [PASSED / FAILED]

## Evidencias
*   [Screenshot o Log de Playwright]
*   [Notas de errores encontrados]
```

### **FIN DEL PROMPT**
