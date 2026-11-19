# APE 5 · Diseño de Interfaces Web Adaptables (`Aula Abierta`)

Repositorio oficial de la **Guía Práctica APE 5 (Fases 1 y 2)** correspondiente a la asignatura **Interacción Humano / Computador** de la Carrera de Software — Facultad de Ingeniería en Sistemas, Electrónica e Industrial (FISEI), **Universidad Técnica de Ambato (UTA)**.

* **Repositorio:** [https://github.com/VK0691/APE5-IHC](https://github.com/VK0691/APE5-IHC)
* **Nivel y Paralelo:** Quinto - "B"
* **Docente:** Ing. Mg. José Rubén Caiza Caizabuano
* **Integrantes del Equipo:**
  * Bejarano Masabanda Carlos Fabian
  * Guatemal Avilez Bryan Stalin
  * Molina Nuñez Karen Valeria
  * Solis Salinas Mario Tomas

---

## Descripción del Proyecto

Transformación del boceto estático de escritorio (`prototipo-A.html`) de la plataforma **Aula Abierta · Reserva de Talleres** en una interfaz web adaptable (*responsive*), semántica y accesible por teclado bajo metodología **Mobile-First**.

### Objetivos Alcanzados
1. **Eliminación de desbordamiento horizontal:** Sustitución de dimensiones rígidas (`960 px`) por un flujo fluido de una columna (`1fr`) en dispositivos móviles y una cuadrícula de dos columnas (`1.6fr 1fr`) a partir del punto de corte `48rem` (`768 px`).
2. **Semántica HTML5 y accesibilidad:** Uso de etiquetas estructurales (`<header>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<dl>`) y región dinámica `<p role="status" aria-live="polite">`.
3. **Gestión de estados y foco:** Control completo del ciclo **Disponible → Confirmada → Cancelada** operable al `100 %` con teclado (`Tab`, `Enter`, `Espacio`), prevención de envíos duplicados mediante `disabled` y transferencia automática del foco (`.focus()`).
4. **Validación técnica y con usuarios:** Comprobación de `scrollWidth <= innerWidth` en 4 resoluciones (`320`, `360`, `768` y `1366 px`), prueba de observación con usuario externo y defensa cruzada QA/UX frente al Grupo 3 (G3).

---

## Estructura del Repositorio

```text
APE5-IHC/
├── src/
│   ├── index.html          # Estructura HTML5 semántica de la interfaz
│   ├── estilos.css         # Hoja de estilos Mobile-First (punto de corte en 48rem)
│   └── reserva.js          # Controlador de estados y gestión accesible del foco
├── docs/
│   ├── proyecto.md         # Ficha de aplicación al proyecto y diagnóstico inicial (Fase 1)
│   ├── preguntas.md        # Acta de defensa cruzada QA/UX frente al Grupo 3 (Fase 2)
│   └── conclusiones.md     # Síntesis de cierre, limitaciones y siguiente iteración (Fase 2)
├── resultados/
│   ├── pruebas.md          # Matriz de mediciones técnicas en 4 viewports (320 a 1366 px)
│   └── checklist.md        # Registro de prueba de observación con participante externo
├── evidencias/             # Capturas de validación técnica en DevTools al 100 % de zoom
└── README.md               # Documentación general del repositorio
```

---

## Resumen de Validación Técnica (Fase 2)

| Viewport | `innerWidth` | `scrollWidth` | Desborde | Distribución |
| :--- | :---: | :---: | :---: | :--- |
| `320 × 720 px` | `320 px` | `320 px` | `0 px` | 1 columna (`1fr`) |
| `360 × 800 px` | `360 px` | `360 px` | `0 px` | 1 columna (`1fr`) |
| `768 × 1024 px` | `768 px` | `768 px` | `0 px` | 2 columnas (`1.6fr 1fr`) |
| `1366 × 768 px` | `1366 px` | `1366 px` | `0 px` | 2 columnas centradas (`max-width: 62rem`) |

### Resultados de Prueba con Usuario Externo
* **Tiempo total de tarea:** `14.2 s`
* **Errores de navegación:** `0`
* **Solicitudes de ayuda:** `0`

---

## Ejecución Local

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/VK0691/APE5-IHC.git
   ```
2. Abrir el archivo `src/index.html` en cualquier navegador moderno o mediante una extensión de servidor local (*Live Server*).
3. Para auditar los puntos de corte, abrir **DevTools (`F12`) → Toggle Device Toolbar (`Ctrl + Shift + M`)** al `100 %` de zoom.