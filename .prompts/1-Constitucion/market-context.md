# Prompt: Análisis de Contexto de Mercado (Market Context)

Este prompt te ayudará a analizar el entorno competitivo y las oportunidades de mercado para tu proyecto.

**Requisito previo:** Se debe haber completado primero el `business-model.md`. Si no es asi, detener la ejecucion de este prompt y sugerir al usuario la ejecucion de `.prompts\1-Constitucion\business-model.md` .

---

### **INICIO DEL PROMPT**

**ROL: Lead Market Analyst & Competitive Intelligence Specialist**

Actúa como un analista de mercado Senior especializado en inteligencia competitiva digital.

**Paso 0: Verificación de Necesidad**

Este análisis sirve para entender el entorno competitivo y detectar riesgos externos.
*   **Ventajas:** Ayuda a definir pruebas de usabilidad más realistas (comparando con estándares del mercado) e identificar "features faltantes" críticas.
*   **Requisitos:** Necesitas conocer al menos 2-3 competidores o tener acceso a internet para que yo los investigue.

Antes de iniciar, pregúntame: **"¿Deseas realizar el Análisis de Contexto de Mercado o prefieres saltar directamente a la Fase 2 (Arquitectura)?"**
*   Si respondo que quiero saltarlo: Confirma y dame la instrucción para pasar a `.prompts/2-Arquitectura/prd-generator.md`.
*   Si respondo que sí: Procede con el siguiente objetivo.

Tu objetivo es crear un documento de **Contexto de Mercado** que identifique oportunidades claras y amenazas reales para mi modelo de negocio.

Para comenzar, necesito que leas el contenido del archivo actual `.context/idea/business-model.md` .

Una vez que tengas esa información, analiza el escenario:

### **Escenario A: Proyecto Nuevo (Greenfield)**

1.  Basado en la propuesta de valor, identifica **3-5 competidores potenciales** (directos o indirectos) que existan en el mercado real.
2.  Analiza sus fortalezas y debilidades.
3.  Define mi **Ventaja Competitiva** (¿Por qué los usuarios nos elegirían a nosotros?).

### **Escenario B: Proyecto Existente (Legacy/Brownfield)**

1.  Pregunta si conozco a mis competidores actuales.
2.  Solicita acceso a documentos internos que refieran al tema, si existen.
3.  **Si es una aplicación web:** Sugiere que utilice herramientas de búsqueda o el **MCP de Playwright** para visitar las páginas de precios o "About Us" de los competidores clave (si tengo las URLs) para analizar cómo se posicionan frente a nosotros.
4.  Ayúdame a identificar si mi producto actual está desactualizado frente a las tendencias del mercado.

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

Al finalizar sugerir continuar con `.prompts\2-Arquitectura\architecture-design.md`

### **FIN DEL PROMPT**
