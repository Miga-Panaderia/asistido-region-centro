# MIGA · Pedidos Asistidos de Panadería · Multizona

Proyecto preparado para publicar directamente con **GitHub Pages**.

## Estructura

- `index.html` → aplicación MIGA.
- `config/sucursales.js` → padrón de zonas y sucursales.
- `assets/miga-avatar.png` → avatar de MIGA.
- `.nojekyll` → evita procesamiento Jekyll innecesario en GitHub Pages.

## Padrón incluido

Se cargaron 5 zonas y 62 sucursales:

- **NEUQUEN INTERIOR**: 14 sucursales
- **NEUQUEN CIUDAD**: 14 sucursales
- **RIO NEGRO**: 16 sucursales
- **TRELEW**: 10 sucursales
- **VIEDMA**: 8 sucursales

## Elaboradoras

La versión Multizona **no establece ninguna elaboradora por defecto**.

1. Ingresá como **Administrador General**.
2. Abrí **Plan Elaboradora**.
3. Usá **＋ / − Elaboradoras**.
4. Elegí manualmente qué sucursales serán elaboradoras.
5. En cada elaboradora, definí las **Sucursales a producir**. Se permiten destinos de cualquier zona.
6. Configurá el WhatsApp de cada elaboradora desde el Menú Admin.

## Publicar en GitHub Pages

1. Creá un repositorio nuevo en GitHub.
2. Subí **el contenido de esta carpeta** a la raíz del repositorio.
3. En GitHub abrí **Settings → Pages**.
4. En *Build and deployment*, elegí **Deploy from a branch**.
5. Seleccioná la rama `main` y la carpeta `/ (root)`.
6. Guardá. GitHub mostrará la dirección pública cuando termine el deploy.

## Datos y sincronización

Esta primera versión online sigue utilizando `localStorage`, igual que la versión offline:

- El **código** se actualiza para todos cuando publicás una nueva versión en GitHub.
- La **configuración que guarda cada sucursal** queda en el navegador/PC donde se modificó.
- Los cambios todavía **no se sincronizan entre distintas PCs**.

El paso siguiente para sincronización real es conectar el mismo proyecto a **Firebase/Firestore**.

## Seguridad importante

GitHub Pages sirve archivos estáticos al navegador. Por eso, las contraseñas locales y la clave de Administrador General de esta versión **no constituyen seguridad fuerte para una publicación pública**: una persona con conocimientos técnicos puede inspeccionar el JavaScript o borrar el almacenamiento local.

Antes de usarlo como sistema público con datos sensibles o permisos reales, conviene migrar la autenticación a Firebase Authentication y las reglas de acceso a Firestore.

## Actualizar zonas o sucursales

El padrón está centralizado en `config/sucursales.js`. Esto evita tener que modificar toda la lógica de MIGA para sumar una sucursal en el futuro.

## Respaldo y restauración

El **Administrador General** dispone de una tarjeta **Respaldo y Restauración**.

- **Descargar respaldo completo:** genera un `.json` con todas las configuraciones MIGA almacenadas en ese navegador y las ventas cargadas.
- **Restaurar desde respaldo:** recupera la configuración desde ese archivo.
- **Restaurar sucursal actual:** vuelve únicamente la sucursal seleccionada a sus parámetros y cronograma iniciales.

MIGA registra el respaldo mensual como pendiente o realizado. Desde el día 28 se considera período de cierre y se recomienda descargar una copia.

> Importante: mientras MIGA use GitHub Pages + `localStorage`, los datos son propios de cada navegador/PC. Guardá el archivo de respaldo fuera de la PC. Cuando se conecte Firebase, el respaldo podrá centralizarse.

## Plan Elaboradora por zona

En **Plan Elaboradora**, el flujo ahora es:

1. **Zona elaboradora**
2. **Sucursal elaboradora**
3. **Sucursales a producir**

La pre-solapa **Zona elaboradora** muestra solamente las zonas que tienen al menos una elaboradora habilitada.  
Al elegir una zona, MIGA filtra las elaboradoras visibles de esa zona.  
Si se activa una elaboradora de otra zona, la pre-solapa se sincroniza automáticamente.

## Vista limpia de Plan Elaboradora

Cuando se abre la solapa **Plan Elaboradora**, MIGA oculta la barra general de sucursal
(MIGA, archivo de ventas, Zona, Sucursal, Guardar/WhatsApp, Inicio y Administrador general).

En esa vista quedan únicamente los controles propios del Plan Elaboradora:
**Zona elaboradora → Sucursal elaboradora → Fecha de producción → Sucursales a producir**.

Al volver a cualquier otra solapa, la barra general aparece nuevamente.

## Padrón de referencias por zona

El bloque **Padrón de Referencias** ahora permite trabajar por tres alcances:

- **Sucursal actual**
- **Zona seleccionada**
- **Todas las sucursales**

Cuando se elige **Zona seleccionada**, aparece el selector **Zona del padrón** y la grilla muestra un **listado consolidado por zona**.
Además de los datos del artículo, se informa en cuántas sucursales de ese alcance existe cada referencia.

Las operaciones **Agregar / Editar / Eliminar / Importar referencias** respetan el alcance elegido.

## Coeficiente rápido

La columna **Coef.** de **Panadería Suc** ahora utiliza un selector desplegable.

Valores rápidos:
`0% · 5% · 10% · 15% · 20% · 25% · 30% · 40% · 50%`

También existe **Personalizado…** para ingresar cualquier otro porcentaje.

El impacto sobre la producción es inmediato al seleccionar el valor. El guardado de la configuración continúa realizándose automáticamente en segundo plano, evitando la espera que existía al salir de cada casillero.

## Botón flotante de MIGA

El acceso al asistente ya no se muestra como un globito genérico.

Ahora MIGA aparece como un **botón flotante circular con el logo/avatar oficial**, ubicado en una posición más limpia:
- **Escritorio:** esquina superior derecha
- **Móvil:** esquina inferior derecha

En **Plan Elaboradora** también se reposiciona automáticamente para no mezclarse con la interfaz principal.

## Precarga neutral

La pantalla inicial de MIGA ya no muestra códigos, nombres de sucursal ni zona durante la carga.
Los mensajes son generales: inicialización, configuración, parámetros, padrón, cálculo y preparación de interfaz.
