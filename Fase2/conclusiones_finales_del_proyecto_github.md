# Conclusiones Finales · APE 5 (Fase 2)

**Proyecto:** Aula Abierta · Reserva de Talleres  
**Integrantes:** Bejarano Carlos, Guatemal Bryan, Molina Karen, Solis Mario

---

## Síntesis de Cierre

1. **Requisito y decisión técnica:**  
   Frente al problema inicial de ancho fijo (`960 px`) que provocaba desbordamiento horizontal y ocultaba el estado de reserva en dispositivos móviles, se decidió aplicar una arquitectura CSS *Mobile-First* (`1fr` en móvil y `1.6fr 1fr` a partir de `48rem`) sobre una estructura HTML5 semántica (`<dl>`, `<button>`, `role="status"`), manteniendo intacto el orden natural del DOM.

2. **Dato observado en validación:**  
   La auditoría técnica en DevTools confirmó ausencia total de desplazamiento horizontal (`scrollWidth <= innerWidth`, con `0 px` de desborde) en las cuatro resoluciones evaluadas (`320`, `360`, `768` y `1366 px`). Asimismo, la prueba de observación con usuario externo registró un tiempo de completitud de `14.2 s` con `0` errores y `0` solicitudes de ayuda.

3. **Limitación identificada:**  
   Cuando el catálogo crezca a cuatro o más talleres apilados verticalmente en pantallas estrechas (`320 px` y `360 px`), el panel lateral *«Mi reserva»* quedará ubicado al final de la página fuera del primer pantallazo, exigiendo desplazamiento vertical para consultar el resumen completo.

4. **Siguiente iteración:**  
   Incorporar en una próxima versión una barra de estado compacta persistente en la parte superior del *viewport* móvil para confirmar reservas sin depender del desplazamiento vertical, además de añadir un diálogo de confirmación previa antes de ejecutar la cancelación de un cupo.