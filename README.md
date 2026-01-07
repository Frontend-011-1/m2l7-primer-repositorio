# Proyecto para aprender a usar Git y GitHub

## Tecnologías utilizadas en el proyecto

- HTML
- Git para control de versiones
- GitHub para almacenar nuestro repositorio en la web
- Uso de la terminal

---

## Comandos útiles

### git init

Para inicializar un repositorio local (se hace una vez por proyecto!)

### git add

Imaginemos que estamos preparando una maleta para un viaje. `git add` es como meter los objetos (archivos modificados o nuevos) en la mochila antes de salir. Pero todavía no los enviamos, solo están preparados para el viaje.

- `git add index.html`: Prepara ese archivo en específico
- `git add .`: Prepara los archivos modificados del directorio actual

### git commit

Una vez que tienes todo en la mochila, `git commit` es como cerrar la mochila y tomar una foto del estado actual para recordar lo que llevas. Guarda los cambios preparados en el historial de Git con un mensaje descriptivo.

### Commits y restauración

Usar convención de nombrado para commits (lo mimso para ramas): feat para funcionalidades, fix para corregir un error, docs para cambios en documentacion, style para cambios que no afectan lógica (espacios, formateo de codigo, puntos y coma, NO ES CSS), refactor para cambios en el código para mejorarlo pero no añaden nuevas funcionalidades ni arreglan bugs.

#### git checkout -- <archivo>

1. Sirve para descartar cambios hechos en un archivo del directorio de trabajo y devolverlo al estado exacto del último commit (botón de arrepentimiento)
2. Borrar una sección completa del index.html, guardaste el archivo y nada funciona. Para dejarlo como antes:
3. `git checkout -- index.html`
4. Git va al último commit o al staging área si ya habías hecho un `git add .`

#### Git restore <archivo> - versión moderna

1. Agregar un cambio al index.html
2. Se guarda el archivo, se ve el navegador, pero se ve mal o quedó como no debía quedar. Ctrl + z ya no funciona
3. Verificar qué archivo sufrió cambios con `git status` --> `modificados: index.html`
4. Para deshacer los cambios en el archivo y volver a cambios del último commit: `git restore index.html`
5. Si es que habías hecho `git add .`:
   - `git restore --staged index.html`
   - `git restore index.html`

#### Otros para restaurar commits

1. Corregir último commit. Por ejmplo el commit está bien pero se te olvidó agregar un archivo o escribiste mal el mensaje: `git commit --ammend -m "Nuevo y mejor mensaje"`. Si olvidaste un archivo es importante usar de nuevo `git add .`.

#### Restaurar commit anterior

1. Hiciste un commit con cambios
2. `git revert <hash-del-commit>`
3. Resolver conflictos en editor (Aceptar entrante para volver a cambios anteriores)
4. Git add y commit

### Cambiar nombre

1. `git mv archivo_antiguo archivo_nuevo`
2. git add y commit

### Ramas

1. `git branch nuevo-nombre` para crear rama
2. `git checkout nuevo-nombre` para cambiarse a esa rama
3. Hacer algún cambio
4. add y commit en nueva rama
5. `git checkout main` para volver a rama main
6. `git merge nuevo-nombre` para fusionar los cambios de la nueva rama con main

### Etiquetas

1. Seleccionar un hash de un commit para dejar una etiqueta en ese commit
2. `git tag v1.0 <hash>`
3. Se puede comprobar con `git log` y oneline

## Resolución de conflictos

1. Crear rama mejora-titulo
2. Cambiar h1 a "Pésimamente mal escrito"
3. Cambiarse a main branch
4. Cambiar el mismo h1: "Título perfectamente bueno"
5. Hacer merge de la rama mejora-titulo
6. Resolver cambios en main.html
7. `<<<<<<< HEAD:` Aquí empieza tu versión (lo que tienes actualmente).
8. `=======:` Esta es la línea divisoria.
9. `>>>>>>>` mejora-titulo: Aquí termina la versión de tu compañero.
10. Hay que decidir qué versión se queda. Preferir opción "Resolver en el editor"
11. git add y commit
