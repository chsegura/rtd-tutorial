****
Uso de la aplicación
****

.. Shiny app: hw-monitor:

La aplicación `hw-monitor <https://www2.dgeo.udec.cl/shiny/hw-monitor/>`_, desarrollada en **Shiny**, tiene como objetivo principal mostrar los pronósticos diarios del índice **sETI** (consultar :doc:`anexoA`).

La estructura del directorio principal del proyecto incluye un directorio de nivel superior llamado ``hw-monitor``. Dentro de este directorio se encuentran los siguientes elementos: ::
   
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

En detalle, estos elementos son:

``ui.R``: 
   Este archivo representa la interfaz de usuario, donde se definen las diferentes partes de la aplicación que los usuarios finales pueden visualizar y utilizar.
   
``server.R``:
    Este archivo corresponde al backend de la aplicación, es decir, el motor que procesa los datos y controla la lógica de la aplicación.

``docs/``:
   Este directorio almacena textos predefinidos y también imágenes estáticas que se muestran en diferentes pestañas de la aplicación. 
   
``www/``: 
   El directorio ``www`` contiene imágenes varias y logotipos utilizados en la aplicación. Además, se encuentran enlazados en el subdirectorio ``external_repository`` los repositorios externos ``JMA``, ``mjo_repo`` y ``SERVIMET`` (descritos en :doc:`anexoA`). En los subdirectorios ``figures`` y ``upload`` se encuentran los repositorios internos de imágenes y archivos generados en ``hw_dynamic/ETI`` (descrito en :doc:`anexoA`).
    
.. Important::
   Es importante tener instalado R para generar y utilizar la aplicación `hw-monitor <https://www2.dgeo.udec.cl/shiny/hw-monitor/>`_. 

Instalación de Shiny
====

Si estás familiarizado con R, es posible que te sientas tentado a instalar paquetes directamente desde R en lugar de utilizar la línea de comandos. Sin embargo, para garantizar una instalación segura del paquete y que esté disponible para todos los usuarios, se recomienda seguir el siguiente comando:

.. code:: bash

   sudo su - -c "R -e \"install.packages('shiny', repos='http://cran.rstudio.com/')\""

En este comando, el ``sudo su -`` ejecuta el siguiente comando como si estuvieras en el entorno del usuario, y la opción ``-c`` especifica el comando que se ejecutará. Dentro de las comillas dobles, se encuentra el comando específico.

El comando ``install.packages`` es utilizado en R para instalar paquetes. En este caso, se instala el paquete Shiny desde el repositorio especificado.

.. note::
   Shiny es una biblioteca del lenguaje de programación R que permite crear aplicaciones web interactivas en R nativo, sin necesidad de utilizar tecnologías web como HTML, CSS o JavaScript. Es una herramienta poderosa para desarrollar aplicaciones web interactivas de manera eficiente utilizando el lenguaje R. 

Instalación de Shiny Server
====

Shiny Server es un servidor web diseñado específicamente para alojar aplicaciones Shiny en un entorno controlado. Los pasos para su instalación son los siguientes:

1. Instalar ``gdebi`` 

.. code:: bash

   sudo apt install gdebi-core

2. Consultar la página oficial de descarga en https://www.rstudio.com/products/shiny/download-server/ para obtener la URL del último binario preconstruido de 64 bits que sea compatible con tu sistema operativo.

3. Descargar el paquete Shiny Server utilizando el comando wget seguido de la URL obtenida:

.. code:: bash

   wget https://download3.rstudio.org/ubuntu-14.04/x86_64/shiny-server-1.5.17.973-amd64.deb

4. Utilizar gdebi para instalar el paquete Shiny Server:

.. code:: bash

   sudo gdebi shiny-server-1.5.17.973-amd64.deb

5. El servidor Shiny debería iniciarse automáticamente. Puedes verificar su estado utilizando el siguiente comando: 

.. code:: bash

   sudo systemctl status shiny-server.service

6. En un navegador web, visita la dirección IP pública de tu servidor seguida del puerto 3838. Por ejemplo, "ejemplo.com:3838".

.. note:: 
   GDebi es una herramienta ligera que permite instalar paquetes DEB de forma rápida y sencilla, sin necesidad de utilizar el Centro de Software de Ubuntu.

Instalación de paquetes de R
====

Para asegurar el correcto funcionamiento de `hw-monitor <https://www2.dgeo.udec.cl/shiny/hw-monitor/>`_, se deben instalar los siguientes paquetes. Puedes utilizar el siguiente comando para instalarlos:

.. code:: bash

   sudo su - -c "R -e \"install.packages(c('shiny','shinyBS','dygraphs','leaflet','dplyr','shinythemes','xts','tidyverse','lubridate','RCurl','R.matlab','sf','tmap','spData','sp','ncdf4','raster','rgdal','rjson'), repos='http://cran.rstudio.com/')\""


Sin embargo, para una mejora continua de la aplicación y evitar tener que instalar los paquetes uno por uno, se recomienda ejecutar una lista más completa de paquetes:

.. code:: bash

   sudo su - -c "R -e \"install.packages(c('shiny','dplyr','shinythemes','tidyverse','lubridate','RCurl','R.matlab','tmap','spData','ncdf4','rjson','zoo','xts','dygraphs','hydroTSM','shinyBS','shinyWidgets','rgdal','sf','rgeos','leaflet','colorRamps','zip','grid','gridExtra','readr','shinyjs','leaflet.esri','httpuv','mime','jsonlite','xtable','digest','htmltools','R6','sourcetools','later','promises','crayon','rlang','fastmap','Rcpp','BH','magrittr','sp','lattice','base64enc','crosstalk','htmlwidgets','markdown','png','RColorBrewer','raster','scales','viridis','leaflet.providers','lazyeval','ggplot2','yaml','xfun','farver','labeling','munsell','viridisLite','lifecycle','gtable','MASS','mgcv','reshape2','tibble','withr','glue','colorspace','nlme','Matrix','plyr','stringr','cli','fansi','pillar','pkgconfig','assertthat','utf8','vctrs','stringi','ellipsis','hms','clipr','leaflet.extras','evaluate','pkgload','praise','desc','pkgbuild','rprojroot','rstudioapi','callr','prettyunits','backports','processx','ps','highr','knitr','tinytex','foreign','classInt','DBI','units','e1071','class','KernSmooth','rex','httr','curl','openssl','askpass','sys','commonmark','xml2','hunspell','testthat','rmarkdown','reactlog','maptools','XML','maps','RJSONIO','purrr','covr','egg','spelling','shinyAce','V8'), repos='http://cran.rstudio.com/')\""
   
Estos paquetes proporcionan funcionalidades adicionales y mejoras para la aplicación `hw-monitor <https://www2.dgeo.udec.cl/shiny/hw-monitor/>`_.   

Depuración de la aplicación
====

Para realizar la depuración y detectar posibles errores al realizar modificaciones en la aplicación, debes editar el archivo ``/etc/shiny-server/shiny-server.conf`` y agregar las siguientes líneas: :: 

   # Instruct Shiny Server to run applications as the user "shiny"
   run_as shiny;
   
   # my add
   preserve_logs true;
   sanitize_errors false;
   
   # Define a server that listens on port 3838

Estas líneas agregadas al archivo permitirán respaldar un archivo ``.log`` en la ubicación ``/var/log/shiny-server/`` y mostrar mensajes en pantalla cada vez que se acceda a la aplicación y ocurra algún error.

De esta manera, podrás tener un registro de los posibles errores y realizar la depuración necesaria para mejorar el funcionamiento de la aplicación.

