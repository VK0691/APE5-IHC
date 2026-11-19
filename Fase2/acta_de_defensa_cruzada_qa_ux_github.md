# Acta de Defensa Cruzada QA/UX · APE 5 (Fase 2)

**Grupo Evaluado:** Grupo Quinto - B (Bejarano, Guatemal, Molina, Solis)  
**Grupo Retador Asignado:** Grupo 3 (G3)  
**Prototipo Sustentado:** *Aula Abierta · Reserva de Talleres*

---

## 1. Pregunta Técnica 1: Punto de corte en CSS y preservación del orden con `Tab`

* **Pregunta (G3):** ¿Por qué eligieron `48rem` como punto de corte en lugar de píxeles fijos y cómo garantizan que al pasar de una a dos columnas no se rompa el orden de tabulación con la tecla `Tab`?
* **Respuesta y sustento técnico:**
  * Se utilizó `@media (min-width: 48rem)` (`768 px` con base estándar de `16 px`) porque las unidades relativas `rem` escalan proporcionalmente si el usuario incrementa el tamaño de tipografía predeterminado de su navegador.
  * La distribución en escritorio mediante CSS Grid (`grid-template-columns: 1.6fr 1fr`) altera exclusivamente la disposición visual en pantalla sin utilizar propiedades que modifiquen el orden de lectura como `order` o `row-reverse`. Por tanto, el flujo de tabulación (`header → article → aside`) coincide exactamente con el orden lógico del árbol DOM (WCAG 2.1, criterio 2.4.3).

---

## 2. Pregunta Técnica 2: Prevención de envíos duplicados y gestión del foco

* **Pregunta (G3):** ¿Qué ocurre a nivel de accesibilidad y control de estado cuando el usuario confirma una reserva y qué sucedería con el foco del teclado si no se gestionara explícitamente en JavaScript?
* **Respuesta y sustento técnico:**
  * Al pulsar *«Reservar un lugar»*, el controlador ejecuta `btnReservar.disabled = true`, bloqueando de forma nativa tanto clics repetidos como pulsaciones accidentales de `Enter` o `Espacio`.
  * Como los navegadores remueven del orden de tabulación a los controles con atributo `disabled`, omitir la gestión del foco provocaría que el cursor de teclado se pierda y regrese al inicio del documento (`<body>`). Para evitarlo, inmediatamente después de mostrar el botón de cancelación (`btnCancelar.hidden = false`), se invoca `btnCancelar.focus()`, manteniendo continuidad total para usuarios de teclado.

---

## 3. Objeción de Diseño: Ajuste geométrico vs. comprensión real del usuario

* **Objeción (G3):** Eliminar el scroll horizontal resuelve el ajuste geométrico de las cajas en pantalla, pero en móvil el panel *«Mi reserva»* queda debajo del taller; ¿cómo demuestran que el usuario realmente comprende que su cupo quedó reservado y no solo que la página cabe en la pantalla?
* **Respuesta y evidencia empírica:**
  * Para garantizar comprensión semántica y no solo ajuste geométrico, se implementaron tres señales redundantes:
    1. Cambio inmediato de la etiqueta del botón dentro de la tarjeta activa a *«Lugar reservado»*.
    2. Región dinámica accesible `<p id="estado-reserva" role="status" aria-live="polite">` que anuncia el cambio de estado.
    3. Traslado automático del foco hacia *«Cancelar reserva»*.
  * En la prueba de observación (`resultados/checklist.md`), el participante externo completó la tarea en `14.2 s` con `0` errores y `0` solicitudes de ayuda, demostrando comprensión efectiva del estado de su inscripción.