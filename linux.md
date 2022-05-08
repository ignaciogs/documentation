# Linux

* [Aplicaciones](#aplicaciones)
* [Utilidades para mejorar la terminal](#terminal)
* [Ejercicios / manuales / etc...](#ejercicios)


## <a name="aplicaciones">Aplicaciones</a>
* [Terminal Kitty](https://sw.kovidgoyal.net/kitty/) Terminal muy liviana basada en GPU
* [Zeal](https://zealdocs.org/) Gestor de documentación para tener multitud de documentación oficial en offline

## <a name="terminal">Utilidades para mejorar la terminal<a/>

### BAT [(Github)](https://github.com/sharkdp/bat)
El bat es un cat vitaminizado, el cual formatea la salida en un formato mucho más amigable, tiene detección de sintaxis y algunas cosillas más.

#### Instalación
```
sudo apt install bat
```

#### Consideraciones
Después de la instalación para ejecutarlo hay que utilizar el comando **batcat**, en el caso que se hubiera instalado directamente desde el .deb bastararía con **bat**. Para que sea más sencillo de utilizar es bastante útil crearse un alias para que cuando se utilice el cat utilice en su defecto el batcat. Para ello por ejemplo en el fichero **~/.zshrc** creamos un alias de la siguiente manera
```
alias cat='batcat'
```
  
## <a name="ejercicios">Ejercicios / manuales / etc...</a>
* [Overthewire](https://overthewire.org/wargames/) Página para aprender conceptos de seguridad, manejarse con la terminal, etc.. a través de multitud de ejercicios y juegos
