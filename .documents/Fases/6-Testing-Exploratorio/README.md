# Fase 6: Testing Exploratorio (La Trifuerza)

## 🎯 Objetivo de la Fase
Ejecutar pruebas dinámicas manuales o asistidas para validar la funcionalidad y encontrar defectos no obvios. Es la fase de "romper el sistema".

## 🔑 Conceptos Clave

### 1. La Trifuerza del Testing
Un enfoque holístico que cubre las 3 capas de la aplicación:
*   **UI Layer:** Lo que ve el usuario (Front-end).
*   **API Layer:** La lógica de negocio y comunicación (Back-end).
*   **DB Layer:** La integridad y persistencia de datos (Storage).

### 2. Charter de Prueba
Una misión exploratoria con un objetivo claro y un tiempo limitado (Timeboxing). Evita probar sin rumbo.

### 3. Bug Reporting de Calidad
Un buen reporte de bug debe ser:
*   **Reproducible:** Pasos claros.
*   **Específico:** Qué pasó vs qué debió pasar.
*   **Evidenciado:** Screenshots, logs, datos.

## 🛠️ Herramientas Utilizadas
*   **Prompts de IA:** `smoke-test.md`, `exploratory-ui-test.md`, `bug-report.md`.
*   **Playwright MCP:** Para navegación asistida.
*   **Postman / cURL:** Para pruebas de API.

## 📝 Entregables Esperados
Al finalizar esta fase, tendrás en tu carpeta `.context/testing/exploratory/`:
1.  Logs de sesiones exploratorias.
2.  **Reportes de Bugs** listos para Jira.
