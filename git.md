# Git

#### Activar que se firmen todos los commits
```console
git config --global commit.gpgsign true
```

#### Firmar un commit determinado (-S)
```console
git commit -S -m "YOUR_COMMIT_MESSAGE"
```

#### Migrar el directorio de un repositorio a otro (y otra ubicación) manteniendo el historial de cambios
1. Creamos un directorio llamado por ejemplo migration
2. Dentro de migration creamos dos directorios uno llamado source y otro llamado target
3. Dentro de source clonamos el repo que tiene todo y del que queremos extraer el diectorio
4. Una vez clonado y dentro del directorio, eliminamos el origin para evitar subir cosas por error
```console
git remote rm origin
```
5. Filtramos todo el historial del git manteniendo solo la carpeta que nos interesa
```console
git filter-branch --subdirectory-filter nombre-subdirectorio -- --all
```
6. Eliminamos los datos no deseados
```console
git reset --hard
git gc --aggressive 
git prune
git clean -fd
``` 
7. Esto dejara el contenido de la carpeta en el directorio raiz con lo que aprovechamos para moverlo a la carpeta definitiva
```console
git mv file-directorio nuevo-directorio
git add ./
git commit -m "Files moved to folder"
```
8. Nos metemos en el directorio target que estará vacio, nos clonamos el proyecto al que meter el directorio nuevo y entramos en el directorio
9. No creamos una rama y nos movemos a ella
10. En el nuevo repositorio metemos como repositorio externo el repor en el que hemos dejado la carpeta
```console  
git remote add old-repo ../../source/repor-anterior
```
12. Actualizamos el repo con lo que tiene el old seleccionando la rama desde donde lo tiene que coger
```console  
git pull old-repo development --allow-unrelated-histories
```
13. Eliminamos el repositorio remoto desde donde lo hemos cogido
```console
git remote remove old-repo
```
14. Ahora por último mergeamos develop en nuestra rama que tiene el nuevo directorio
```console  
git merge develop --allow-unrelated-histories
```
14.- Subimos la rama de la manera normal, hacemos PR y pa dentro.

#### Eliminar un submodulo

* Delete the relevant section from the .gitmodules file.
* Stage the .gitmodules changes git add .gitmodules
* Delete the relevant section from .git/config.
* Run git rm --cached path_to_submodule (no trailing slash).
* Run rm -rf .git/modules/path_to_submodule (no trailing slash).
* Commit git commit -m "Removed submodule "
* Delete the now untracked submodule files rm -rf path_to_submodule
