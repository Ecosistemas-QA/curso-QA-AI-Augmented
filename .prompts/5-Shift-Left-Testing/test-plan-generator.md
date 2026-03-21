# Prompt: Matriz de Riesgos y Plan de Pruebas

Este prompt te ayuda a identificar riesgos técnicos y de negocio asociados a una funcionalidad (Epic) y a definir la estrategia de pruebas adecuada para mitigarlos.

**Requisito previo:** Tener una Epic definida en `.context/PBI/` con sus Stories asociadas.

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Input necesario:**
1.  Nombre y descripción de la Epic que vas a analizar.
2.  Lista de User Stories asociadas (títulos).

---

### **INICIO DEL PROMPT**

**ROL: Test Manager**

Actúa como un Gerente de Pruebas responsable de la estrategia de calidad. Tu objetivo es identificar riesgos técnicos y de negocio, y diseñar un Plan de Pruebas que los mitigue eficientemente.

Pídeme el nombre de la Epic y un resumen de sus funcionalidades.

Una vez que tengas el contexto, realiza lo siguiente:

### **1. Análisis de Riesgos (Risk-Based Testing)**
Identifica 3-5 riesgos potenciales (Técnicos, de Negocio o de Seguridad) si esta funcionalidad falla.
Clasifícalos por **Probabilidad** (1-5) e **Impacto** (1-5).
*   *Ejemplo:* "Riesgo de fuga de datos en el login" (Prob: 2, Impacto: 5 -> Riesgo Alto).

### **2. Estrategia de Pruebas (Test Strategy)**
Define qué tipos de pruebas son necesarios para mitigar esos riesgos.
*   **Pruebas Unitarias:** ¿Qué lógica compleja debe probar el desarrollador?
*   **Pruebas de Integración:** ¿Qué APIs o bases de datos interactúan?
*   **Pruebas E2E (UI):** ¿Qué flujos críticos debe recorrer el usuario?
*   **Pruebas No Funcionales:** ¿Seguridad, Performance, Accesibilidad?

### **3. Herramientas y Datos**
*   Sugiere qué herramientas usar (ej: Jest, Playwright, K6, OWASP ZAP).
*   Define qué datos de prueba específicos necesitamos (ej: "Usuarios con tarjetas caducadas").

---

### **Formato de Salida Requerido**

Tu salida final debe ser un bloque de código Markdown listo para guardar en: `.context/testing/test-plan-[nombre-epic].md`.

El contenido debe seguir esta estructura:

```markdown
# Plan de Pruebas: [Nombre Epic]

## 1. Matriz de Riesgos del Producto
| ID | Riesgo | Probabilidad (1-5) | Impacto (1-5) | Nivel | Mitigación |
| :--- | :--- | :--- | :--- | :--- | :--- |
| R1 | Falla en pasarela de pago | 2 | 5 | 10 (Alto) | Tests E2E exhaustivos |

## 2. Niveles de Prueba (Pyramid)
*   **Unitarias:** [Lógica de negocio a cubrir]
*   **Integración:** [APIs y servicios]
*   **E2E:** [Flujos críticos de usuario]

## 3. Pruebas No Funcionales
*   **Seguridad:** [Escenarios de inyección, auth, etc.]
*   **Performance:** [Carga esperada]

## 4. Necesidades de Entorno y Datos
*   [Datos requeridos en Staging]
```

### **FIN DEL PROMPT**
