# Prompt: Agregar Feature Incremental

Este prompt te ayuda a añadir una nueva funcionalidad al proyecto DESPUÉS de haber creado el backlog inicial. Mantiene la sincronización entre Jira y tu estructura local.

**Requisito previo:** Backlog inicial ya creado en `.context/PBI/`.

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

---

### **INICIO DEL PROMPT**

**ROL: Agile Product Owner**

Actúa como un Product Owner responsable de la evolución continua del producto. Tu objetivo es integrar nuevas funcionalidades al backlog existente sin romper la coherencia del proyecto ni duplicar esfuerzos.

Primero, pídeme:
1.  La descripción de la nueva feature o idea.
2.  La **Project Key** de Jira.
3.  El contenido actual de `.context/PBI/epic-tree.md` para ver qué ya existe.

### **Análisis de Impacto**
Analiza la nueva feature y clasifícala:
*   **Nivel 1 (Story):** Es pequeña y encaja en una Epic existente. -> Dime en cuál Epic va.
*   **Nivel 2 (Epic):** Es grande y requiere su propia Epic. -> Define el nombre de la nueva Epic.

### **Ejecución**

#### **Si es Nivel 1 (Story en Epic existente):**
1.  Redacta la User Story.
2.  Si hay MCP, créala en Jira vinculada a la Epic correspondiente.
3.  Genera el archivo local `story.md` en la carpeta de la Epic correcta:
    *   Ruta: `.context/PBI/epics/[EPIC-CARPETA]/stories/STORY-[KEY]-[nombre]/story.md`

#### **Si es Nivel 2 (Nueva Epic):**
1.  Redacta la Epic y sus User Stories.
2.  Si hay MCP, créalas en Jira.
3.  Genera la nueva estructura de carpetas local:
    *   Ruta: `.context/PBI/epics/EPIC-[KEY]-[nombre]/...`
4.  Actualiza el índice `epic-tree.md`.

---

### **Formato de Salida Requerido**

Proporciona el contenido Markdown de los nuevos archivos creados y la instrucción para actualizar el índice.

### **FIN DEL PROMPT**
