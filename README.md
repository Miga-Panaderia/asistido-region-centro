# MIGA · Multizona v62 · Alertas para el próximo ciclo

Versión basada en v60 con una lógica de alerta visual, sin modificar los sugeridos de producción.

## Novedades

- Admin General puede marcar referencias del padrón como **Evento próximo ciclo**.
- Al iniciar el ciclo, esas referencias quedan guardadas para las sucursales de su zona y la cola de eventos se limpia.
- Checklist diferencia explícitamente **Presente**, **Ausente** y **Sin marcar**.
- Las referencias marcadas Ausente durante el ciclo se transfieren como antecedente al ciclo siguiente.
- En **Hoja del Panadero Suc**:
  - amarillo = posible venta extraordinaria / evento,
  - rojo = ausencia explícita en el ciclo anterior,
  - rojo tiene prioridad si una referencia cumple ambas condiciones.
- Los colores también se conservan al imprimir la Hoja del Panadero.

La venta real de Prisma y el cálculo del sugerido no son modificados por estas alertas.

No requiere cambios en las reglas de Firestore: utiliza las colecciones y permisos existentes.
