# 📅 Planificador UG - Extensión de Chrome

**Planificador UG** es una extensión de navegador diseñada para optimizar y simplificar el proceso de matriculación de los estudiantes de la **Universidad de Guayaquil**. La herramienta se integra directamente con el sistema SIUG para permitir la planificación visual de horarios, detección automática de choques y generación inteligente de propuestas.

---

⚠️ **Nota:** Este proyecto se encuentra actualmente en desarrollo privado. No está disponible para el público general ni para pruebas externas por el momento.

## 🚀 Funcionalidades Clave

### 1. Planificación Visual e Interactiva
*   **Inyección Dinámica:** Agrega botones "+" directamente en la tabla de materias del SIUG.
*   **Vista Previa en Tiempo Real:** Renderizado del horario en un lienzo (`Canvas`) para visualizar huecos y distribución semanal.
*   **Detección de Choques:** Algoritmo que valida instantáneamente si una materia nueva interfiere con las ya seleccionadas.

### 2. Generador Automático (Algoritmo de 5 Fases)
El sistema incluye un motor de generación automática que utiliza una estrategia de optimización avanzada:
*   **Fase 0 (Opción Única):** Prioriza materias que solo tienen un grupo disponible en el sistema.
*   **Fase 1 (Backtracking):** Maximiza la cantidad de materias sin choques en la jornada preferida (Matutina, Vespertina, Nocturna).
*   **Fase 2-3 (Búsqueda Transversal):** Si hay choques o filtros de docente, busca automáticamente alternativas en otras jornadas.
*   **Fase 4 (Último Recurso):** Si no hay opciones sin conflicto, añade el mejor grupo disponible notificando la excepción al usuario.

### 3. Asistente de IA (Integración con Groq/Llama)
Cuenta con un chat integrado que utiliza modelos de lenguaje de gran escala (LLM) para entender peticiones en lenguaje natural:
*   *"No quiero recibir clases con x profesor y prefiero la mañana".*
*   La IA extrae los parámetros (JSON) y los delega al algoritmo determinista del sistema para construir el horario.

### 4. Filtros Avanzados de Docentes
*   Panel dedicado para listar y excluir docentes específicos de la tabla actual.
*   Sincronización persistente con el generador automático.

### 5. Exportación Profesional
*   Generación de **PDF en formato A4 (Landscape)** utilizando `jsPDF`.
*   Diseño limpio con badges de modalidad (Presencial/Híbrida), nombres de docentes y rangos horarios.

---

## 🛠️ Tecnologías Utilizadas

El proyecto sigue una arquitectura modular y "pura" (Vanilla JS), lo que garantiza velocidad y facilidad de mantenimiento:

*   **Core:** JavaScript ES6+ (Arquitectura modular).
*   **Extension API:** `chrome.storage.local` para persistencia y `Content Scripts` para manipulación del DOM en SIUG.
*   **IA:** API de **Groq** (Modelos Llama 3.1 8B y 3.3 70B) para el procesamiento de lenguaje natural.
*   **Gráficos:** HTML5 `Canvas` API para la previsualización interactiva.
*   **PDF:** `jsPDF` para la generación de documentos del lado del cliente.
*   **Estilos:** CSS3 con variables personalizadas y animaciones para la interfaz del panel y los Toasts.

---

## 📁 Estructura del Proyecto

```bash
├── config.js       # Única fuente de verdad (colores, medidas de layout, constantes)
├── horario.js     # Lógica pura de negocio (detección de choques y parseo de tiempos)
├── storage.js      # Abstracción de la persistencia en el navegador
├── render.js       # Motor de dibujo compartido entre Canvas y PDF
├── ui.tabla.js     # Algoritmo de backtracking e inyección en la tabla SIUG
├── ui.gemini.js    # Interfaz de usuario del chat con IA
├── gemini.js       # Cliente de comunicación con la API de Groq
├── ui.panel.js     # Manejo del panel flotante y eventos de UI
└── ui.toast.js     # Sistema de notificaciones no intrusivas
```

---

## 🎥 Video Demostrativo

*(Sección reservada para el video de funcionamiento)*

---

## ✉️ Contacto

Desarrollado por **Gerardo Sebastián Anchundia Moreira** - sebastiananchundiam@gmail.com

---
*Nota: Este proyecto no está afiliado oficialmente con la Universidad de Guayaquil. Es una herramienta independiente para apoyo al estudiante.*
