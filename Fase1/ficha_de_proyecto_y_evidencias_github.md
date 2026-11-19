# Ficha de Aplicación y Evidencias · APE 5 (Fase 1)

**Asignatura:** Interacción Humano Computador  
**Nivel y Paralelo:** Quinto - B  
**Tema:** T2.5. Taller de transformación responsive (`Aula Abierta · Reserva de Talleres`)  
**Integrantes:**
- Bejarano Masabanda Carlos Fabian
- Guatemal Avilez Bryan Stalin
- Molina Nuñez Karen Valeria
- Solis Salinas Mario Tomas

---

## 1. Diagnóstico del Boceto Inicial (`prototipo-A.html` a 360 px)

Al evaluar el boceto estático original bajo un *viewport* móvil estándar de `360 px`, se identificaron las siguientes fallas críticas de usabilidad:

| Elemento / Selector | Regla en Boceto A | Impacto en Móvil (`360 px`) |
| :--- | :--- | :--- |
| `body` | `width: 960px;` | Genera un desbordamiento horizontal obligatorio de `600 px`. |
| `main` | `grid-template-columns: 580px 360px;` | Mantiene dos columnas rígidas sin apilamiento vertical. |
| `<aside>` (*Mi reserva*) | Segunda columna fija | Queda completamente oculto fuera de la pantalla visible inicial. |
| `<button>` | Atributo `disabled` estático | Impide probar el flujo de inscripción y carece de retroalimentación. |

---

## 2. Ficha de Aplicación al Proyecto

- **Actor:** Estudiante universitario que consulta y gestiona su inscripción en talleres extracurriculares desde su dispositivo móvil o computador de escritorio.
- **Tarea:** Revisar los datos clave de un taller disponible, confirmar la reserva de un cupo y, si lo requiere, cancelar dicha reserva.
- **Dato decisivo:** Día, franja horaria (`Jueves · 14:00 a 16:00`) y aula (`Laboratorio 2`), estructurados semánticamente mediante listas de definición (`<dl>`).
- **Acción principal:** Activar el botón nativo **«Reservar un lugar»** mediante puntero o teclado (`Tab` + `Enter` / `Espacio`).
- **Estado final:** Confirmación visual y semántica en la región `<p role="status">`, bloqueo del botón principal (`disabled`) para impedir reservas duplicadas y traslado automático del foco hacia el botón **«Cancelar reserva»**.

### Regla de Negocio, Criterio de Aceptación y Decisión HCI
- **Regla de negocio:** Un estudiante puede mantener únicamente una reserva activa por taller a la vez; mientras esté confirmada, no se permite volver a reservar, pero sí cancelar para liberar el cupo.
- **Criterio de aceptación medible:**
  1. En `360 px` de ancho, la interfaz se apila en 1 sola columna sin barra de desplazamiento horizontal (`document.documentElement.scrollWidth <= 360`).
  2. A partir de `48rem` (`768 px`), la distribución cambia a 2 columnas (`minmax(0, 1.5fr) minmax(0, 1fr)`) manteniendo intacto el orden del DOM.
  3. El ciclo completo (**Disponible → Confirmada → Cancelada**) puede operarse al 100 % con teclado sin pérdida de foco.
- **Decisión HCI justificada:** Se emplea diseño *Mobile-First* con unidades relativas (`rem`) y flujo natural de lectura (primero el detalle del taller, luego el panel de estado), evitando alteraciones visuales con `order` para preservar la coherencia entre lectores de pantalla y navegación secuencial.

---

## 3. Evidencias Visuales (Capturas de Pantalla)

> **Instrucciones para subir evidencias al repositorio:**  
> 1. Guardar las capturas dentro de la carpeta `docs/evidencias/`.  
> 2. Nombrarlas como `movil-360px.png` y `escritorio-1366px.png` (o `escritorio-768px.png`).  
> 3. Hacer commit y push junto con este archivo.

### 3.1. Vista Móvil (`360 px` · 1 Columna)
*Verificación: Sin scroll horizontal, panel «Mi reserva» visible debajo de la tarjeta del taller y botones con área táctil mínima de `44 px` (`2.75rem`).*

![Vista móvil 360px](evidencias/movil-360px.png)

### 3.2. Vista Escritorio (`768 px` / `1366 px` · 2 Columnas)
*Verificación: Activación de cuadrícula de dos columnas desde `@media (min-width: 48rem)` y estado de reserva confirmada con foco activo.*

![Vista escritorio 1366px](evidencias/escritorio-1366px.png)

---

## 4. Hipótesis Detectada en Revisión entre Pares (Para Fase 2)

> *"Cuando la oferta académica incluya cuatro o más talleres apilados verticalmente en móvil (`360 px`), el panel `<aside>` de «Mi reserva» quedará desplazado hacia la parte inferior fuera del primer pantallazo. En la Fase 2 se evaluará si incorporar una notificación contextual dentro de la propia tarjeta o una barra fija inferior reduce el tiempo de verificación del usuario tras pulsar reservar."*