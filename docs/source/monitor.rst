****
Shiny app: hw-monitor
****

.. Shiny app: hw-monitor:

**hw-monitor** es una aplicación de **Shiny** cuya función principal es mostrar los pronósticos diarios del índice **sETI** (ver :doc:`anexoA`). 

Tenemos un directorio ``hw-monitor`` de nivel superior en el directorio principal del proyecto. Dentro de esto está: ::
   
   hw_dynamic
   ├── hw-monitor
       ├── server.R
       ├── ui.R
       ├── docs
       └── www
           ├── external_repository
               ├── JMA
               ├── mjo_repo
               └── SERVIMET
           ├── figures
           └── upload

``ui.R``: 
   Este archivo que significa interfaz de usuario (del inglés), es donde se definen las diferentes partes de las aplicaciones fronterizadas (es decir, lo que ven los usuarios finales).
   
``server.R``:
    Este archivo por el contrario, es el backend o el motor de la aplicación, es decir, donde se procesan los datos.

``docs/``:
   Este directorio almacena algunos textos predefinidos, además de imágenes estáticas que se muestran en distintas pestañas de la aplicación. 
   
``www/``: 
   El directorio ``www`` además de imágenes varias y logos usados en la aplicación, tiene linkeados en ``external_repository`` los repositorios externos ``JMA``, ``mjo_repo`` y ``SERVIMET`` (descritos en :doc:`anexoB`). En ``figures`` y ``upload`` existen repositorios internos de imagenes y archivos generados en ``hw_dynamic/ETI`` (descrito en :doc:`anexoA`). 

    
.. Important::
   Para generar **hw-monitor** lo primero es tener instalado R. 

Instalando Shiny
====

Si está familiarizado con R, es posible que tenga la tentación de instalar paquetes directamente desde R en lugar de hacerlo desde la línea de comandos. Sin embargo, usar el siguiente comando es la forma más segura de garantizar que el paquete se instale para todos los usuarios y no solo para el usuario que actualmente ejecuta R. 

.. code:: bash

   sudo su - -c "R -e \"install.packages('shiny', repos='http://cran.rstudio.com/')\""

El ``su -`` ejecuta el siguiente comando como si estuviera en el propio entorno del usuario, y la opción ``-c`` especifica el comando que se ejecutará. Ese comando, en este caso, es lo que sigue entre comillas dobles.

``install.packages`` es el comando R que se usa para instalar paquetes R. Entonces, en este comando específicamente, el paquete Shiny se instala desde el repositorio especificado.

.. note::
   Shiny es una biblioteca para el lenguaje de programación R que permite crear aplicaciones web interactivas en R nativo, sin necesidad de usar tecnologías web como HTML, CSS o JavaScript. 

Instalando Shiny server
====

Shiny server construye un servidor web diseñado específicamente para alojar aplicaciones Shiny en un entorno controlado. Los pasos para su instalación consisten en: 

1. Instalar ``gdebi`` 

.. code:: bash

   sudo apt install gdebi-core

2. Debe consultar la página oficial de descarga https://www.rstudio.com/products/shiny/download-server/ para obtener la URL del último binario preconstruido de 64 bits que coincida con su sistema operativo. 

.. code:: bash

   wget https://download3.rstudio.org/ubuntu-14.04/x86_64/shiny-server-1.5.17.973-amd64.deb

3 Use gdebi para instalar el paquete Shiny Server

.. code:: bash

   sudo gdebi shiny-server-1.5.17.973-amd64.deb

4 El servidor Shiny debería iniciarse automáticamente. Consulta su estado 

.. code:: bash

   sudo systemctl status shiny-server.service

5 En un navegador, navegue hasta la dirección IP pública en el puerto 3838 (por ejemplo, ejemplo.com:3838).

.. note:: 
   GDebi es una pequeña herramienta que nos permite instalar paquetes DEB de manera rápida y sencilla sin tener que lanzar el Centro de Software de Ubuntu.

Instalando paquetes de R
====

Para que **hw-monitor** se ejecute correctamente, esta lista de paquetes deben ser instalados: 

.. code:: bash

   sudo su - -c "R -e \"install.packages(c('shiny','shinyBS','dygraphs','leaflet','dplyr','shinythemes','xts','tidyverse','lubridate','RCurl','R.matlab','sf','tmap','spData','sp','ncdf4','raster','rgdal','rjson'), repos='http://cran.rstudio.com/')\""


Sin embargo, con el propósito de ir mejorando la aplicación y no tener que ir instalando los paquetes de uno en uno, se recomienda ejecutar esta lista de paquetes más completa:

.. code:: bash

   sudo su - -c "R -e \"install.packages(c('shiny','dplyr','shinythemes','tidyverse','lubridate','RCurl','R.matlab','tmap','spData','ncdf4','rjson','zoo','xts','dygraphs','hydroTSM','shinyBS','shinyWidgets','rgdal','sf','rgeos','leaflet','colorRamps','zip','grid','gridExtra','readr','shinyjs','leaflet.esri','httpuv','mime','jsonlite','xtable','digest','htmltools','R6','sourcetools','later','promises','crayon','rlang','fastmap','Rcpp','BH','magrittr','sp','lattice','base64enc','crosstalk','htmlwidgets','markdown','png','RColorBrewer','raster','scales','viridis','leaflet.providers','lazyeval','ggplot2','yaml','xfun','farver','labeling','munsell','viridisLite','lifecycle','gtable','MASS','mgcv','reshape2','tibble','withr','glue','colorspace','nlme','Matrix','plyr','stringr','cli','fansi','pillar','pkgconfig','assertthat','utf8','vctrs','stringi','ellipsis','hms','clipr','leaflet.extras','evaluate','pkgload','praise','desc','pkgbuild','rprojroot','rstudioapi','callr','prettyunits','backports','processx','ps','highr','knitr','tinytex','foreign','classInt','DBI','units','e1071','class','KernSmooth','rex','httr','curl','openssl','askpass','sys','commonmark','xml2','hunspell','testthat','rmarkdown','reactlog','maptools','XML','maps','RJSONIO','purrr','covr','egg','spelling','shinyAce','V8'), repos='http://cran.rstudio.com/')\""

Debugging
====

Para revisar posibles errores al hacer modificaciones a la aplicación hay que editar el archivo ``/etc/shiny-server/shiny-server.conf``, esto que guarda un ``.log``. En el archivo deben agregarse las siguientes líneas :: 

   # Instruct Shiny Server to run applications as the user "shiny"
   run_as shiny;
   
   # my add
   preserve_logs true;
   sanitize_errors false;
   
   # Define a server that listens on port 3838

Ahora los ``.log`` se respaldan en ``/var/log/shiny-server/`` además de mostrar un mensaje en pantalla cada vez que se ingrese a la aplicación (y exista un error).



