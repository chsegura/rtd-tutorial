hw-monitor
=====

.. hw-monitor:

hw-monitor es una aplicación de Shiny cuya función principal es mostrar los pronósticos diarios del índice sETI. Consta de los archivos server.R y ui.R donde se define la apariencia y distribución de algunos textos dentro de la aplicación. Los textos más largos se encuentran en un directorio docs/ que además de tener estos archivos de texto, tiene algunas imágenes usadas como ejemplos. El directorio www/ tiene linkeados repositorios externos, además de otras imágenes y logos usados en la aplicación. ::

   .
   |---- hw-monitor
   |     |---- server.R
   |     |---- ui.R
   |     |---- docs
   |     |---- www
   |     |     |---- external_repository
   |     |     |     |---- JMA
   |     |     |     |---- mjo_repo
   |     |     |     |---- SERVIMET
   |     |     |---- figures
   |     |     |---- upload
   
.. Important::
   Para generar hw-monitor lo primero es tener instalado R. 

instalando Shiny
====

.. note::
   Shiny es una biblioteca para el lenguaje de programación R que permite crear aplicaciones web interactivas  en R nativo, sin necesidad de usar tecnologías web como HTML, CSS o JavaScript. 

Si está familiarizado con R, es posible que tenga la tentación de instalar paquetes directamente desde R en lugar de hacerlo desde la línea de comandos. Sin embargo, usar el siguiente comando es la forma más segura de garantizar que el paquete se instale para todos los usuarios y no solo para el usuario que actualmente ejecuta R. ::

   sudo su - -c "R -e \"install.packages('shiny', repos='http://cran.rstudio.com/')\""

El su - ejecuta el siguiente comando como si estuviera en el propio entorno del usuario, y la opción -c especifica el comando que se ejecutará. Ese comando, en este caso, es lo que sigue entre comillas dobles.

install.packages es el comando R que se usa para instalar paquetes R. Entonces, en este comando específicamente, el paquete Shiny se instala desde el repositorio especificado.

instalando Shiny server
====

Instalar gdebi ::

   sudo apt install gdebi-core

Debe consultar la página oficial de descarga https://www.rstudio.com/products/shiny/download-server/ para obtener la URL del último binario preconstruido de 64 bits que coincida con su sistema operativo. ::

   wget https://download3.rstudio.org/ubuntu-14.04/x86_64/shiny-server-1.5.17.973-amd64.deb

Use gdebi para instalar el paquete Shiny Server::

   sudo gdebi shiny-server-1.5.17.973-amd64.deb

El servidor Shiny debería iniciarse automáticamente. Consulta su estado ::

   sudo systemctl status shiny-server.service

En un navegador, navegue hasta la dirección IP pública en el puerto 3838 (por ejemplo, ejemplo.com:3838).





