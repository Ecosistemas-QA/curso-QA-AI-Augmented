# 🗺️ AI Project Map: QA AI-Augmented Course

## 1. Misión y Propósito
Este repositorio es la base de un curso diseñado para transformar a **QA Manuales** en **QA Augmented Specialists**. El enfoque es el **Context Engineering**: usar la IA como un orquestador técnico que interactúa con herramientas de desarrollo (CLI, Git, Jira, DBs) a través de protocolos **MCP**.

## 2. Estructura de Archivos (Arquitectura de Contexto)

```text
.
├── .prompts/               # Librería de "Cerebros" (Fases F1-F7)
├── .context/               # Memoria de trabajo (Outputs de la IA)
├── .guides/                # Manuales técnicos (Git, LLMs, Setup)
├── .documents/             # Base de conocimiento teórica (READMEs humanos)
├── README.md               # Portada y guía de inicio
└── TODO.md                 # Roadmap interno y definiciones pendientes
```

## 3. Lógica de las Fases (The Workflow)

El curso sigue un flujo lineal y lógico donde cada paso alimenta al siguiente:

1.  **F1 - Constitución:** Define el negocio (`business-model.md`) y el mercado (`market-context.md`).
2.  **F2 - Arquitectura:** Genera el `prd-generator.md` y el `architecture-design.md` (incluye diseño de APIs y Diagramas Mermaid).
3.  **F3 - Infraestructura:** Mapea el entorno técnico. Matriz de componentes (Frontend, API, DB) y estrategia de datos.
4.  **F4 - Especificaciones:** Gestión de Backlog en Jira (Jira-First) y refinamiento BDD/Gherkin.
5.  **F5 - Shift-Left Testing:** Inspección estática de requisitos y corrección proactiva en la fuente. Análisis de Riesgos.
6.  **F6 - Testing Exploratorio:** Ejecución de la **"Trifuerza"** (UI, API, DB) asistida por MCPs (Playwright, Postman, SQL).
7.  **F7 - Documentación CPs:** Formalización de casos de prueba, cálculo de ROI de automatización y soporte para Xray.

## 4. Estándares Técnicos para la IA (System Prompting)

Todos los prompts en `.prompts/` siguen estos principios de optimización:

*   **Identidad (Role-Based):** Cada prompt inicia con un `ROL:` específico (Senior PM, Chief Architect, DevOps Lead, Test Manager, etc.).
*   **Encadenamiento (Chaining):** Al finalizar, cada prompt sugiere explícitamente el archivo del siguiente paso.
*   **Validación de Pre-requisitos:** Los prompts verifican la existencia del contexto anterior antes de ejecutar (Smart Logic).
*   **Clean Context:** Se han eliminado todas las instrucciones de "copia y pega". El flujo está diseñado para lectura de archivo directa.
*   **Enterprise Language:** Se ha eliminado el término "MVP" en favor de "Release Objetivo" o "Versión 1.0".

## 5. Configuración de Entorno y Git

*   **Terminal:** Optimizada para **Warp** (Warp AI / Blocks).
*   **Git Sync:** El repositorio local está configurado con un remoto `origin` que realiza un **Multi-Push** a dos destinos:
    1.  `https://github.com/Ecosistemas-QA/curso-QA-AI-Augmented.git`
    2.  `https://github.com/jlb984/curso-QA-AI-Augmented.git`
*   **Autenticación:** Uso de **Personal Access Tokens (PAT)** inyectados en las URLs de los remotos para evitar conflictos de identidad.

## 6. Estado Actual del Proyecto (Marzo 2026)

*   **Completado:** Fases 1, 2 y 3 (Refinadas, sincronizadas y commiteadas).
*   **Pendiente de Commitear:** Fases 4, 5, 6 y 7 (Ya están escritas y optimizadas en local).
*   **Definiciones Pendientes (`TODO.md`):** Estrategia de Base de Datos "Enterprise" universal para MCP.
