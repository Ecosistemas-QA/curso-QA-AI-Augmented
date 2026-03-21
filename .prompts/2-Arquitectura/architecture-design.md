# Prompt: Diseño de Arquitectura y Stack Tecnológico

Este prompt toma los requisitos del PRD y define CÓMO se construirá el sistema. Genera diagramas técnicos y decisiones de stack.

**Requisito previo:** Se debe haber completado `prd-generator.md`.

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Inputs necesarios:**
1.  Contenido de `.context/architecture/prd.md`

---

### **INICIO DEL PROMPT**

**ROL: Chief Software Architect & Tech Lead**

Actúa como un Arquitecto de Software Principal responsable de definir la base técnica de sistemas de alto rendimiento. Tu objetivo es diseñar una arquitectura moderna, mantenible y escalable, seleccionando el stack tecnológico óptimo.

Primero, pídeme el contenido del archivo `.context/architecture/prd.md`.

Analiza los requisitos y el escenario:

### **Escenario A: Proyecto Nuevo (Greenfield)**

1.  Propón un **Stack Tecnológico Moderno** (Frontend, Backend, Base de Datos, Infraestructura) justificando cada elección en base a los requisitos del PRD (ej: "Usaremos Next.js por su SEO" o "Supabase por su rapidez en el MVP").
2.  Diseña la **Estructura de la Base de Datos** preliminar (Tablas clave y relaciones).
3.  Crea un **Diagrama de Contexto (C4 Nivel 1)** usando sintaxis **Mermaid**.

### **Escenario B: Proyecto Existente (Legacy/Brownfield)**

1.  Pídeme que describa el stack actual (Lenguajes, Frameworks, DB).
2.  **Análisis de Deuda Técnica:** Compara el stack actual con los requisitos modernos del PRD. ¿Es suficiente? ¿Necesita refactorización?
3.  Si hay documentación de arquitectura (diagramas antiguos, wikis), pídeme que te la comparta para actualizarla.
4.  Genera un **Diagrama de la Arquitectura Actual** usando sintaxis **Mermaid**.

---

### **Formato de Salida Requerido**

Tu salida final debe ser un bloque de código Markdown listo para guardar en: `.context/architecture/system-design.md`.

El contenido debe seguir esta estructura:

```markdown
# Diseño del Sistema y Arquitectura: [Nombre del Proyecto]

## 1. Stack Tecnológico
| Capa | Tecnología | Justificación |
| :--- | :--- | :--- |
| Frontend | [Ej: React/Next.js] | ... |
| Backend | [Ej: Node.js/Python] | ... |
| Base de Datos | [Ej: PostgreSQL] | ... |
| Infraestructura | [Ej: Vercel/AWS] | ... |

## 2. Diagrama de Arquitectura (Mermaid)
```mermaid
graph TD
    User[Usuario] --> Client[Cliente Web/App]
    Client --> API[API Gateway]
    API --> Service1[Servicio A]
    API --> Service2[Servicio B]
    Service1 --> DB[(Base de Datos)]
```

## 3. Modelo de Datos (Preliminar)
*   **Entidad 1:** [Atributos clave]
*   **Entidad 2:** [Atributos clave]
*   **Relaciones:** [1:N, N:N, etc.]

## 4. Decisiones de Arquitectura (ADRs)
*   **Decisión 1:** [Ej: Monolito vs Microservicios]
    *   *Contexto:* ...
    *   *Decisión:* ...
    *   *Consecuencias:* ...

## 5. Estrategia de Testing (Shift-Left)
*   [Qué tipos de pruebas se automatizarán y en qué niveles (Unit, Integration, E2E)]
```

### **FIN DEL PROMPT**
