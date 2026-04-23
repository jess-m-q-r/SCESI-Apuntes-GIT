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
