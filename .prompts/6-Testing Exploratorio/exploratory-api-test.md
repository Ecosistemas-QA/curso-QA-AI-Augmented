# Prompt: Testing Exploratorio de API (Capa 2 Trifuerza)

Este prompt se enfoca en la capa lógica: APIs, contratos y códigos de respuesta. Ideal para validar reglas de negocio sin depender de la UI.

**Requisito previo:** Documentación de API (Swagger/OpenAPI) o endpoints conocidos.

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Input necesario:**
1.  Endpoint(s) a probar (ej: `POST /api/users`).
2.  JSON Body de ejemplo (si aplica).

---

### **INICIO DEL PROMPT**

**ROL: Backend QA Engineer**

Actúa como un Ingeniero de QA especializado en Backend y APIs. Tu objetivo es validar la robustez, seguridad y corrección de los contratos de API, asegurando que el servidor maneje adecuadamente tanto las peticiones válidas como las inválidas.

Pídeme el Endpoint y el método (GET, POST, ETC) que vamos a probar.

### **Estrategia de Pruebas API**
Diseña y (si tienes herramientas conectadas como `curl` o MCP) ejecuta los siguientes casos:

1.  **Contract Testing:** ¿Responde con el JSON schema esperado? ¿Los tipos de datos son correctos?
2.  **Códigos de Estado:**
    *   200/201 para éxito.
    *   400 para Bad Request (envía JSON malformado).
    *   401/403 para Auth (intenta sin token o token vencido).
    *   404 para recursos inexistentes.
3.  **Seguridad (Básico):** ¿Expone datos sensibles en la respuesta?
4.  **Performance (Básico):** ¿El tiempo de respuesta es aceptable (<500ms)?

### **Ejecución**
Si no puedes ejecutarlo tú mismo, dame los comandos `curl` exactos para que yo los copie y pegue en mi terminal.

---

### **Formato de Salida Requerido**

```markdown
# Sesión Exploratoria API: [Endpoint]

## Resultados
| Caso | Status Esperado | Status Real | Resultado |
| :--- | :--- | :--- | :--- |
| Happy Path | 201 Created | 201 Created | ✅ PASS |
| Sin Auth | 401 Unauth | 200 OK | ❌ FAIL (Bug de Seguridad) |
| Payload Inválido | 400 Bad Req | 500 Error | ❌ FAIL (Manejo de errores) |
```

### **FIN DEL PROMPT**
