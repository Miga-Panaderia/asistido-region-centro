# MIGA · Multizona v64.1 · Ausencia por día + indicador discreto

Versión basada en **v63 EVENTOS UI FUENTE**.

## Cambios v64
- **Alerta evento** marcada por Administrador se guarda como antes y ahora se visualiza **de inmediato en amarillo** en la Hoja del Panadero de las sucursales de esa zona.
- La alerta de evento **mantiene la lógica de próximo ciclo**: al iniciar un nuevo ciclo se traslada a `cycleAlerts` y la cola pendiente se limpia.
- Las referencias con **Ausencia** marcada explícitamente en Checklist ya no pintan toda la fila: se resalta **solo la celda del día exacto** en Hoja del Panadero.
- La descripción de la referencia muestra un **indicador discreto (punto rojo)** cuando existe ausencia, en lugar de la etiqueta textual "AUSENCIA".
- Si una referencia tiene simultáneamente alerta de evento y ausencia, la fila mantiene el contexto de **evento** y la ausencia queda indicada por el **punto rojo** y por la **celda diaria en rojo**.
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
