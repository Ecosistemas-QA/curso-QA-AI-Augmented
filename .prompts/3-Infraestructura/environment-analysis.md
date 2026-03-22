# Prompt: Análisis de Infraestructura y Entornos de Prueba

Este prompt está diseñado para que el QA Augmented "mapee el terreno" donde ejecutará sus pruebas. Define qué tipo de aplicación es, los entornos disponibles y cómo se despliega el código.

---

### **INICIO DEL PROMPT**

**ROL: DevOps & Infrastructure Lead**

Actúa como un Ingeniero Líder en DevOps y QA. Tu objetivo es diseñar una estrategia de entornos de prueba robusta que garantice la fiabilidad del software desde el desarrollo local hasta producción.

Para comenzar, necesito que me hagas las siguientes preguntas clave para entender el contexto:

1.  **Tipo de Aplicación:** ¿Es una aplicación Web, Móvil (iOS/Android), de Escritorio, o una combinación?
2.  **Estado del Proyecto:** ¿Es un proyecto nuevo (sin infraestructura aún) o existente (con servidores y pipelines ya configurados)?

Una vez que tengas mis respuestas, analiza el escenario:

### **Escenario A: Proyecto Nuevo (Greenfield)**

1.  **Recomendación de Entornos:** Propón una estrategia de entornos estándar para QA moderna (ej: Local -> Preview/PR -> Staging -> Production). Explica el propósito de cada uno.
2.  **Estrategia de Dispositivos:**
    *   Si es Web: Recomienda navegadores y resoluciones clave (Desktop, Mobile Web).
    *   Si es Mobile: Sugiere simuladores vs dispositivos reales (granjas de dispositivos como BrowserStack/SauceLabs).
3.  **CI/CD:** Sugiere un pipeline básico de integración continua (ej: GitHub Actions) que ejecute lints y tests unitarios en cada Pull Request.

### **Escenario B: Proyecto Existente (Legacy/Brownfield)**

1.  **Investigación de Entornos:** Guíame con preguntas para descubrir qué entornos existen hoy (ej: "¿Tienes una URL de 'Dev' o 'QA' diferente a la de producción?").
2.  **Acceso y Credenciales:** Recuérdame (sin pedirme las claves reales) que debo solicitar accesos a VPNs, bases de datos de staging o cuentas de prueba específicas.
3.  **Pipelines Actuales:** Pregúntame si sé cómo se despliega el código hoy. Si no lo sé, sugiéreme contactar al equipo de DevOps o revisar archivos como `.github/workflows` o `Jenkinsfile` en el repositorio.

---

### **Formato de Salida Requerido**

Tu salida final debe ser un bloque de código Markdown listo para guardar en: `.context/infrastructure/environments.md`.

El contenido debe seguir esta estructura:

```markdown
# Estrategia de Infraestructura y Entornos: [Nombre del Proyecto]

## 1. Tipo de Aplicación y Alcance
*   **Plataforma:** [Web / Mobile / Híbrida]
*   **Matriz de Compatibilidad:**
    *   [Navegadores/SO soportados]
    *   [Resoluciones clave]

## 2. Mapa de Entornos (Matriz de URLs)
| Componente | Entorno Local | Entorno Staging/QA | Entorno Producción |
| :--- | :--- | :--- | :--- |
| **Frontend** | `http://localhost:3000` | `[URL]` | `[URL]` |
| **Backend API** | `http://localhost:8080` | `[API Base URL]` | `[API Base URL]` |
| **Base de Datos** | `localhost:5432` | `[Host/Connection]` | `[Restringido]` |

### Detalles de Acceso
*   **Credenciales de Prueba:** [Referencia a Vault/.env]
*   **VPN/Restricciones:** [Si aplica]

## 3. Pipeline de CI/CD (Integración Continua)
*   **Trigger:** [Cuándo se ejecutan las pruebas: al hacer Push, al crear PR, etc.]
*   **Pruebas Automáticas:** [Qué tests corren en el pipeline]

## 4. Herramientas de Infraestructura
*   [Ej: Docker, Kubernetes, Vercel, AWS]
```

Al finalizar sugerir continuar con `.prompts\3-Infraestructura\data-strategy.md`

### **FIN DEL PROMPT**
