Reflexion sobre Git Worktree

1. Ventajas de Worktree
La principal ventaja que le veo frente a cambiar de rama normal es que no tengo que andar guardando los cambios con stash si tengo algo a medias. Simplemente abro otra carpeta y listo. 
Comparado con clonar el repo varias veces, lo bueno es que no ocupa tanto espacio porque comparten la carpeta .git, y si descargo algo en una rama ya lo tengo en todas.

2. Situaciones reales
- Una situacion seria si estoy programando una cosa y de repente me piden revisar un bug en otra rama. En vez de parar lo que estoy haciendo, abro un worktree en otra carpeta, arreglo el bug y sigo con lo mio.
- Otra seria para probar cosas. Si quiero ver si algo funciona en una rama distinta sin romper mi entorno actual, un worktree me permite tener las dos cosas abiertas a la vez.

3. Buenas practicas
- Yo pondria nombres claros a las carpetas, como wt-nombre-rama, para saber que son temporales.
- Tambien esta bien sacarlas fuera de la carpeta principal del proyecto para no liarse.
- Y de vez en cuando usar git worktree prune por si he borrado alguna carpeta a mano y git todavia se cree que esta ahi.
