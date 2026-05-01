# TRABAJO INDIVIDUAL 

Jessica Mayra Quispe Rico

## CLASE 1
### ¿Qué es GIT?
<img src="imagen/gitLogo.png" width="200" align="left" hspace="40">
Sistema de Control de Versiones Distribuido (VCS).  
<br>
Permite guardar y tener control sobre las versiones de archivos de manera local.  
<br clear="all">

### ¿Cómo nació GIT?
<img src="imagen/Linus.jpg" width="300" align="left" hspace="10">
Linus Torvalds el creador de Linux, usaba BitKeeper pero tubo un problema y BitKeeper decidio quitarles la licencia debido a esto Linus se encerrro y dentro de 2 a 3 semanas creo GIT.
<br clear="all">

### ¿Cómo instalar GIT? 

Página web: [GIT Install](https://gitscm.com/install/) 

Se debe seguir los pasos indicados en la página dependiendo el S.O.

Para Linux Debian/Ubuntu
```
apt-get install git
```

Verificación de instalación ingresar el comando:
```
git --version
```
### Configuraciones Básicas

```
git config --global user.name "Nombre"
git config --global user.email "tu@correo.com"
git config --global core.autocrlf true

```

### Archivos que todo repositorio debe tener

- **README.md**: Descripción del proyecto.  
- **.gitignore**: Archivo que indica a GIT que debe ignorar o no incluir.

## CLASE 2
### Estados de GIT
 
**Directorio de Trabajo (Modificado)**: Tu carpeta local donde GIT observa los archivos y los cataloga en:
- **Untracked**: Sin seguimiento, GIT lo ve pero no tiene una versión antigua de este archivo.
- **Modified**: GIT ya tiene una versión previa del archivo y fue modificado, eliminado o renombrado.
**Stage Area (Preparado)**: Área de espera donde seleccionas qué archivos modificados se incluirán en el siguiente commit.
 
**Repositorio Local (Confirmado)**: El historial. Los cambios quedan guardados con un ID (hash) y son parte de la historia.
 
### Comandos Básicos
 
```
git restore <archivo>           # Revertir archivo modificado a su estado original
git add <archivo>               # Agregar un archivo al stage area
git add .                       # Agregar todos los archivos al stage area
git restore --staged <archivo>  # Sacar archivo del stage area
git commit -m "mensaje"         # Confirmar cambios al repositorio local
git reset --soft HEAD~1         # Deshacer el último commit
```
 
### Buenas Prácticas en Commits
 
Usar **commits atómicos**: cada commit representa un único cambio lógico, pequeño y completo.
 
Formato recomendado:
```
git commit -m "<tipo>: <descripción>"
```
 
Prefijos:
- **feat**: nueva característica para el usuario.
- **fix**: bug que afecta al usuario.
- **perf**: mejoras de rendimiento.
- **build**: cambios en el sistema de build o instalación.
- **ci**: cambios en integración continua.
- **docs**: cambios en la documentación.
- **refactor**: refactorización del código.
- **style**: cambios de formato que no afectan al usuario.
- **test**: para tests o refactorización de tests.
Reglas:
- Usar verbos imperativos: `Add`, `Change`, `Fix`, `Remove`
- Sin punto final ni puntos suspensivos
- Máximo 50 caracteres

## CLASE 3
### ¿Qué es Github?

Plataforma en la nube que permite a desarrolladores alojar, gestionar y colaborar en proyectos de software
utilizando Git.

### Git vs Github

- **Git**: Sistema de control de versiones, crea puntos de guardado.
- **Github**: Es el servidor donde esos puntos se almacenan

### SSH vs HTTPS

Para el control de acceso o uso de repositorio.
- **HTTPS**: Pide autenticación cada vez
- **SSH**: Se configura la PC/Laptop ssh para comunicar con git hub, mediante una key, esta al ponerla en 
Github no pedira cada vez

### Configuración SSH 
Comandos utilizados
```
ssh-keygen -t ed25519 -C “tu-correo@email.com”    
cat ~/.ssh/id_ed25519.pub
```
Pasos
Se copia el contenido del comando cat y en github vamos a:
- Settings 
- SSH y gpg kEYS 
- New SSH kEY: Aqui es donde se pega el contenido, se asigna un nommbre para la pc y Add SSH Key

```
ssh -T git@github.com  #Esto para verificacion
```

### Crear Repositorio en Github
- Ir al apartado de repositorios y dar en NEW
- POner el nombre y crear repositorio

### Conexión de un repositorio local de Git a uno existente en Github
 
Comandos
```
git remote add origin git@github.com:TuUser/TuRepo.git

git branch -M main

git push -u origin main
```
### Clonar un repositorio de Git

Comandos
```
git clone git clone “git@github.com:TuUser/TuRepo.git”

```
Con HTTPS

```
git clone “https://github.com/TuUser/TuRepo.git”
```
Comando para cambiar el puntero de github y no pida autenticación cada vez

```
git remote set-url origin “git@github.com:TuUser/TuRepo.git”
```
Comando para ver que repositorio remoto esta conectado a tu repo

```
git remoto -v
```
### Cambios en el repositorio en Github

- Subir archivos locales.
```
git push origin <rama>
```

- Bajar los cambios hechos.

```
git pull origin <rama>
```
## CLASE 4

### Git Remote
Es el comando que permite gestionar nuestras conexiones con los repositorios remotos.
Le dice a GIT local donde enviar o traer la información.
Comandos
- **git remote -v**: Muestra las URLs donde apunta nuestro repositorio.
- **git remote add <apodo> "url"**: Vincula el repositorio local con uno en la nube .
- **git remote set-url <apodo> "url"**: Cambia la url donde apunta nuestro repositorio. 
<apodo> es una forma de llamar a la url

### Multiples SSH
Si se tiene mas de una cuenta de Github se puede manejar mas de una llave SSH. Es decir se necesita una llave
para cada puerta como tal.

### Crear multicuentas

Comando para diferenciar de la nueva cuenta y evitar que sobreescriba en la ruta ~./ssh/id_ed25519, se crea una
nueva ruta.
```
ssh-keygen -t ed25519 -C “tu-correo@email.com”  -f ~./ssh/ruta.pub 
```

Cuentas que se debe poner 
```
 #Cuenta Personal
Host github.com
 HostName github.com
 User git 
 identityFIle ~./ssh/id_ed25519

 #Cuenta del otro correo
Host github-miname
HostName github.com
User git
IdentityFile ~/.ssh/id_miname
```
Una vez modificado 
```
ssh -T git@github-auxi
```
### Configuraciones Locales
Las configuraciones locales se toman en cuenta antes que las globales, y estas solo funcionan para el repositorio en el que se aplican.
Para hacer configuraciones locales lo que se debe hacer es
lo mismo que en las globales pero sin el flag --global:

```
git config user.name "Mi nuevo Name"
git config user.email "micorreo@gmail.com"
```
Realizar git clone con el host correcto
```
git clone git@github-miname:usuario/repo.git
```

### Git Checkout
¿Para que sirve?
- Inspeccionar: Ver codifgo en un commit antiguo
- Restaurar
- Experimentar
- Cambiar

### Como ir y volver en un commit
```
#Para ir atras debes hacer:
git checkout <hash_antiguo>
#Y para volver al ultimo hash de la rama
git checkout <rama>

#Si hiciste algo aca (como un commit) desaparece salvo que hagas:
git checkout <hash_commit_creado>
git checkout -b rama_nueva
```
## CLASE 5
### Ramas Y GITFLOW
Las ramas permite crear una versión paralela, sin afectar el main, el codigo principal funcional.
Puedes realizar cambios sin miedo a dañar directamente el codigo principal y trabajo en paralelo con otras
personas.
#### Git branch
Comando que permite gestionar las ramas que tiene o tendra un proyecto.
```
git branch                         #Lista las ramas.
git branch <nombre de la rama>     #Crea rama a partir de la que estamos actualmente.
git branch -D <nombre de la rama>  #Elimina una rama.
```
#### Git checkout
El uso de git checkout en ramas es el siguiente:
```
git checkout <rama>    #Cambia de rama, pero no se debe tener nada modificado sin guardar.
git checkout -b <rama> #Crea la rama y te mueve directamente a esa rama creada.
```
Git checkout es multiproposito (Rama, Commits, Archivos).
#### Git switch
Alternativa para navegar entre ramas, dado que git checkout estaba sobrecargado o tenia muchas funciones.

```
git switch <rama>     #Cambia a esa rama.
git switch -c <rama>  #Crea la rama y te posiciona ahi.
```
### Git flow
Es un flujo de trabajo el cual nos permite organizarnos y maneja estandares para tener organizado nuestras ramas.
Que ramas se tiene:
- **main**: Es la que se tiene por defecto al crear el repositorio de git, contiene el codigo que se encuentra
en producción.
- **develop**: Es la rama de "pre-producción". Tiene las caracteristicas que aun estan en el periodo de 
validación.
- **rama de apoyo**: Son ramas que nos ayudaran en el desarrollo
1. **feature**: Cuando se trabaja en una nueva característica para el proyecto. Se crea en la rama develop, al 
acabar se fusiona en develop y se elimina.
```
 #Ejemplos de nombres
feature/sum-function
feature/add-search-bar
```
2. **release**: Cuando se prepara el lanzamiento de una nueva versión. En teoría donde se hacen pruebas (QA).
Se crea desde la rama develop y se fucionan en develop o main.
```
 #Ejemplos de nombres
release/v1.0.0
release/v2.1.0-beta
```
3. **hotfix**: Para trabajar en cambios imprevistos, como arreglar bigs o un problema en producción. Se crea 
desde la rama main.
```
 #Ejemplos de nombres
hotfix/login-authentication-error
```
## CLASE 6
### Git merge
Permite fusionar ramas en una sola, para que tengan commit hechos.
Se recomienda usar el flag `--no-ff` (no fast forward) para preservar el historial de ramas, incluso si la rama es eliminada después.
```
git merge --no-ff rama
```
### Git fetch
Permite ver cambios en la rama y sus ramas hijas.
```
git fetch
```
### Git pull
Descarga y aplica todos los cambios del repositorio remoto a la rama actual.
```
git pull origin rama
```
### Git push
Sube los cambios locales al repositorio remoto.
```
git push origin rama
```
Si es la primera vez* que subes una rama a un repositorio que no es tuyo, usa el flag "-u"
```
git push origin -u rama
```
### Flujo de trabajo (Sin Pull Requests)
 
1. Situarse en develop y actualizarla
```
git checkout develop
git fetch
git pull origin develop
```
2. Moverse a tu rama de trabajo
```
git checkout mi-rama
```
3. Integrar cambios de develop (solo si hubo cambios)
```
git merge develop
```
4. Trabajar en tu rama...
5. Subir cambios al remoto (agregar -u si es la primera vez)
```
git push origin mi-rama
```
6. Volver a develop y actualizarla
```
git checkout develop
git fetch
git pull origin develop
```
7. Fusionar tu rama en develop
```
git merge --no-ff mi-rama
```
8. Resolver conflictos manualmente si los hay, luego:
```
git add .
git commit
```
9. Eliminar la rama local y subir develop
```
git branch -D mi-rama
git push origin develop
```
## CLASE 7
### Pull Request
Es la forma de trabajo en git/github, se crea un request(petición) en el grupo del repositorio de github el cual permite mostrar que es lo que se quiere unir o mergar al codigo base que ya se tiene.

### Como crear una Pull Request
Al momento de haber realizado un **git push origin rama** en github mostrara un boton para realizar la PR.  
[Video tutorial de Youtube ](https://youtu.be/4CeMKqloOJc)

### Flujo de trabajo
1. Preparar tu rama

```
git checkout develop
git fetch
git pull origin develop

git checkout    # Agrega -b si estás creando la rama nueva
git merge develop            # Solo si hubo cambios en develop desde que creaste tu rama
```

2. Trabajar y subir cambios

```
git push origin    # Agrega -u si es la primera vez que subes esta rama al remoto
```

3. Antes de abrir el PR — sincronizar con develop

```
git checkout develop
git fetch
git pull origin develop

git checkout 
git merge develop            # Solo si hubo nuevos cambios en develop
```

Si hay conflictos, resuélvelos manualmente en los archivos afectados, luego:

```
git add .
git commit   
git push origin 
```

4. Crear el PR

Sigue el flujo mostrado en como crear un PR.  
### ¿Por qué usar PRs?

Sin PRs, cualquier colaborador puede mergear código sin avisar esto es un riesgo innecesario. Los PRs obligan al equipo a revisar los cambios antes de que entren al repositorio, abriendo espacio para el debate, la aprobación y la detección de errores o código problemático.

### ¿Cómo proteger el repositorio y limitar la colaboración?

Saber la importancia de los PRs no es suficiente, sin restricciones los colaboradores aún pueden mergear sin aprobación. 

### ¿Cómo colaboro si no soy un colaborador invitado?

Puedes contribuir a un repositorio sin ser colaborador invitado mediante un fork.

## CLASE 8
### Git stash
Guarda temporalmente cambios sin hacer commits.
```
git stash -m "descripcion" #Guarda los cambios  con un nombre
git stash list             #Lista todos los stashes guardados
git stash pop              #Recupera el ultimo stash
```
### Git diff
Muestra las diferencias entre archivos o ramas.
```
git diff .                  # Cambios sin stagear (todos los archivos)
git diff archivo            # Cambios sin stagear en un archivo específico
git diff --staged .         # Cambios ya en staging (todos los archivos)
git diff --staged archivo   # Cambios en staging de un archivo específico
git diff rama1 rama2        # Diferencias entre dos ramas
```
- Usar git stash -m "algo" siempre con un mensaje descriptivo.
- Eliminar la rama después de mergear el PR.
