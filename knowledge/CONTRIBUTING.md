# Aportar a la biblioteca común

Control publica automáticamente una propuesta saneada cuando su usuario pulsa
**Publicar automáticamente** tras una búsqueda externa. La publicación queda
como una incidencia pública estructurada, no como un cambio directo de código
ni una orden ejecutable.

Cada instalación usa su propia autenticación de GitHub. No comparte tokens ni
recibe permisos de escritura sobre los equipos de otras personas.

Antes de publicar, Control elimina rutas locales, credenciales, tokens,
nombres de usuario, historial privado y salidas de terminal. La persona que
publica debe comprobar que la solución y sus fuentes pueden hacerse públicas.

La comunidad elige, verifica o marca como errónea/no aplicable cada propuesta.
Control calcula los avisos por porcentaje de resultados y retira las que
alcanzan el 75% de avisos negativos con al menos cinco resultados.
