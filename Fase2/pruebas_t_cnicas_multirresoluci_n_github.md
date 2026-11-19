# Matriz de Pruebas Técnicas y Mediciones Responsivas · APE 5 (Fase 2)

**Proyecto:** Aula Abierta · Reserva de Talleres  
**Nivel y Paralelo:** Quinto - B  
**Herramienta:** Chrome / Edge DevTools (Emulación de dispositivos al `100 %` de zoom)

---

## 1. Medición de Desbordamiento Horizontal (`scrollWidth <= innerWidth`)

Verificación ejecutada en la consola del navegador mediante `document.documentElement.scrollWidth <= window.innerWidth` sobre la rama `main`:

| Viewport de Prueba | `innerWidth` | `scrollWidth` | Desborde (`px`) | ¿Cumple? | Disposición y Comportamiento Visual |
| :--- | :---: | :---: | :---: | :---: | :--- |
| `320 × 720 px` | `320 px` | `320 px` | `0 px` | Sí | Flujo de 1 columna (`1fr`); sin corte de texto ni desplazamiento horizontal. |
| `360 × 800 px` | `360 px` | `360 px` | `0 px` | Sí | Flujo de 1 columna; jerarquía legible y área táctil mínima de `44 px` (`2.75rem`). |
| `768 × 1024 px` | `768 px` | `768 px` | `0 px` | Sí | Punto de corte `48rem` activo; transición a 2 columnas (`1.6fr 1fr`). |
| `1366 × 768 px` | `1366 px` | `1366 px` | `0 px` | Sí | Vista escritorio de 2 columnas centrada dentro de contenedor máximo de `62rem`. |

---

## 2. Verificación de Accesibilidad por Teclado y Estados

| Criterio Evaluado | `320 px` / `360 px` | `768 px` / `1366 px` | Estado |
| :--- | :---: | :---: | :---: |
| Navegación secuencial con `Tab` | Respeta orden lógico del DOM (`header → article → aside`) | Respeta orden lógico del DOM sin alteración por `order` | Aprobado |
| Indicador visual de foco (`:focus-visible`) | Contorno visible de `3px` con contraste alto | Contorno visible de `3px` con contraste alto | Aprobado |
| Bloqueo de reserva duplicada (`disabled`) | Botón principal bloqueado al confirmar | Botón principal bloqueado al confirmar | Aprobado |
| Transferencia automática del foco (`.focus()`) | Traslada foco a *«Cancelar reserva»* y viceversa | Traslada foco a *«Cancelar reserva»* y viceversa | Aprobado |

---

## 3. Registro de Capturas en `evidencias/`

* `evidencias/viewport-320x720.png` — Captura al `100 %` de zoom en ancho mínimo extremo (`320 px`).
* `evidencias/viewport-360x800.png` — Captura al `100 %` de zoom en móvil estándar (`360 px`).
* `evidencias/viewport-768x1024.png` — Captura al `100 %` de zoom en el punto de corte (`48rem` / `768 px`).
* `evidencias/viewport-1366x768.png` — Captura al `100 %` de zoom en escritorio (`1366 px`).