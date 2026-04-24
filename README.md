# TRABAJO INDIVIDUAL 

Jessica Mayra Quispe Rico

## CLASE 1
### ¿Qué es GIT?

Sistema de Control de Versiones Distribuido (VCS).
Permite guardar y tener control sobre las versiones de archivos de manera local.

### ¿Cómo nació GIT?

Linus Torvalds el creador de Linux, usaba BitKeeper pero tubo un problema y BitKeeper decidio  
quitarles la licencia debido a esto Linus se encerrro y dentro de 2 a 3 semanas creo GIT.


### ¿Cómo instalar GIT? 

Página web: https://gitscm.com/install/ 

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

**README.md**: Descripción del proyecto
**.gitignore**: Archivo que indica a GIT que debe ignorar o no incluir

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

- Subir archivos locales
```
git push origin <rama>
```

- Bajar los cambios hechos

```
git pull origin <rama>
```
