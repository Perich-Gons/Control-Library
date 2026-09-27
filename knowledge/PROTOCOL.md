# Protocolo de biblioteca común de Control

La biblioteca común permite reutilizar soluciones sin otorgar a una respuesta
externa capacidad de modificar otro equipo.

## Ciclo de una petición

1. **Consulta local.** Control revisa su catálogo operativo, servicios,
   versiones, modelos y resoluciones guardadas localmente.
2. **Biblioteca común.** Si no existe una solución local suficiente, consulta
   el índice público de `Control` con intención, capacidades necesarias y
   versiones relevantes. Devuelve todas las coincidencias encontradas; la interfaz
   las presenta como tarjetas desplegables y permite filtrar por estado, componente
   y compatibilidad.
3. **Decisión visible.** El usuario ve una tarjeta desplegable por cada
   coincidencia. La cabecera muestra título, estado y compatibilidad; el detalle
   contiene la pregunta almacenada, la solución, fuentes, fecha, límites y
   versiones. Puede abrir una propuesta, pedir contraste externo o descartarla.
4. **Validación local.** Elegir una propuesta no la ejecuta. Control compara
   la propuesta con el inventario y las políticas de esa instalación, genera
   un plan y aplica los gates habituales: permiso, mantenimiento cuando
   proceda, copia, ejecución registrada, verificación y reversión.
5. **Ayuda externa.** Solo si el usuario lo solicita, Control realiza la
   búsqueda externa de solo lectura.
6. **Aportación.** La respuesta externa se convierte en un borrador saneado.
   El usuario puede proponerlo a la biblioteca desde su fork mediante Pull
   Request.

## Estados de una entrada

- `draft`: borrador local, aún no compartido.
- `proposed`: propuesta pública pendiente de revisión.
- `verified`: resolución aceptada y comprobada por mantenedores.
- `superseded`: resolución sustituida por otra más reciente.
- `rejected`: propuesta no utilizable; se conserva solo en la trazabilidad de
  contribución, no se ofrece como solución.

Las propuestas `proposed` pueden mostrarse como alternativas, claramente
marcadas. Solo una entrada `verified` puede ser recomendada por defecto, y
ninguna entrada se ejecuta sin validar la compatibilidad local.

## Índice público

El repositorio `Control` mantendrá `knowledge/index.json`. Cada registro
incluye un identificador, título, resumen, etiquetas semánticas, estado,
versiones/entornos compatibles, enlace a la entrada, fuentes y fecha de
revisión. Esto permite buscar sin descargar todo el repositorio.

No se incluyen rutas locales, credenciales, tokens, nombres de usuarios,
registros de terminal ni inventarios particulares de una instalación.

## Uso comunitario

Cada resolución publicada tendrá una ficha comunitaria vinculada en GitHub. Al
seleccionarla, Control podrá registrar una reacción del usuario autenticado:

- **Elegida**: la persona la consideró adecuada para su caso.
- **Verificada en su equipo**: la persona confirmó que terminó correctamente
  tras las comprobaciones locales.
- **No aplicable**: la propuesta no era compatible o no resolvió su caso.

GitHub cuenta una reacción por cuenta y resolución, por lo que el total
representa usuarios distintos y no pulsaciones repetidas. Al buscar de nuevo,
Control mostrará los tres contadores junto a cada tarjeta, por ejemplo:
`Elegida por 20 usuarios · Verificada por 16 · No aplicable para 2`.

Los contadores ayudan a decidir, pero no sustituyen la validación de versión,
hardware, permisos y políticas de cada instalación.
