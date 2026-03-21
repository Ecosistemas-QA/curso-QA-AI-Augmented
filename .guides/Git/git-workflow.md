# Flujo de Trabajo y Buenas Prácticas (Workflow QA)

## 🎯 Objetivo
En un equipo de **QA Augmented**, Git no solo guarda código, sino **Conocimiento**. Usamos Git para gestionar Prompts, Documentación de Pruebas y Contexto del Proyecto.

El objetivo es que **todos tengamos la misma información** actualizada y ordenada.

---

## 🚫 La Regla de Oro
> **NUNCA trabajes directamente en la rama `main`.**

La rama `main` es sagrada. Debe contener solo documentos aprobados y funcionales. Si subes algo roto a `main`, rompes el trabajo de todo el equipo.

---

## 🌳 Uso de Ramas (Branches)

Una **Rama** es una copia paralela del proyecto donde puedes trabajar tranquilo sin afectar a los demás.

### Nomenclatura Recomendada para QA

Usa prefijos para que sepamos de qué trata tu trabajo:

| Prefijo | Uso | Ejemplo |
| :--- | :--- | :--- |
| **docs/** | Documentación nueva o actualizada | `docs/US-1122-login` |
| **prompts/** | Creación o mejora de Prompts | `prompts/mejora-analisis` |
| **test/** | Casos de prueba o scripts | `test/regresion-pagos` |
| **fix/** | Corrección de errores en docs | `fix/typo-en-readme` |

### Comandos para Ramas

1.  **Crear una rama nueva:**
    ```bash
    git checkout -b docs/mi-nueva-tarea
    ```
2.  **Cambiar de rama:**
    ```bash
    git checkout main
    ```
3.  **Ver tus ramas:**
    ```bash
    git branch
    ```

---

## 🔄 El Ciclo de Vida de una Tarea

Imagina que te asignan documentar la **Historia de Usuario 505 (Pago con QR)**.

### Paso 1: Actualizar y Crear Rama
Antes de nada, asegúrate de tener lo último de `main`:
```bash
git checkout main
git pull origin main
git checkout -b docs/US-505-pago-qr
```

### Paso 2: Trabajar
Creas los archivos, modificas los prompts, escribes los casos de prueba.
*(Aquí usas `git status`, `git add .` y `git commit -m "..."` tantas veces como necesites)*.

### Paso 3: Subir tu Rama
Cuando termines, sube **tu rama** a la nube (no a `main`):
```bash
git push origin docs/US-505-pago-qr
```

### Paso 4: Pull Request (Revisión de Pares)
Ve a GitHub y verás un botón **"Compare & pull request"**.
*   Esto avisa a tu equipo: *"Terminé los docs de la US-505, ¿alguien puede revisarlos?"*.
*   Un compañero revisa que los prompts sean efectivos y la documentación clara.
*   Si todo está bien, aprueban y mezclan (**Merge**) tu trabajo en `main`.

---

## ✨ Buenas Prácticas de Commit

El mensaje del commit debe explicar **QUÉ** hiciste, no solo decir "cambios".

*   ❌ Mal: "archivos subidos", "fix", "listo"
*   ✅ Bien: "docs: Agregar casos de prueba para Login"
*   ✅ Bien: "prompt: Optimizar prompt de análisis de riesgos"

### Estructura Recomendada:
`[tipo]: [descripción breve]`

*   **feat:** Algo nuevo (Feature).
*   **fix:** Corrección.
*   **docs:** Solo documentación.
*   **style:** Formato (espacios, puntos y comas).
*   **refactor:** Mejorar algo que ya existía sin cambiar su función.
