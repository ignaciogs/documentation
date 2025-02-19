# Linux

* [Aplicaciones](#aplicaciones)
* [Utilidades para mejorar la terminal](#terminal)
  * [BAT](#bat)
  * [LSD](#lsd)
* [Shell (comandos útiles)](#shell) 
* [Ejercicios / manuales / etc...](#ejercicios)
* [Scripts interesantes](#scripts)


## <a name="aplicaciones">Aplicaciones</a>
> [Terminal Kitty](https://sw.kovidgoyal.net/kitty/) Terminal muy liviana basada en GPU

> [Zeal](https://zealdocs.org/) Gestor de documentación para tener multitud de documentación oficial en offline

> [sxhkd](https://github.com/baskerville/sxhkd) Demonio para manejat atajos de teclado y facilmente configurable mediante fichero
>```console
>git clone https://github.com/baskerville/sxhkd.git
>make
>sudo make install
>
>#Si falla el make será muy posible que se tenga que instalar los siguientes paquetes
>sudo apt install apt-file
>sudo apt install libxcb-util0-dev
>sudo apt install libxcb-keysyms1-dev
>
>#Una vez instalado tenemos que crear un fichero de configuración llamado sxhkdrc dentro de .congif/sxhkd/sxhkdrc
>cd ~/.config
>mkdir sxhkd
> Creamos un fichero sxhkdrc o nos descargamos el nuestro
>```
> [Fichero sxhkdrc](sxhkdrc)


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
 
### Consultar las cabeceras de una url
 ```console
 curl -X HEAD -i https://www.myweb.com 
 ```
 
### Monitorizar la salida de openVPN
 ```console
 sudo tail -f /var/log/syslo
 ```
  
## <a name="ejercicios">Ejercicios / manuales / etc...</a>
* [Overthewire](https://overthewire.org/wargames/) Página para aprender conceptos de seguridad, manejarse con la terminal, etc.. a través de multitud de ejercicios y juegos

* ## <a name="scripts">Scripts interesantes</a>
### Obtener una lista de PRs abiertos en github en un conjunto de repositorios
 ```shell
 #!/bin/bash

TOKEN="your_token"
REPOS=(
    "owner/repository_name"
    "owner/repository_name"
    "owner/repository_name"
)

# Colors
RED=$(tput setaf 1)
GREEN=$(tput setaf 2)
BLUE=$(tput setaf 4)
RESET=$(tput sgr0)

BACK_REPO="\033[48;2;255;255;255m"
TEXT_REPO="\033[38;2;0;0;0m"
RESET="\033[0m"

for REPO in "${REPOS[@]}"; do
    response=$(curl -s -H "Authorization: token $TOKEN" "https://api.github.com/repos/$REPO/pulls?state=open")

    # Comprobar si hay PRs abiertos
    pr_count=$(echo "$response" | jq 'length')
    if [[ "$pr_count" -eq 0 ]]; then
        continue
    fi

    # Calculate column widths
    title_width=$(echo "$response" | jq -r '.[].title' | awk '{ if (length > max) max = length } END { print max }')
    url_width=$(echo "$response" | jq -r '.[].url' | awk '{ if (length > max) max = length } END { print max }')
    user_width=$(echo "$response" | jq -r '.[].user.login' | awk '{ if (length > max) max = length } END { print max }')
    update_width=$(echo "$response" | jq -r '.[].updated_at' | awk '{ if (length > max) max = length } END { print max }')

    echo -e "${TEXT_REPO}${BACK_REPO}Repository: $REPO${RESET}"
    printf "${RED}%-${title_width}s ${GREEN}%-${url_width}s ${BLUE}%-${user_width}s ${BLUE}%-${update_width}s ${RESET}\n" "Titulo" "Url" "Usuario" "Fecha"

    echo "$response" | jq -r '.[] | "\(.title)\t\(.url)\t\(.user.login)\t\(.updated_at)"' | while IFS=$'\t' read -r title url user updated; do
        formatted_updated=$(echo "$updated" | awk -F '[-T:.Z]' '{ printf "%s-%s-%s %s:%s:%s\n", $1, $2, $3, $4, $5, $6 }')
        printf "${RED}%-${title_width}s ${GREEN}%-${url_width}s ${BLUE}%-${user_width}s ${BLUE}%-${update_width}s ${RESET}\n" "$title" "$url" "$user" "$formatted_updated"
    done

    echo -e "\n"
done 
 ``` 
