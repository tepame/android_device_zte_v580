# LineageOS 14.1 (Nougat) para ZTE Blade V580

## Instrucciones para compilar LineageOS

### Bibliotecas de JAVA

#### El siguiente comando asegura comenzar con un estado 'limpio':
```
sudo apt-get remove openjdk-* icedtea-*
```
#### Instalar repositos de "java" desde terminal:
```
sudo apt-add-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-8-jdk
```
#### Instalación de requisitos para la compilación:
```
sudo apt-get install git ccache lzop bison gperf build-essential zip curl zlib1g-dev g++-multilib python-networkx libxml2-utils bzip2 libbz2-dev libghc-bzlib-dev squashfs-tools pngcrush liblz4-tool optipng libc6-dev-i386 gcc-multilib libssl-dev gnupg flex lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev xsltproc unzip python-pip python-dev libffi-dev libxml2-dev libxslt1-dev libjpeg8-dev openjdk-8-jdk
```
### Setup de Google

#### Crea el directorio "bin":
```
mkdir ~/bin
```
#### Añade el directorio "bin" a la ruta:
```
PATH=~/bin:$PATH
```
#### Instalar "repo" desde los repositorios de Google:
```
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```
### Dispositivo

#### crea el directorio "android/platform":
```
mkdir ~/android/platform
cd ~/android/platform
```
#### Configurar usuario de Git:
```
git config --global user.email "aaa@bbbbbb.com" (correo que se usó en github) 
git config --global user.name "NAME" (Nombre de usuario de github)
```
#### Inicializar el repositorio de LineageOS:
```
repo init -u https://github.com/LineageOS/android.git -b cm-14.1
```
#### Ahora para descargar la fuente (esto tardara dependiendo de tu computadora e internet):
```
repo sync -f --force-sync --no-clone-bundle
``` 
### Configurar los directorios "device" y "vendor":

### device

#### Ir al directorio "android/platform/device":
```
cd ~/android/platform/device
```
#### Crear el directorio "zte":
```
mkdir zte
cd zte
```
#### Descargue el repositorio "device" para ZTE Blade V580:
```
git clone https://github.com/tepame/android_device_zte_v580.git v580
```
### vendor

#### Ir al directorio "android/platform/vendor":
```
cd ~/android/platform/vendor
```
#### Crear el directorio "zte":
```
mkdir zte
cd zte
```
#### Descargue el repositorio "vendor" para ZTE Blade V580:
```
git clone https://github.com/tepame/android_vendor_zte_v580.git v580
```
#### Parches:
```
cd ~/android/platform/device/zte/v580/patches_mtk && . apply-patches.sh
```
### Configuración de Caché:

#### Diríjase a su carpeta de inicio (~), abra el archivo ".bashrc" y pégue el siguiente código en la parte inferior:
```
export USE_CCACHE=1
export ANDROID_JACK_VM_ARGS="-Xmx4096m -Xms512m -Dfile.encoding=UTF-8 -XX:+TieredCompilation"
```
### Compilación

#### Ir al directorio "android/platform":
```
cd ~/android/platform
```
#### Ejecutar el siguiente comando:
```
. build/envsetup.sh && brunch v580
```

### Comienza la compilación!!!

#### Tratamos los errores a medida que ocurren...

## Exito!!!