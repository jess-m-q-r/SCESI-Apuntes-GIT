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
