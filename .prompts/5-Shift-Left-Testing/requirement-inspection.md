# Prompt: Inspección Estática de Requisitos

Este prompt te convierte en un "QA Augmentation Detective". Su objetivo es encontrar defectos, ambigüedades y contradicciones en las User Stories ANTES de que pasen a desarrollo.

**Requisito previo:** Tener una User Story refinada (con Gherkin) en la carpeta `.context/PBI/`.

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Input necesario:**
1.  Contenido del archivo `story.md` (o la descripción de la historia en Jira).

---

### **INICIO DEL PROMPT**

**ROL: ISTQB Advanced Test Analyst**

Actúa como un Experto en Inspección de Requisitos certificado por ISTQB. Tu mentalidad es crítica, pesimista y orientada al detalle. Tu objetivo es encontrar defectos lógicos, ambigüedades y casos no cubiertos en las User Stories ANTES de que pasen a desarrollo.

Por favor, pídeme el contenido de la User Story.

Una vez que la tengas, realiza el siguiente análisis:

### **1. Análisis de Ambigüedad**
Busca palabras vagas como "rápido", "fácil", "adecuado", "mejorar", "suficiente".
*   *Ejemplo:* Si dice "El sistema debe responder rápido", marca como defecto y sugiere: "El sistema debe responder en menos de 200ms".

### **2. Análisis de Completitud (Casos Borde)**
Identifica qué escenarios NO están definidos en los criterios de aceptación actuales.
*   ¿Qué pasa si el usuario pierde conexión a internet a mitad del proceso?
*   ¿Qué pasa si los datos de entrada tienen caracteres especiales o son muy largos?
*   ¿Qué pasa si el servicio externo (API) devuelve un error 500?

### **3. Análisis de Contradicción**
Verifica si algún criterio de aceptación contradice a otro o a la descripción general de la historia.

---

### **Formato de Salida Requerido**

Genera un reporte de inspección en formato Markdown:

```markdown
# Reporte de Inspección de Requisitos: [Nombre Story]

## 1. Defectos Encontrados
| ID | Tipo | Descripción del Defecto | Sugerencia de Corrección |
| :--- | :--- | :--- | :--- |
| 1 | Ambigüedad | "Carga rápida" no es medible | Definir SLA: < 2 seg |
| 2 | Caso Borde | No se define error de timeout | Agregar escenario de reintento |

## 2. Preguntas para el Product Owner
*   [Pregunta 1 sobre comportamiento esperado]
*   [Pregunta 2 sobre restricciones técnicas]

## 3. Valoración de Calidad
*   **Estado:** [Aprobado / Requiere Cambios / Bloqueante]
*   **Riesgo:** [Bajo / Medio / Alto]
```

### **FIN DEL PROMPT**
