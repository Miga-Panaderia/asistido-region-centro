# MIGA · Multizona v71.2 · Limpieza de cronogramas

Base funcional: **MIGA v64 (alertas inmediatas) + v64.1 (ausencia por día) + referencias especiales de Checklist**.

## Funcionalidad conservada
- **Alerta evento** marcada por Administrador se visualiza de inmediato en amarillo en la Hoja del Panadero y mantiene la lógica de próximo ciclo.
- Las referencias con ausencia en Checklist se señalan con un punto rojo discreto y el día exacto se resalta en rojo en Hoja del Panadero.
- Si coinciden evento y ausencia, la fila conserva el contexto amarillo del evento y la celda del día ausente queda roja por encima.
- Se conservan la tipografía y la estructura multizona de Firebase/Firestore y GitHub Pages.
- No se modifican ventas Prisma, fórmulas, sugeridos, coeficientes, cronogramas ni reglas de cálculo del padrón original.

## Referencias especiales de Checklist · v71.1
- **Punto Caliente:** se administra exclusivamente desde **Administrador General → Punto Caliente por elaboradora**. Cada referencia se asigna a una elaboradora habilitada.
- **Asignación automática:** el Checklist identifica qué elaboradora abastece a cada sucursal usando la configuración de destinos de **Plan Elaboradora**. La sucursal no debe seleccionar ni configurar una elaboradora.
- **Referencias no elaboradas:** se administran exclusivamente desde **Administrador General → Referencias exclusivas de Checklist · No elaboración**, seleccionando la zona correspondiente; se aplican a todas las sucursales de esa zona.
- Ambos tipos se incorporan a la lista habitual del Checklist y se diferencian con sus etiquetas. Si el artículo ya existe en el padrón o en otra referencia, el Checklist conserva una sola fila y añade la clasificación correspondiente.
- Las referencias especiales no se muestran como cuadros de configuración en Parámetros Suc, no se agregan al padrón original y no intervienen en los cálculos de producción.
- Las referencias de Punto Caliente se guardan en la configuración global sincronizada por Firebase. Las referencias exclusivas de Checklist se guardan en la configuración central por zona y se sincronizan por Firebase.
- Si hay referencias de Punto Caliente heredadas de la versión anterior, se conservan durante la migración. Las referencias se muestran solo a las sucursales que figuran explícitamente como destinos de su elaboradora.

## Corrección v71.1
- Se restauraron las constantes y variables del módulo Plan Elaboradora que faltaban en el paquete anterior. Esto recupera la lectura de elaboradoras habilitadas, los destinos, los teléfonos de WhatsApp y el padrón de Punto Caliente.
- La lista de teléfonos también recupera los códigos guardados aunque una elaboradora no esté actualmente habilitada.
- Las referencias exclusivas del Checklist ahora se administran por zona, se sincronizan como configuración central y se incluyen automáticamente en el Checklist de todas las sucursales de esa zona.
- Se migran una sola vez las referencias exclusivas que estuvieran guardadas en configuraciones individuales de sucursal, evitando que reaparezcan tras eliminarlas.

## Estructura
- `index.html`
- `README.md`
- `.nojekyll`
- `assets/miga-avatar.png`
- `config/sucursales.js`
- `firebase/firestore.rules`


## Mejora v71.2 · Limpiar cronogramas
- Cada referencia del padrón tiene un botón de limpieza de línea junto al botón **✓ 7/7**. Borra los siete indicadores de días de esa referencia, sin eliminar el artículo del padrón.
- Se agregó **Borrar todos los 1** sobre el padrón para limpiar los días marcados de todas las referencias de la sucursal de una sola vez.
- Ambas acciones piden confirmación, requieren acceso autorizado a la sucursal y guardan los cambios mediante el mecanismo existente de sincronización.
- Estas acciones solo limpian los valores del cronograma; no eliminan referencias, no alteran las ventas ni cambian los cálculos ajenos al cronograma.
