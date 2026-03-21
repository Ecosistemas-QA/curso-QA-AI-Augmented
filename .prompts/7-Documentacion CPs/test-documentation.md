# Prompt: Documentación Formal de Casos de Prueba (Jira/Xray)

Este prompt genera la documentación final detallada, lista para ser importada a tu herramienta de gestión (Jira, Xray, TestRail).

**Requisito previo:** Escenarios priorizados.

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Input necesario:**
1.  Escenarios seleccionados (Manuales o Automatizables).
2.  ¿Usas Jira Nativo o Jira + Xray?

---

### **INICIO DEL PROMPT**

**ROL: QA Documentation Specialist**

Actúa como un Especialista en Documentación de QA. Tu objetivo es redactar Casos de Prueba formales con un lenguaje técnico preciso, asegurando que cualquier persona del equipo pueda entenderlos y ejecutarlos sin dudas.

Pídeme los escenarios y la herramienta destino (Jira Estándar o Xray).

### **Redacción de Pasos**
*   **Para Manuales (Jira Standard):**
    *   Usa formato "Acción -> Resultado Esperado".
    *   Sé imperativo y claro.
    *   Incluye Pre-condiciones y Datos de Prueba.

*   **Para Automatizables (Xray/Cucumber):**
    *   Usa formato **Gherkin** estricto (Given/When/Then).
    *   Usa `Scenario Outline` si hay múltiples datos.

### **Acción (Si hay MCP)**
Si tienes **MCP de Atlassian**, pregúntame si quieres que cree los Test Issues directamente en Jira vinculados a la User Story.
*   *Tipo de Issue:* "Test" (si existe) o "Task" con etiqueta `Test-Case`.
*   *Link:* "Tests" -> [User Story Key].

---

### **Formato de Salida Requerido**

**Opción A: Formato Jira CSV (Tabla Markdown)**
| Summary | Description | Step | Expected Result | Priority | Label |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [TC-01] Login Exitoso | Verificar acceso con credenciales válidas | 1. Ir a /login<br>2. Ingresar user/pass<br>3. Click Entrar | Redirige al Home | High | Regression |

**Opción B: Formato Gherkin (Xray)**
```gherkin
Feature: Login Seguro

  @Automate @Priority:High
  Scenario: Acceso con credenciales validas
    Given el usuario esta en la pagina de login
    When ingresa el usuario "admin" y password "1234"
    Then es redirigido al dashboard principal
```

### **FIN DEL PROMPT**
