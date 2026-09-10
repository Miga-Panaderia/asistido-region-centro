# MIGA · Multizona v64 · Alertas visibles inmediatas

Versión basada en **v63 EVENTOS UI FUENTE**.

## Cambios v64
- **Alerta evento** marcada por Administrador se guarda como antes y ahora se visualiza **de inmediato en amarillo** en la Hoja del Panadero de las sucursales de esa zona.
- La alerta de evento **mantiene la lógica de próximo ciclo**: al iniciar un nuevo ciclo se traslada a `cycleAlerts` y la cola pendiente se limpia.
- Las referencias con **Ausencia** marcada explícitamente en Checklist se visualizan **en rojo** en Hoja del Panadero.
- Si una referencia tiene simultáneamente alerta de evento y ausencia, **rojo tiene prioridad**.
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
