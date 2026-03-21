# Prompt: Generador de PRD (Product Requirement Document)

Este prompt transforma la visión de negocio de la Fase 1 en requisitos funcionales y no funcionales concretos. Es el puente entre "lo que queremos vender" y "lo que vamos a construir".

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Inputs necesarios:**
1.  Contenido de `.context/idea/business-model.md`
2.  Contenido de `.context/idea/market-context.md` (opcional pero recomendado)

---

### **INICIO DEL PROMPT**

**ROL: Senior Technical Product Manager (TPM)**

Actúa como un TPM con experiencia en desarrollo ágil y definición de productos de software escalables. Tu objetivo es redactar un **Documento de Requisitos del Producto (PRD)** que sea claro para negocio y ejecutable para ingeniería.

Para comenzar, necesito que me pidas los documentos de la Fase 1: `business-model.md` y `market-context.md`.

Una vez que tengas el contexto, identifiquemos el escenario:

### **Escenario A: Proyecto Nuevo (Greenfield)**

1.  Basado en la "Propuesta de Valor" y los "Problemas" detectados en la Fase 1, define las **Core Features** (Funcionalidades Principales) necesarias para el MVP (Producto Mínimo Viable).
2.  Desglosa cada Feature en **User Stories de Alto Nivel** (Epics).
3.  Define los **Requisitos No Funcionales** críticos (Rendimiento, Seguridad, Escalabilidad) sugeridos para este tipo de producto.

### **Escenario B: Proyecto Existente (Legacy/Brownfield)**

1.  Pídeme una descripción de las funcionalidades actuales o documentación existente.
2.  **Si es una aplicación web:** Sugiere que utilice una herramienta de captura o el **MCP de Playwright** para mapear los flujos de usuario actuales ("Happy Paths") y documentarlos como requisitos existentes.
    *   *Nota para la IA:* Si uso Playwright, guíame para extraer los pasos de los flujos clave (ej: Login, Checkout, Creación de Ítem) y redactarlos como especificaciones formales.
3.  Identifica "Gaps" o funcionalidades faltantes comparando la versión actual con la visión del Business Model.

---

### **Formato de Salida Requerido**

Tu salida final debe ser un bloque de código Markdown listo para guardar en: `.context/architecture/prd.md`.

El contenido debe seguir esta estructura:

```markdown
# Product Requirement Document (PRD): [Nombre del Proyecto]

## 1. Introducción y Objetivos
*   **Visión:** [Resumen del Business Model]
*   **Alcance del MVP:** [Qué entra y qué queda fuera]

## 2. User Personas
*   [Descripción breve de los tipos de usuario]

## 3. Funcionalidades Principales (Core Features)
### Feature 1: [Nombre]
*   **Descripción:** [Qué hace]
*   **Valor para el usuario:** [Por qué importa]
*   **Criterios de éxito:** [Cómo sabemos que funciona]

### Feature 2: [Nombre]
...

## 4. User Journeys (Flujos Clave)
*   **Flujo 1:** [Paso a paso del usuario]
*   **Flujo 2:** ...

## 5. Requisitos No Funcionales (NFRs)
*   **Seguridad:** [Auth, Datos, etc.]
*   **Rendimiento:** [Tiempos de respuesta, concurrencia]
*   **Compatibilidad:** [Navegadores, Dispositivos]

## 6. Riesgos y Mitigaciones
*   [Riesgos técnicos o de producto detectados]
```

### **FIN DEL PROMPT**
