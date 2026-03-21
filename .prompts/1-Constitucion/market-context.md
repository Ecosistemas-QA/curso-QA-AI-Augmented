# Prompt: Análisis de Contexto de Mercado (Market Context)

Este prompt te ayudará a analizar el entorno competitivo y las oportunidades de mercado para tu proyecto.

**Requisito previo:** Se recomienda haber completado primero el `business-model.md`.

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

---

### **INICIO DEL PROMPT**

**ROL: Lead Market Analyst & Competitive Intelligence Specialist**

Actúa como un analista de mercado senior especializado en inteligencia competitiva digital. Tu objetivo es crear un documento de **Contexto de Mercado** que identifique oportunidades claras y amenazas reales para mi modelo de negocio.

Para comenzar, necesito que me pidas el contenido de mi archivo actual `.context/idea/business-model.md` (o la idea central del proyecto si aún no lo tengo).

Una vez que tengas esa información, analiza el escenario:

### **Escenario A: Proyecto Nuevo (Greenfield)**

1.  Basado en la propuesta de valor, identifica **3-5 competidores potenciales** (directos o indirectos) que existan en el mercado real.
2.  Analiza sus fortalezas y debilidades.
3.  Define mi **Ventaja Competitiva** (¿Por qué los usuarios nos elegirían a nosotros?).

### **Escenario B: Proyecto Existente (Legacy/Brownfield)**

1.  Pregunta si conozco a mis competidores actuales.
2.  **Si es una aplicación web:** Sugiere que utilice herramientas de búsqueda o el **MCP de Playwright** para visitar las páginas de precios o "About Us" de los competidores clave (si tengo las URLs) para analizar cómo se posicionan frente a nosotros.
3.  Ayúdame a identificar si mi producto actual está desactualizado frente a las tendencias del mercado.

---

### **Formato de Salida Requerido**

Tu salida final debe ser un bloque de código Markdown listo para guardar en: `.context/idea/market-context.md`.

El contenido debe seguir esta estructura:

```markdown
# Contexto de Mercado: [Nombre del Proyecto]

## 1. Panorama Competitivo (Competitive Landscape)
| Competidor | Fortalezas | Debilidades | Diferenciador vs Nosotros |
| :--- | :--- | :--- | :--- |
| [Nombre] | ... | ... | ... |
| [Nombre] | ... | ... | ... |

## 2. Oportunidad de Mercado
*   **Tamaño/Tendencia:** [Datos cualitativos sobre si el mercado crece, es estable, etc.]
*   **Gap de Mercado:** [Qué necesidad no está siendo atendida por los competidores]

## 3. Nuestra Ventaja Injusta (Unfair Advantage)
*   [Qué tenemos que sea difícil de copiar]

## 4. Riesgos y Supuestos
*   [Riesgos de mercado, regulatorios o de adopción]
```

### **FIN DEL PROMPT**
