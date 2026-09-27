# Protocolo de biblioteca común de Control

La biblioteca común reutiliza soluciones sin entregar a una respuesta externa
capacidad de modificar otro equipo. Cada instalación conserva su executor,
permisos, mantenimiento, copia, verificación y reversión.

## Ciclo de una petición

1. **Consulta local.** Control revisa catálogo, servicios, versiones, modelos y
   conocimiento local.
2. **Biblioteca común.** Si no hay una resolución local suficiente, busca en la
   biblioteca pública y devuelve todas las coincidencias técnicas relevantes.
3. **Decisión visible.** Las coincidencias aparecen en una ventana propia con la
   pregunta, solución, compatibilidad, fuentes, experiencia comunitaria y
   advertencias. Elegir una nunca ejecuta cambios.
4. **Validación local.** Control contrasta la propuesta con la instalación y
   crea un plan; los cambios siguen los gates habituales: permiso,
   mantenimiento cuando corresponda, copia, ejecución registrada, verificación
   y reversión.
5. **Ayuda externa.** Solo por petición explícita del usuario, Control realiza
   una búsqueda pública de solo lectura.
6. **Publicación automática.** Una conclusión externa saneada puede publicarse
   de inmediato como una propuesta pública de GitHub. No contiene rutas,
   credenciales, usuarios, registros de terminal ni inventarios particulares.

## Calidad comunitaria

Cada propuesta pública usa reacciones de cuentas GitHub independientes:

- 👍 **Elegida**: encaja con el caso de la persona.
- 🎉 **Verificada**: terminó correctamente tras la comprobación local.
- 👎 **Errónea o no aplicable**: no era compatible o no resolvió el caso.

La popularidad no decide si una propuesta es correcta. Control calcula el
porcentaje de avisos negativos sobre los resultados (`verificada + errónea/no
aplicable`) y no clasifica hasta reunir cinco resultados:

| Avisos negativos | Estado mostrado | Comportamiento |
| --- | --- | --- |
| Menos de 5 resultados | Sin datos suficientes | Se muestra sin recomendación. |
| 0–24% | Respaldada | Se muestra como alternativa normal. |
| 25–49% | Con advertencias | Se muestra un aviso antes de elegir. |
| 50–74% | Riesgo alto | Se muestra, pero exige comprobación profunda. |
| 75–100% | Anulada | No se ofrece como candidata. |

Estos estados se recalculan al leer la biblioteca; no requieren una revisión
manual ni permiten que una persona altere los totales varias veces.

## Datos públicos

Las propuestas se representan como incidencias públicas estructuradas de la
biblioteca, con un identificador, pregunta, solución, etiquetas,
compatibilidad, fuentes y fecha. El índice `knowledge/index.json` conserva la
compatibilidad con instalaciones y entradas anteriores. Una instalación puede
leer la biblioteca sin autenticarse; solo publicar o valorar exige su propia
cuenta GitHub.
