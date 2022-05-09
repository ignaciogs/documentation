# Linux

* [Aplicaciones](#aplicaciones)
* [Utilidades para mejorar la terminal](#terminal)
  * [BAT](#bat)
  * [LSD](#lsd)
* [Shell (comandos útiles)](#shell) 
* [Ejercicios / manuales / etc...](#ejercicios)


## <a name="aplicaciones">Aplicaciones</a>
* [Terminal Kitty](https://sw.kovidgoyal.net/kitty/) Terminal muy liviana basada en GPU
* [Zeal](https://zealdocs.org/) Gestor de documentación para tener multitud de documentación oficial en offline

## <a name="terminal">Utilidades para mejorar la terminal<a/>

### <a name="bat">BAT [(Github)](https://github.com/sharkdp/bat)</a>
El bat es un cat vitaminizado, el cual formatea la salida en un formato mucho más amigable, tiene detección de sintaxis y algunas cosillas más.

#### Instalación
```console
sudo apt install bat
```

#### Consideraciones
Después de la instalación para ejecutarlo hay que utilizar el comando **batcat**, en el caso que se hubiera instalado directamente desde el .deb bastararía con **bat**. Para que sea más sencillo de utilizar es bastante útil crearse un alias para que cuando se utilice el cat utilice en su defecto el batcat. Para ello por ejemplo en el fichero **~/.zshrc** creamos un alias de la siguiente manera
```console
alias cat='batcat'
```
  
### <a name="lsd">LSD [Github](https://github.com/Peltoche/lsd)</a>
El **lsd** es un ls de linux vitaminizado, haciendo la salida por consola más amigable con colores, iconos y demás mejoras visuales  

#### Instalación
1. Instalar las fuentes [Nerd-fonts](https://github.com/ryanoasis/nerd-fonts/blob/master/readme.md) que son las fuentes que tienen todos los iconos
  ```console
  git clone https://github.com/ryanoasis/nerd-fonts.git
  cd nerd-fonts
  ./install.sh
  ```
2. Descargarse la última versión de lsd desde su [página de releases](https://github.com/Peltoche/lsd/releases) (Por ejemplo para ubuntu el fichero lsd_0.21.0_amd64.deb) e instalarlo
```console
sudo dpkg -i lsd_0.21.0_amd64.deb 
```
#### Consideraciones
Para utilizarlo de forma más simple sería bueno como dice en su pagina crear los siguientes alias en el fichero *~/.zshrc** por ejemplo si es que estamos utilizando zsh
 ```console
 alias ls='lsd'
 alias l='ls -l'
 alias la='ls -a'
 alias lla='ls -la'
 alias lt='ls --tree'
 ```
 
## <a name="shell">Shell (comandos útiles)</a> 
 
### Búsqueda de palabras en ficheros
```console
grep --include=*.java -irn ~/workspace/ -e "cadena" 
``` 
Entre otros existen estos parámetros interesantes
* -i case insesitive
* -r is recursive
* -n is line number
* -w stands match the whole word
 
  
## <a name="ejercicios">Ejercicios / manuales / etc...</a>
* [Overthewire](https://overthewire.org/wargames/) Página para aprender conceptos de seguridad, manejarse con la terminal, etc.. a través de multitud de ejercicios y juegos
