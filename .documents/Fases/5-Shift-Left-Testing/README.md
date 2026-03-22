# Fase 5: Shift-Left Testing

## 🎯 Objetivo de la Fase
Mover las actividades de prueba "a la izquierda" en la línea de tiempo. Es decir, probar **antes** de que exista código. Aquí prevenimos defectos en lugar de solo detectarlos. Tambien se hace una valoracion o calificacion de cada CP propuesto en las US para la etapa de documentacion.

## 🔑 Conceptos Clave

### 1. Inspección Estática
Analizar los requisitos (User Stories) buscando:
*   **Ambigüedades:** Palabras vagas ("rápido", "fácil").
*   **Lagunas:** Casos no cubiertos (errores, desconexión).
*   **Contradicciones:** Reglas que chocan entre sí.

### 2. Risk-Based Testing (RBT)
No se puede probar todo exhaustivamente. Priorizamos basándonos en:
*   **Probabilidad:** ¿Qué tan probable es que falle?
*   **Impacto:** ¿Qué tan grave es si falla?

### 3. Estrategia de Prueba (Test Strategy)
Definir **qué** tipos de pruebas (Unitarias, Integración, E2E) y **con qué** herramientas se abordará cada Epic.

## 🛠️ Herramientas Utilizadas
*   **Prompts de IA:** `requirement-inspection.md`, `test-plan-generator.md`.

## 📝 Entregables Esperados
Al finalizar esta fase, tendrás en tu carpeta `.context/testing/`:
1.  Reportes de **Inspección de Requisitos**.
2.  **Planes de Prueba** y **Matrices de Riesgo** por Epic.
3.  **User Stories Corregidas:** Las mejoras detectadas deben aplicarse directamente en la fuente (Jira o Documentos Locales), cerrando el ciclo de calidad.
