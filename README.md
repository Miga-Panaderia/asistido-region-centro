# MIGA · Multizona v67.3 · Administración central de referencias especiales

Base funcional: **MIGA v64 (alertas inmediatas) + v64.1 (ausencia por día) + referencias especiales de Checklist**.

## Funcionalidad conservada
- **Alerta evento** marcada por Administrador se visualiza de inmediato en amarillo en la Hoja del Panadero y mantiene la lógica de próximo ciclo.
- Las referencias con ausencia en Checklist se señalan con un punto rojo discreto y el día exacto se resalta en rojo en Hoja del Panadero.
- Si coinciden evento y ausencia, la fila conserva el contexto amarillo del evento y la celda del día ausente queda roja por encima.
- Se conservan la tipografía y la estructura multizona de Firebase/Firestore y GitHub Pages.
- No se modifican ventas Prisma, fórmulas, sugeridos, coeficientes, cronogramas ni reglas de cálculo del padrón original.

## Referencias especiales de Checklist · v67.3
- **Punto Caliente:** se administra exclusivamente desde **Administrador General → Punto Caliente por elaboradora**. Cada referencia se asigna a una elaboradora habilitada.
- **Asignación automática:** el Checklist identifica qué elaboradora abastece a cada sucursal usando la configuración de destinos de **Plan Elaboradora**. La sucursal no debe seleccionar ni configurar una elaboradora.
- **Referencias no elaboradas:** se administran exclusivamente desde **Administrador General → Referencias exclusivas de Checklist · No elaboración**, seleccionando la sucursal correspondiente.
- Ambos tipos se incorporan a la lista habitual del Checklist y se diferencian con sus etiquetas. Si el artículo ya existe en el padrón o en otra referencia, el Checklist conserva una sola fila y añade la clasificación correspondiente.
- Las referencias especiales no se muestran como cuadros de configuración en Parámetros Suc, no se agregan al padrón original y no intervienen en los cálculos de producción.
- Las referencias de Punto Caliente se guardan en la configuración global sincronizada por Firebase. Las referencias exclusivas de Checklist se guardan en la configuración de la sucursal que selecciona el Administrador General.
- Si hay referencias de Punto Caliente heredadas de la versión anterior, se conservan durante la migración. Las referencias se muestran solo a las sucursales que figuran explícitamente como destinos de su elaboradora.

## Estructura
- `index.html`
- `README.md`
- `.nojekyll`
- `assets/miga-avatar.png`
- `config/sucursales.js`
- `firebase/firestore.rules`
