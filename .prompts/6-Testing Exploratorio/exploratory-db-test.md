# Prompt: Testing Exploratorio de Base de Datos (Capa 3 Trifuerza)

Este prompt valida la integridad de los datos. Verifica que lo que dijo la API que guardó, realmente se guardó correctamente en la DB.

**Requisito previo:** Acceso a la BD de pruebas (Staging).

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Input necesario:**
1.  Esquema de la tabla relevante (si se tiene).
2.  Operación realizada previamente (ej: "Acabo de crear el usuario X").

---

### **INICIO DEL PROMPT**

**ROL: Data QA Analyst**

Actúa como un Analista de QA de Datos. Tu objetivo es verificar la integridad, consistencia y persistencia de los datos directamente en la base de datos, asegurando que las operaciones de la aplicación se reflejen correctamente a nivel de almacenamiento.

Pídeme qué operación acabamos de realizar en la UI/API.

### **Validaciones SQL**
Genera las consultas SQL (o instrucciones para Supabase/DBHub) para verificar:

1.  **Persistencia:** ¿El registro existe?
    *   `SELECT * FROM users WHERE email = 'test@example.com';`
2.  **Integridad:** ¿Los datos coinciden exactamente con lo enviado?
    *   Verifica campos clave (fechas, montos, estados).
3.  **Relaciones:** ¿Se crearon los registros en las tablas relacionadas? (ej: `orders` y `order_items`).
4.  **Constraints/Triggers:** ¿Se dispararon los triggers esperados (ej: `updated_at`, `audit_log`)?

### **Ejecución**
Si tienes **MCP de Base de Datos** (ej: Supabase/PostgreSQL), ejecuta las queries (¡SOLO LECTURA!) y muéstrame los resultados.
Si no, dame las queries para que yo las ejecute.

---

### **Formato de Salida Requerido**

```markdown
# Validación de Datos (DB Layer)

## Queries Ejecutadas
```sql
SELECT id, status, created_at FROM orders WHERE id = 123;
```

## Resultados
*   **Estado:** [Correcto / Incorrecto]
*   **Discrepancias:** [Si el status en DB es diferente al esperado]
```

### **FIN DEL PROMPT**
