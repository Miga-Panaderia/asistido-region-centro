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

## Ajustes para celular

Se mejoró la experiencia móvil con:

- desplazamiento táctil reforzado en tablas anchas;
- barra superior y herramientas con mejor acomodo en pantallas chicas;
- pestañas inferiores con desplazamiento horizontal;
- botón de MIGA más chico y reubicado en móvil para no tapar la parte inferior;
- ventana del asistente reposicionada en móvil.

## Firebase · Fase 1

Proyecto Firebase conectado:

- Project ID: `miga-panaderia-region-centro`
- Authentication: correo/contraseña
- Administrador técnico: `admin@miga-panaderia.app`
- Firestore: base `(default)`

### Antes de probar

1. En Firebase → Firestore → **Reglas**, pegá el contenido de `firebase/firestore.rules` y publicalo.
2. En Firebase → Authentication → **Settings / Configuración** → **Dominios autorizados**, agregá:
   `miga-panaderia.github.io`
3. Subí esta versión de MIGA a GitHub Pages.

### Primera inicialización

Ingresá como **Administrador General** usando la contraseña que creaste en Firebase.

Después abrí:

**Menú Admin → Firebase · Sincronización → Subir datos actuales a Firebase**

Hacelo desde la PC/navegador que tenga la configuración correcta. Esta operación inicializa la nube.

Después podés abrir MIGA en otro dispositivo, entrar como Admin General y elegir **Traer datos desde Firebase**. Una vez conectada, la sincronización queda activa mientras dure la sesión del Admin.

### Importante

Esta es la **Fase 1**: solamente el Administrador General tiene permiso de Firestore.  
La siguiente etapa será crear la autenticación de las sucursales y reglas para que cada una pueda leer/escribir únicamente lo que le corresponde.

## Padrón maestro de referencias por zona

Desde esta versión, cada zona maneja un padrón maestro independiente:

- NEUQUEN INTERIOR
- NEUQUEN CIUDAD
- RIO NEGRO
- TRELEW
- VIEDMA

Las sucursales heredan automáticamente el padrón de su zona.  
La sucursal conserva solamente sus particularidades de cada referencia, especialmente **Coef.** y **Cronograma**.

### Operaciones del Admin General

En **Menú Admin → Padrón de Referencias por Zona**:

- Agregar referencia
- Editar referencia
- Eliminar referencia
- Importar / actualizar desde Excel
- Reemplazar padrón completo de una zona desde Excel

Al reemplazar:

- una referencia que continúa conserva Coef. y Cronograma en cada sucursal;
- una referencia nueva entra con Coef. `0%` y cronograma vacío;
- una referencia eliminada deja de formar parte de todas las sucursales de esa zona.

### Firebase

Se agrega la colección:

`miga_zone_refs`

Antes de usar esta versión en producción, actualizá nuevamente **Firestore → Reglas** con el archivo `firebase/firestore.rules` de esta versión y publicalo.

## Cambio de contraseña del Administrador General

El **Menú Admin** incorpora la sección **Seguridad Admin General**.

Para cambiar la contraseña se solicita:

1. Contraseña actual
2. Nueva contraseña
3. Repetición de la nueva contraseña

MIGA reautentica al usuario contra Firebase antes de ejecutar el cambio.  
La contraseña nueva se actualiza con Firebase Authentication y **no se guarda en localStorage ni dentro del HTML**.

El cambio de contraseña no modifica:

- UID del Administrador General
- reglas de Firestore
- configuración de MIGA
- repositorio de GitHub

No es necesario modificar ni volver a publicar las reglas de Firestore por esta función.

## Firebase por sucursal · tiempo real

Esta versión habilita el esquema definitivo:

**Sucursal + contraseña → Firebase → sincronización automática**

Cada sucursal utiliza internamente una cuenta técnica de Firebase. El usuario no necesita conocer ni escribir ningún correo.

### Accesos de sucursal

Desde **Administrador General → Accesos Firebase por Sucursal**:

- una clave en una sucursal sin acceso crea su cuenta Firebase;
- una nueva clave en una sucursal activa restablece su acceso;
- el acceso anterior queda deshabilitado;
- el botón `✕` deshabilita el acceso online.

### Sincronización

Una vez autenticada una sucursal:

- carga su configuración desde Firebase;
- Coef. y Cronograma se guardan automáticamente;
- otro dispositivo con la misma sucursal recibe los cambios sin recargar;
- el indicador superior muestra **☁ Sincronizado**.

Si esa sucursal es elaboradora, MIGA escucha también las sucursales asignadas en **Plan Elaboradora**, por lo que sus modificaciones se reflejan en tiempo real.

### Móvil

En pantallas pequeñas:

- Panadería Suc y Hoja del Panadero ya no dejan Artículo/Descripción inmovilizados;
- toda la tabla puede desplazarse horizontalmente;
- Plan Elaboradora compacta las columnas iniciales y oculta Marca, Aptitud y Bto para acercar las columnas de sucursal.

### Reglas de Firestore

Antes de usar esta versión, volver a publicar el archivo:

`firebase/firestore.rules`

en **Firebase → Firestore → Reglas**.

## MIGA · modo guiado

MIGA deja de aceptar preguntas libres.

El campo de texto se habilita solamente cuando MIGA pregunta:

**¿Con quién tengo el gusto?**

Después de guardar el nombre, el campo desaparece y se muestran exclusivamente botones de preguntas que MIGA tiene programadas para responder.

Las preguntas están agrupadas en:

