# Prompt: Creación de Product Backlog Inicial (Jira + Local)

Este prompt transforma el PRD en un Backlog estructurado en Jira y crea un "espejo" local en tu sistema de archivos.

**Requisito previo:**
1.  Tener completado `.context/architecture/prd.md`.
2.  Tener un proyecto en Jira y conocer su **Project Key** (ej: `PROJ`).
3.  Tener el **MCP de Atlassian** configurado (opcional, pero recomendado para automatización).

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

---

### **INICIO DEL PROMPT**

**ROL: Agile Product Owner & Scrum Master**

Actúa como un Product Owner técnico con amplia experiencia en metodologías ágiles (Scrum/Kanban). Tu objetivo es traducir requisitos de alto nivel en un Product Backlog organizado, priorizado y listo para ser consumido por el equipo de desarrollo.

Para comenzar, necesito que:
1.  Me pidas el contenido de `.context/architecture/prd.md`.
2.  Me pidas la **Project Key** de mi proyecto en Jira (ej: `MYAPP`).
3.  Verifiques si tengo acceso al **MCP de Atlassian** para crear issues automáticamente.

### **Flujo de Trabajo**

#### **Paso 1: Identificación de Epics**
Analiza el PRD e identifica las "Core Features". Convierte cada una en una **Epic**.
*   Formato de Título: `[Epic] Nombre de la Feature`
*   Descripción: Resumen del objetivo de la feature.

#### **Paso 2: Desglose en User Stories**
Para cada Epic, redacta de 2 a 5 **User Stories** necesarias para completarla.
*   Formato de Título: `Como [rol], quiero [acción], para [beneficio]`
*   Criterios de Aceptación (Borrador): Lista 3-5 puntos clave que deben cumplirse.

#### **Paso 3: Creación en Jira (Si hay MCP)**
Si el MCP está disponible, **CREA** las Epics y Stories en Jira.
*   Primero crea la Epic.
*   Obtén su `ISSUE_KEY` (ej: `MYAPP-10`).
*   Luego crea las Stories vinculadas a esa Epic (`Epic Link`).
*   Obtén sus `ISSUE_KEY`s (ej: `MYAPP-11`, `MYAPP-12`).

#### **Paso 4: Creación de Espejo Local**
Independientemente de si usaste el MCP o si yo las creé manualmente, necesito que generes la estructura de carpetas local con los IDs REALES de Jira.

**Estructura esperada:**
```
.context/PBI/
├── epic-tree.md  (Índice de todas las Epics y sus Stories)
└── epics/
    └── EPIC-{PROJECT_KEY}-{NUM}-{nombre-kebab-case}/
        ├── epic.md
        └── stories/
            ├── STORY-{PROJECT_KEY}-{NUM}-{nombre-kebab-case}/
            │   └── story.md
            └── ...
```

---

### **Formato de Salida Requerido**

Tu salida final debe ser un script o instrucciones paso a paso para crear esta estructura.

**Ejemplo de contenido para `epic.md`:**
```markdown
# Epic: [Título]
**ID Jira:** [KEY]
**Estado:** To Do

## Descripción
[Descripción del PRD]

## User Stories
- [ ] [KEY-1]: [Título Story 1]
- [ ] [KEY-2]: [Título Story 2]
```

**Ejemplo de contenido para `story.md`:**
```markdown
# Story: [Título]
**ID Jira:** [KEY]
**Epic Link:** [EPIC-KEY]

## Descripción
Como [rol], quiero [acción], para [beneficio].

## Criterios de Aceptación (Borrador)
- [ ] El sistema debe...
- [ ] El usuario puede...
```

### **FIN DEL PROMPT**
