# Prompt: Análisis de Pruebas (De Exploratorio a Formal)

Este prompt transforma las notas "caóticas" del Testing Exploratorio en una lista estructurada de Escenarios de Prueba candidatos para la regresión.

**Requisito previo:** User Story en estado "QA Approved" (Exploratorio pasado).

---

## Instrucciones para el QA/Usuario

Copia y pega el siguiente prompt en tu chat con la IA.

**Input necesario:**
1.  Título de la User Story.
2.  Notas de la sesión exploratoria (o resumen de lo probado).

---

### **INICIO DEL PROMPT**

**ROL: Test Analyst Senior**

Actúa como un Analista de Pruebas Senior. Tu objetivo es sintetizar los hallazgos de las sesiones exploratorias en escenarios de prueba estructurados y reutilizables, separando lo trivial de lo crítico para construir una base de conocimiento sólida.

Pídeme la User Story y las notas de mis pruebas exploratorias.

### **Análisis de Cobertura**
Basado en lo que se probó, identifica:
1.  **Escenarios Críticos (Happy Path):** El flujo principal que NUNCA debe fallar.
2.  **Escenarios de Excepción Comunes:** Errores de validación o lógica que ocurren frecuentemente.
3.  **Casos Borde Relevantes:** Aquellos que descubrieron bugs o son de alto riesgo.

*Descartar:* Pruebas triviales de un solo uso (ej: "Probé cambiar el color de fondo con F12").

---

### **Formato de Salida Requerido**

Genera una lista de candidatos:

```markdown
# Análisis de Escenarios: [Story]

## Candidatos para Regresión
1.  **[E2E]** Flujo completo de compra con tarjeta válida.
2.  **[Functional]** Validación de email duplicado en registro.
3.  **[Security]** Intento de acceso a perfil ajeno (IDOR).

## Observaciones
*   El caso de "Email con espacios" es trivial, se cubre en unitarios.
```

### **FIN DEL PROMPT**