- **En esta sección**: cambia automáticamente según la solapa activa.
- **Mi sucursal**
- **Ayuda y acceso**
- **Un poco de MIGA**

Si se elige **No soy [nombre]**, vuelve a habilitarse temporalmente el campo para escribir el nuevo nombre.

Esto evita que el usuario escriba consultas fuera del alcance del asistente local.

## v16 · Realtime reforzado + PIN de sucursal

MIGA ya no solicita el PIN automáticamente apenas se abre la página.

Si ese dispositivo ya había iniciado sesión con una sucursal, Firebase restaura la sesión y reactiva los cambios en tiempo real de forma automática. En un dispositivo nuevo, el usuario puede tocar **☁ Ingresar Suc. XXX** o intentar modificar un dato; recién en ese momento se solicita el PIN.

El PIN visible de sucursal es numérico y acepta entre **3 y 12 dígitos**. Firebase utiliza internamente una credencial técnica más larga, por lo que el usuario solamente necesita recordar su PIN.

Las escrituras de una sucursal se envían en orden y el estado superior diferencia **Guardando**, **Sincronizado** y **Error de sincronización**.

Los accesos creados con versiones anteriores pueden seguir funcionando con su clave anterior. Para comenzar a usar PIN de 3 dígitos, restablecer el acceso de esa sucursal desde Admin General.

También se eliminó de MIGA el grupo recreativo y los chistes; el asistente guiado queda enfocado en funciones operativas.

## v17 · Reconexión automática de Firebase

Esta versión corrige el caso en el que un dispositivo ya tenía sesión iniciada pero, después de quedar en segundo plano o suspendido por el navegador, no recibía modificaciones hechas desde otro dispositivo hasta reconectarse manualmente.

MIGA ahora:

- mantiene la sesión Firebase existente;
- al volver a primer plano trae el último estado de Firestore;
- reinicia automáticamente los listeners;
- hace lo mismo al recuperar conexión a Internet;
- detecta restauraciones desde la caché del navegador;
- realiza una comprobación silenciosa si la pestaña visible pasa demasiado tiempo sin actividad del listener.

La reconexión no pide nuevamente el PIN mientras la sesión Firebase continúe siendo válida.

Flujo esperado:

**otro dispositivo modifica → Firebase → MIGA vuelve/permanece activa → catch-up automático → último dato visible → listener activo otra vez**.

## v18 · MIGA explica cada hoja + rueda del mouse

### ¿Qué hace esta hoja?

Se corrigió la lógica que podía reemplazar la respuesta correcta por el mensaje genérico de consulta no reconocida.

MIGA ahora identifica la solapa activa mediante su ID interno y siempre tiene una explicación breve para:

- Parámetros Suc
- Panadería Suc
- Ventas Prisma Suc
- Hoja del Panadero Suc
- Plan Elaboradora

Las explicaciones indican el objetivo de la hoja y continúan siendo válidas aunque todavía no existan ventas, cálculos o sucursales asignadas.

### Scroll con rueda del mouse

Se agrega manejo explícito de rueda para las tablas principales:

- rueda normal: desplazamiento vertical;
- `Shift + rueda`: desplazamiento horizontal;
- si no existe recorrido vertical y sí horizontal, la rueda avanza por las columnas;
- trackpads con desplazamiento horizontal también funcionan.

Se aplica a Panadería Suc, Ventas Prisma, Hoja del Panadero, Plan Elaboradora y padrón de Parámetros.

## v19 · Ocultar selector de sucursales a producir

En **Plan Elaboradora**, el bloque **SUCURSALES A PRODUCIR** y los botones **Todas / Ninguna** ahora son herramientas exclusivas de edición.

- Se muestran únicamente mientras está activo **Administrador General**.
- Al salir del Administrador General desaparecen inmediatamente.
- La selección guardada continúa utilizándose para calcular el Plan Elaboradora.
- Los usuarios normales solo ven el resultado del plan, no el panel de configuración.

## v20 · Scroll natural con rueda

Se normaliza el comportamiento de escritorio:

- **Parámetros Suc:** la rueda funciona con el puntero en cualquier parte de la hoja.
- **Panadería Suc / Ventas / Hoja del Panadero / Plan Elaboradora:** la rueda normal queda reservada al desplazamiento vertical.
- Al llegar abajo de una tabla, la rueda **ya no comienza a mover automáticamente hacia la derecha**.
- El desplazamiento horizontal queda disponible mediante:
  - `Shift + rueda`;
  - gesto horizontal de trackpad;
  - barra/navegador horizontal de la hoja;
  - arrastre táctil en celular.

Esto evita cambios inesperados de dirección al llegar al final vertical.

## v21 · Ajustes móviles en Plan Elaboradora y Hoja del Panadero

### Plan Elaboradora
- En celular, las solapas de **Sucursales elaboradoras** muestran solo el **código** (por ejemplo `050`, `188`, `357`).
- El encabezado **PADRÓN PANADERIA...** se vuelve más compacto y adaptable para evitar desbordes visuales.

### Hoja del Panadero Suc
- En celular, el encabezado de la tabla deja de comportarse como **sticky**.
- Al hacer scroll vertical ya no queda fija la fila desde **U/M** en adelante.

## v22 · Panadería Suc sin encabezado fijo en celular

En vista móvil, toda la fila de encabezados de **Panadería Suc** deja de usar posición fija.

Ahora Art., Descripción, Marca, Aptitud, U/M, Bto, Consumo, Coef. y el resto del encabezado suben junto con la tabla al hacer scroll vertical.
