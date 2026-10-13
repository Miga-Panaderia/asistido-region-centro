# MIGA · Multizona v67.2 · Punto Caliente diferenciado

Base funcional: **MIGA v64 (alertas inmediatas) + v64.1 (ausencia por día) + revisión de referencias especiales**.

## Funcionalidad conservada
- **Alerta evento** marcada por Administrador se visualiza de inmediato en amarillo en la Hoja del Panadero y mantiene la lógica de próximo ciclo.
- Las referencias con ausencia en Checklist se señalan con un punto rojo discreto y el día exacto se resalta en rojo en Hoja del Panadero.
- Si coinciden evento y ausencia, la fila conserva el contexto amarillo del evento y la celda del día ausente queda roja por encima.
- Se conservan la tipografía y la estructura multizona de Firebase/Firestore y GitHub Pages.
- No se modifican ventas Prisma, fórmulas, sugeridos, coeficientes, cronogramas ni reglas de cálculo del padrón original.

## Referencias de Checklist · v67.2
- **Punto Caliente:** se administra desde **Administrador General → Punto Caliente por elaboradora**. Cada referencia queda asignada a una elaboradora habilitada.
- **Selección por sucursal:** en **Parámetros Suc**, cada sucursal elige la elaboradora que la abastece. Las referencias de Punto Caliente asignadas a esa elaboradora se incorporan al Checklist original.
- **Referencias que no son de elaboración:** se registran por sucursal en **Parámetros Suc** y también aparecen en Checklist.
- Los dos tipos de referencias especiales se muestran dentro del Checklist original, junto a las referencias tradicionales, pero con etiquetas distintivas. Se mantienen fuera del padrón original y no participan de los cálculos de producción.
- Las referencias de Punto Caliente se guardan en la configuración global sincronizada por Firebase; la elaboradora elegida y las referencias exclusivas de Checklist se guardan en la configuración de cada sucursal.
- Si se encuentran referencias de Punto Caliente heredadas de la versión anterior, se conservan durante la migración. Cuando no puede inferirse una elaboradora sin ambigüedad, quedan como **Sin asignar** para que el Administrador General las clasifique.

## Estructura
- `index.html`
- `README.md`
- `.nojekyll`
- `assets/miga-avatar.png`
- `config/sucursales.js`
- `firebase/firestore.rules`
