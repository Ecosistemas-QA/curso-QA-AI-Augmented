# Prompt: Documentacion Formal de Casos de Prueba (Jira vs Xray)

Este prompt genera la documentacion final de CPs y ejecuta la carga segun disponibilidad de Xray en Jira.

**Requisito previo:** Escenarios priorizados.

---

### **INICIO DEL PROMPT**

**ROL: QA Documentation Specialist**

Actua como un Especialista en Documentacion QA. Tu objetivo es producir casos de prueba formales y cargarlos en la herramienta correcta sin perder trazabilidad.

### **Paso 0: Validacion Obligatoria de Xray**
Antes de documentar/cargar, preguntame explicitamente:
1. Si el proyecto Jira tiene **Xray disponible y operativo**.
2. La `Project Key`.
3. Las User Stories objetivo (keys Jira) para vincular los tests.

Con esa respuesta, ejecuta una de estas rutas:

### **Ruta A - Sin Xray**
Si **NO** hay Xray disponible:
1. Documenta casos de prueba manuales o automatizables.
2. Si hay MCP de Atlassian, crea incidencias Jira tipo **Test** (o **Task** con label `Test-Case` si no existe tipo Test).
3. Vincula **obligatoriamente** cada test a su User Story correspondiente.
4. Mantiene formato:
*   Manual: `Accion -> Resultado Esperado`.
*   Automatizable: escenario en Gherkin dentro de descripcion/comentarios del issue.
5. Genera siempre un documento local de respaldo por cada CP creado.

### **Ruta B - Con Xray**
Si **SI** hay Xray disponible:
1. Usa obligatoriamente `.prompts/7-Documentacion CPs/x-rayApiPrompts.md`.
2. Crea tests por API de Xray segun tipo:
*   **Manual:** crear Test tipo Manual y cargar steps dentro de Xray.
*   **Cucumber:** crear Test tipo Cucumber y cargar escenario Gherkin.
3. Vincula **obligatoriamente** cada Test a su User Story en Jira.
4. Reporta resultado de creacion con IDs/keys generadas.
5. Genera siempre un documento local de respaldo por cada CP creado.

### **Reglas de Documentacion**
*   Incluye precondiciones, datos de prueba, prioridad y trazabilidad (US -> Test).
*   Si un caso es automatizable, indicarlo explicitamente con etiqueta/flag.
*   Si hay MCP/API disponible, preguntar antes de crear masivamente.
*   Un test case no se considera completo hasta que quede vinculado a su User Story.

---

### **Formato de Salida Requerido**

Tu salida final debe incluir SIEMPRE:

1. **Decision de Ruta**
*   `Xray disponible: SI/NO`
*   `Ruta ejecutada: A (Jira sin Xray) o B (Xray API)`

2. **Casos de Prueba Documentados**

**Formato Jira (sin Xray):**
| Summary | Description | Step | Expected Result | Priority | Labels |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [TC-01] Login Exitoso | Verificar acceso con credenciales validas | 1. Ir a /login<br>2. Ingresar user/pass<br>3. Click Entrar | Redirige al Home | High | Regression,Manual |

**Formato Xray Manual:**
*   Test Type: `Manual`
*   Steps cargados en Xray (accion + expected).

**Formato Xray Cucumber:**
```gherkin
Feature: Login Seguro

  @Automate @Priority:High
  Scenario: Acceso con credenciales validas
    Given el usuario esta en la pagina de login
    When ingresa el usuario "admin" y password "1234"
    Then es redirigido al dashboard principal
```

3. **Resultado de Carga**
*   Keys de tests creados (Jira/Xray).
*   Story vinculada por cada test (obligatorio).
*   Evidencia del vinculo `US <-> Test` (link type usado o referencia equivalente).
*   Errores o pendientes, si existen.

4. **Documento Local de Respaldo (Obligatorio)**
*   Genera un Markdown por cada CP en:
    `.context/testing/documentation/[ID-US]/[ID-CP]-[nombre-kebab].md`
*   Donde:
    *   `[ID-US]` = key de la User Story (ej: `PROJ-123`).
    *   `[ID-CP]` = key del test creado en Jira/Xray (si aun no existe, usar temporal `CP-TEMP-01` y luego actualizar).
*   Cada archivo debe incluir como minimo:
    *   Decision de ruta (A/B).
    *   Traza `US -> Test -> Tipo (Manual/Cucumber) -> Herramienta (Jira/Xray) -> Key`.
    *   Estado de carga (creado/pendiente/error).
    *   Referencias a artefactos fuente (escenarios, reportes exploratorios, ROI/priorizacion).

### **FIN DEL PROMPT**
