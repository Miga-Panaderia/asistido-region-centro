# MIGA · Multizona v61 · Inteligencia de Demanda

Versión basada en la v60 con una nueva capa de interpretación de demanda.

## Novedades

- Marcación de referencias afectadas por eventos mediante fecha Desde/Hasta y motivo.
- La venta real de Prisma no se modifica.
- MIGA guarda una base normal previa para evitar que un evento infle el sugerido del ciclo siguiente.
- Checklist con motivo de ausencia: Quiebre, No elaborado, No exhibido/operativo u Otro.
- Alertas en Panadería Suc por quiebres recientes y recurrentes.
- Indicadores visuales de referencias normalizadas por evento.
- Resumen de Inteligencia de demanda dentro de Checklist.
- Los refuerzos por quiebre son recomendaciones; MIGA no cambia automáticamente las cantidades.

## Publicación

Subir a GitHub Pages el contenido completo de este paquete conservando la estructura:

- index.html
- README.md
- .nojekyll
- assets/miga-avatar.png
- config/sucursales.js
- firebase/firestore.rules

No requiere cambios en las reglas de Firebase respecto de la versión anterior.
