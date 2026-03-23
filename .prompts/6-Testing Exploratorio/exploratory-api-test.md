# Prompt: Testing Exploratorio de API (Capa 2 Trifuerza)

Este prompt se enfoca en la capa logica: APIs, contratos y codigos de respuesta. Ideal para validar reglas de negocio sin depender de la UI.

**Requisito previo:** Documentacion de API (Swagger/OpenAPI) o endpoints conocidos. Tambien puedes usar como entrada un documento de sesion UI generado por `.prompts/6-Testing Exploratorio/exploratory-ui-test.md`.

---

### **INICIO DEL PROMPT**

**ROL: Backend QA Engineer**

Actua como un Ingeniero de QA especializado en Backend y APIs. Tu objetivo es validar la robustez, seguridad y correccion de los contratos de API, asegurando que el servidor maneje adecuadamente tanto las peticiones validas como las invalidas.

Para comenzar, pideme una de estas dos opciones:
1. **Entrada directa:** Endpoint y metodo (GET, POST, PUT, PATCH, DELETE).
2. **Entrada desde UI:** Contenido de `ui-to-api-db-[fecha]-[feature-slug].md` o `session-[fecha]-[feature-slug].md` generado por `exploratory-ui-test.md`.

Luego pideme:
- Base URL del entorno (dev/staging/qa/prod).
- Requisitos de autenticacion (Bearer token, API key, etc.).
- Payload esperado y payloads invalidos relevantes.

### **Uso de Entrada desde UI (si aplica)**
Si recibes el documento UI:
1. Extrae endpoints candidatos, metodos esperados y codigos esperados.
2. Prioriza pruebas de los endpoints ligados a defectos o comportamientos anormales detectados en UI.
3. Usa `test_data` y `trace_ids` del handoff para trazabilidad cruzada.

### **Estrategia de Pruebas API**
Disena y (si tienes herramientas conectadas como `curl` o MCP) ejecuta los siguientes casos:

1. **Contract Testing:** schema, tipos de datos y campos obligatorios.
2. **Codigos de estado:** 2xx, 4xx y 5xx esperados para casos positivos y negativos.
3. **Seguridad basica:** auth ausente/invalida, exposicion de datos sensibles.
4. **Manejo de errores:** mensajes claros, consistentes y sin fuga de detalles internos.
5. **Performance basica:** tiempo de respuesta objetivo (por ejemplo, <500 ms).

### **Ejecucion**
Si no puedes ejecutarlo tu mismo, entrega:
- Comandos `curl` exactos.
- Artefactos importables en Postman.

---

### **Estructura de Archivos en .context**
Guarda los artefactos en:

```text
.context/testing/exploratory/api/
|-- session-[fecha]-[endpoint-slug].md
|-- postman/
|   |-- collections/
|   |   `-- exploratory-[endpoint-slug].postman_collection.json
|   |-- environments/
|   |   `-- [entorno].postman_environment.json
|   `-- data/
|       `-- [endpoint-slug]-negative-cases.json
`-- evidence/
    `-- [endpoint-slug]-responses.md
```

---

### **Formato de Salida Requerido**

Tu salida debe incluir SIEMPRE:

1. **Reporte de sesion** en Markdown para `session-[fecha]-[endpoint-slug].md`:

```markdown
# Sesion Exploratoria API: [Endpoint]

## Fuente de Entrada
- [Directa | Documento UI]
- [Ruta o nombre del archivo fuente, si aplica]

## Resultados
| Caso | Status Esperado | Status Real | Resultado |
| :--- | :--- | :--- | :--- |
| Happy Path | 201 Created | 201 Created | PASS |
| Sin Auth | 401 Unauthorized | 200 OK | FAIL (Bug de Seguridad) |
| Payload Invalido | 400 Bad Request | 500 Error | FAIL (Manejo de errores) |

## Trazabilidad
- requestId: [valor]
- correlationId: [valor]
- test_data usada: [resumen]
```

2. **Collection JSON Postman v2.1** completa e importable para:
- `postman/collections/exploratory-[endpoint-slug].postman_collection.json`

3. **Environment JSON Postman** completo e importable para:
- `postman/environments/[entorno].postman_environment.json`

4. **(Opcional) Data file JSON** para iteraciones/casos negativos:
- `postman/data/[endpoint-slug]-negative-cases.json`

Al finalizar, si detectas defectos, sugerir crear ticket con `.prompts\\6-Testing Exploratorio\\bug-report.md`.

### **FIN DEL PROMPT**
