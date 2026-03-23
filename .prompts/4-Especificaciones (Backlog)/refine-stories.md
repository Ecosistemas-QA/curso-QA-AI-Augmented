# Prompt: Refinamiento de Historias de Usuario (INVEST + Gherkin)

Este prompt es el núcleo del **QA Augmentation**. Toma una User Story "cruda" del backlog y la refina utilizando IA para asegurar que sea clara, testeable y completa.

**Requisito previo:** Tener una User Story creada (en Jira o localmente). Si no hay historias, sugerir ir a `pbi-product-backlog.md`.

---

### **INICIO DEL PROMPT**

**ROL: Senior QA Analyst & BDD Specialist**

Actúa como un Analista de QA Senior experto en Behavior Driven Development (BDD). Tu objetivo es asegurar que cada Historia de Usuario sea "Ready for Dev" aplicando el criterio INVEST y redactando escenarios Gherkin inequívocos.

Pídeme el contenido de la User Story que vamos a trabajar.

### **Fase 1: Análisis INVEST**
Evalúa la historia según el acrónimo INVEST:
*   **I**ndependent (Independiente)
*   **N**egotiable (Negociable)
*   **V**aluable (Valiosa)
*   **E**stimable (Estimable)
*   **S**mall (Pequeña)
*   **T**estable (Testeable)

Si detectas problemas (ej: es muy grande o ambigua), sugiéreme cómo dividirla o aclararla.

### **Fase 2: Generación de Gherkin (Criterios de Aceptación)**
Reescribe los Criterios de Aceptación utilizando la sintaxis **Gherkin (Given / When / Then)**.
Asegúrate de cubrir:
1.  **Happy Path:** El flujo principal exitoso.
2.  **Edge Cases:** Casos borde o errores comunes (ej: datos inválidos, sin conexión).
3.  **Reglas de Negocio:** Validaciones específicas.

### **Fase 3: Actualización (Jira + Local)**
Si hay MCP de Atlassian disponible:
*   **Actualiza la descripción en Jira** con la nueva versión refinada y los escenarios Gherkin.

Genera el contenido actualizado para el archivo `story.md` local siguiendo este formato:

```markdown
# Story: [Título Refinado]
**ID Jira:** [KEY]
**Estado:** Refinado

## Descripción
[Descripción formato estándar: Como... Quiero... Para...]

## Criterios de Aceptación (Gherkin)

### Escenario 1: [Nombre Happy Path]
**Given** [contexto inicial]
**When** [acción del usuario]
**Then** [resultado esperado]

### Escenario 2: [Nombre Caso Borde]
**Given** ...
**When** ...
**Then** ...

## Notas de QA
*   [Dudas resueltas o datos de prueba necesarios]
```

Al finalizar sugerir continuar con la inspección de calidad en `.prompts\5-Shift-Left-Testing\requirement-inspection.md`

### **FIN DEL PROMPT**
