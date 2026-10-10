# MIGA · Multizona v67 · Referencias especiales

Base funcional: **MIGA v64 (alertas inmediatas) + v64.1 (ausencia por día e indicador discreto)**.

## Funcionalidad conservada de v64 y v64.1
- **Alerta evento** marcada por Administrador se guarda como antes y ahora se visualiza **de inmediato en amarillo** en la Hoja del Panadero de las sucursales de esa zona.
- La alerta de evento **mantiene la lógica de próximo ciclo**: al iniciar un nuevo ciclo se traslada a `cycleAlerts` y la cola pendiente se limpia.
- Las referencias con ausencia en Checklist se señalan con un **punto rojo discreto** y el día exacto se resalta en rojo en Hoja del Panadero.
- Si coinciden evento y ausencia, la fila conserva el contexto amarillo del evento y la celda del día ausente queda roja por encima.
- Al ingresar a **Hoja del Panadero** se fuerza un nuevo render para leer el estado más reciente.
- Los cambios de alerta de evento y de ausencia actualizan la vista de Hoja del Panadero sin modificar los cálculos.
- Se conserva la tipografía introducida en v63.
- **No se modifican** ventas Prisma, fórmulas, sugeridos, coeficientes, cronogramas ni reglas de cálculo.
- Se conserva la estructura de Firebase/Firestore y del proyecto GitHub Pages.

## Estructura
- `index.html`
- `README.md`
- `.nojekyll`
- `assets/miga-avatar.png`
- `config/sucursales.js`
- `firebase/firestore.rules`


## Cambios v67 · Referencias especiales por sucursal
- Nueva hoja **Referencias especiales** con dos cuadros independientes por sucursal.
- **Puntos calientes**: referencias fuera del padrón original, con días configurables; se muestran en un bloque separado del Plan Elaboradora cuando la sucursal está seleccionada como destino y el día está activo. No se incorporan al padrón ni a los totales/cálculos estándar.
- **Referencias exclusivas de Checklist**: se agregan al control de presencia por fecha y turno, sin ingresar al padrón de elaboración ni a sus cálculos.
- Ambas listas se guardan en la configuración de la sucursal y siguen el mecanismo de sincronización de MIGA.
- Se conserva el resaltado de ausencia por día y el punto rojo discreto en la referencia.
