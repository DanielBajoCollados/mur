# Robot Submarino UDROBOT
# Guía de Instalación

## 1. Requerimientos del sistema
- Ubuntu Versión 18.04 u otro sistema operativo capaz de soportar ROS Melodic Morenia
- Acceso a internet
- Por lo menos 54 MB de espacio libre para los archivos de UDROBOT, además de lo requerido para ROS Melodic Morenia
- 2 GB o más de memoria RAM

## 2. Instalación

### 2.1. ROS Melodic Morenia

#### Configurar los repositorios de ubuntu
Desde la aplicación de ubuntu "Software y actualizaciones", en la ventana "Software de Ubuntu" se deben activar las opciones para Software libre y abierto mantenido por la comunidad (universe), para Controladores privativos para dispositivos (restricted) y para Software restringido por copyright o cuestiones legales (multiverse), tal y como se muestra en la siguiente imagen.

![software&updates](https://raw.githubusercontent.com/DanielBajoCollados/mur/master/software%26updates.png)

#### Configurar sources.list
Para configurar el prdenador para que acepte software de packages.ros.org es necesario escribir el siguiente código:

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

#### Configurar las llaves
Para configurar las llaves es necesario usar el siguiente código:

```
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```

Es posible que no esté instalado curl.
Para ello es necesario usar el siguiente código:

```
sudo apt install curl
```

#### Instalción
Una vez completa la configuración inicial es posible realizar la instalación.
Se recomienda la instalación completa de escritorio con el siguiente código:

```
sudo apt install ros-melodic-desktop-full
```

Tras introducir el comando debería aprecer un mensaje similar al siguiente:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
autoconf automake autopoint autotools-dev binfmt-support blt 
build-essential bzip2-doc cmake cmake-data cython debhelper
default-libmysqlclient-dev dh-autoreconf dh-python dh-strip-nondeterminism
docutils-common docutils-doc dpkg-dev fakeroot fltk1.3-doc fluid fonts-lato
fonts-lyx freeglut3 freeglut3-dev g++ g++-7 gazebo9 gazebo9-common
gazebo9-plugin-base gcc gcc-4.8-base gcc-7 gdal-data gir1.2-gtk-2.0
.
.
The following packages will be upgraded:
libc6 libc6-dbg libexif12 libfreetype6 libglib2.0-0 libglib2.0-bin
libldap-2.4-2 libldap-common liblz4-1 libopenexr22 libpoppler-glib8
libpoppler73 libpython2.7 libpython2.7-minimal libpython2.7-stdlib
libpython3.6 libpython3.6-minimal libpython3.6-stdlib libssl1.1 libtiff5
libuuid1 libwebp6 libwebpdemux2 libwebpmux3 libx11-6 libx11-xcb1 libxml2
poppler-utils python3.6 python3.6-minimal
.
.
Need to get 504 MB/527 MB of archives.
After this operation, 2.258 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Tras aceptar, se completará la instalación.

#### Configuración del entorno
Tal y como se recomienda desde la página de ROS, es conveniente que las variables de entorno se añadan aautomáticamente con cada sesión que se abra del shell.
Para ello se debe usar el siguiente código:

```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

#### Instalación de dependencias
*rosinstall* es un comando comundmente utilizado para descargar con facilidad otros paquetes de ROS.
Para instalarlo se usa el siguiente código:

```
sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
```

Tras ello debería aparecer algo similar en la consola:

```
python-rosinstall-generator python-wstool build-essential
[sudo] password for user: 
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version (12.4ubuntu1).
build-essential set to manually installed.
The following additional packages will be installed:
bzr git git-man liberror-perl libserf-1-1 libsvn1 mercurial
mercurial-common python-bzrlib python-configobj python-crypto python-dbus
python-gi python-httplib2 python-keyring python-keyrings.alt
.
.
.
0 upgraded, 29 newly installed, 0 to remove and 240 not upgraded.
Need to get 11,7 MB of archives.
After this operation, 69,2 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Tras aceptar se completará la instalación.

Como se puede ver, también se ha instalado *rosdep*, que permite instalar dependencias del sistema para compilar códigos. De hecho, es necesario para algunos componentes de ROS, por lo que es necesario inicializarlo antes de usar las herramientas que ofrece ROS.
Para ello se debe usar el siguiente código:

```
sudo rosdep init
rosdep update
```

Tras introducir esos comandos debería aparecer algo similar en la consola:

```
reading in sources list data from /etc/ros/rosdep/sources.list.d
Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/osx-homebrew.yaml
Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/base.yaml
.
.
.
Add distro "noetic"
Add distro "rolling"
updated cache in /home/user/.ros/rosdep/sources.cache
```

### 2.2. Rviz
Para controlar el robot submarino UDROBOT es necesario también *rviz*.
*rviz* es un paquete de ROS que permite la visualización 3D. Además de mostrar el modelo del robot, es capaz de capturar datos de sus sensores y mostrarlos por pantalla.

Para instalarlo es necesario el siguietne código:

```
sudo apt-get install ros-melodic-rviz
```

Tras introducir el siguiente comando debería obtenerse el siguiente resultado por consola.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
ros-melodic-rviz is already the newest version (1.13.17-1bionic.20210505.041235).
ros-melodic-rviz set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 240 not upgraded.
```

### 2.3. Repositorio Robot Submarino UDROBOT
Una vez instalados ROS melodic y rviz, es necesario clonar el repositorio de UDROBOT en el equipo.
Éste se puede encontrar en: [Go to the Support Web Site](https://github.com/juanscelyg/mur)

Para ello se comenzará haciendo un fork del repositorio. Para ello sólo es necesario pulsar el botón de fork de la esquina superior derecha, tal y como se muestra en la imagen.
![Fork](https://raw.githubusercontent.com/DanielBajoCollados/mur/master/Fork.jpeg)

Una vez hecho el fork, desde el nuevo repositorio, puedes descargar el código en formato zip pulsando el botón verde en el que pone "Code" o clonándolo en una carpeta en el equipo usando en la consola git-clone y el enlace del repositorio. El código debería ser similar al siguiente:

```
git clone https://github.com/GithubUserName/mur.git
```

Tras ello debería aparece el siguiente mensaje por consola:

```
Clonando en 'mur'...
remote: Enumerating objects: 1529, done.
remote: Counting objects: 100% (213/213), done.
remote: Compressing objects: 100% (146/146), done.
remote: Total 1529 (delta 115), reused 139 (delta 58), pack-reused 1316
Recibiendo objetos: 100% (1529/1529), 13.49 MiB | 1.50 MiB/s, listo.
Resolviendo deltas: 100% (977/977), listo.
```

Una vez completado aparecerá una carpeta con el nombre "mur" en el directorio en el que se haya hecho git clone.

