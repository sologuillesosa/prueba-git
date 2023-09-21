# Comandos Git

## Configuración Inicial

git config --global user.name "Juan Perez"
git config --global user.email "correo@gmail.com"

## Comenzar a trabajar con Git

git init // Inicializar un repositorio git
git status // Ver el estado del proyecto
git add subir.txt // Archivos a incorporar
git add .  // Agrega todos los archivos
git rm --cached php/local.txt // Quitar un archivo
git commit -m "Primer commit" // Agregar foto
git commit --amend // i=ins - msg - ZZ=escapar
git log --oneline // Historial de commit 1 linea
git diff // ver los cambios en el archivo
git show <n_commit> // ver commit con dif

## Trabajar con las ramas

git branch --list // ver las ramas
git branch rama-fix // crear rama fix
git switch rama-fix // Cambiar a rama fix
git checkout rama-fix // Cambiar a rama fix
git branch -m fix // Cambiar nombre de rama
git branch -d rama1 rama2 // Eliminar ramas 1y2
git branch -D rama3 // Elimina aún sin merge

## Staging area index, working tree

// Directorio de trabajo «workin directory»
// Está sucio, si tiene cambios sin guardar
git diff // proximos cambios no agregados
git diff --staged // ver agregado en staged
// Sin commit, no permite cambiar de rama
// Por ello, se puede guardar en stash
git stash save "msg" // Guardar stash
git stash list // Ver listado en stash
git stash show -p stash@{0} // diff con id
git stash apply <nombre> // aplica
git stash pop <nombre> // aplica y saca
git stash drop <nombre> // saca
git stash clear // limpiar

## Fusión de ramas simple

---------master---------
git init
git add index.html
git commit -m "Agrego el primer commit"
---------header---------
git checkout -b header
git add index.html
git commit -m "Agrega cabecera"
git log --oneline
---------master---------
git switch master
git merge header
------------------------

## Fusión de ramas multiple

---------master---------
git init
git add index.html
git commit -m "Agrego el primer commit"
git branch
---------footer---------
git checkout -b footer
git add index.html
git commit -m "Agrego el footer"
git log --oneline
---------links---------
git switch master
git checkout -b links
git add index.html
git commit -m "Agrego las hojas de estilo"
git log --oneline
---------master---------
git switch master
git merge links
git merge footer
git log --graph
------------------------

## Merge con conflictos

---------slider---------
git checkout -b slider
git add index.html // agrego lines 8 y 15
git commit -m "Inserta un slider"
---------noticias---------
git switch master
git checkout -b noticias
git add index.html // agrego lines 8 y 15
commit -m "Inserta la seccion de noticias"
---------master---------
git switch master
git merge noticias
git merge slider // superposición de líneas
git status
git restore --staged index.html
// corregir el conflicto y avanzar
git add index.html
git merge --continue
// ZZ=confirmar el merge
------------------------

## Crear un repositorio nuevo en GitHub

git init
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin <repo>
git push -u origin main

## Subir a un repo existente de GitHub

git remote add origin <repo> 
git branch -M main
git push -u origin main

## Otras notas

git pull // descargar los cambios hechos por otros usuarios
git clone <repo> // clonar repositorio a mi equipo
git reset . // anula la acción anterior
git checkout -- . // reconstruye todos los archivos del último commit
git commit --amend // i=para editar y escape, :wq!=editar y cierrar
git commit -am "readme agrega diff" // realiza el add y commit a la vez

## Ver como aplicar

git fetch // actualizar la rama main local
git revert // 
git reset // deshacer un un commit anterior