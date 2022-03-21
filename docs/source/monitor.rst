****
hw-monitor
****

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

Instalando Shiny
====

.. note::
   Shiny es una biblioteca para el lenguaje de programación R que permite crear aplicaciones web interactivas  en R nativo, sin necesidad de usar tecnologías web como HTML, CSS o JavaScript. 

Si está familiarizado con R, es posible que tenga la tentación de instalar paquetes directamente desde R en lugar de hacerlo desde la línea de comandos. Sin embargo, usar el siguiente comando es la forma más segura de garantizar que el paquete se instale para todos los usuarios y no solo para el usuario que actualmente ejecuta R. ::

   sudo su - -c "R -e \"install.packages('shiny', repos='http://cran.rstudio.com/')\""

El su - ejecuta el siguiente comando como si estuviera en el propio entorno del usuario, y la opción -c especifica el comando que se ejecutará. Ese comando, en este caso, es lo que sigue entre comillas dobles.

install.packages es el comando R que se usa para instalar paquetes R. Entonces, en este comando específicamente, el paquete Shiny se instala desde el repositorio especificado.

Instalando Shiny server
----

Instalar gdebi ::

   sudo apt install gdebi-core

Debe consultar la página oficial de descarga https://www.rstudio.com/products/shiny/download-server/ para obtener la URL del último binario preconstruido de 64 bits que coincida con su sistema operativo. ::

   wget https://download3.rstudio.org/ubuntu-14.04/x86_64/shiny-server-1.5.17.973-amd64.deb

Use gdebi para instalar el paquete Shiny Server::

   sudo gdebi shiny-server-1.5.17.973-amd64.deb

El servidor Shiny debería iniciarse automáticamente. Consulta su estado ::

   sudo systemctl status shiny-server.service

En un navegador, navegue hasta la dirección IP pública en el puerto 3838 (por ejemplo, ejemplo.com:3838).

Instalar paquetes de R
----

Esta es una serie de paquetes comúnmente usados en aplicaciones. La lista va más allá de lo que utiliza actualmente hw-monitor, sin embargo es preferible instalar todo de una vez y en caso de implementar nuevas visualizaciones dentro de la aplicación. ::

   sudo su - -c "R -e \"install.packages(c('shiny','dplyr','shinythemes','tidyverse','lubridate','RCurl','R.matlab','tmap','spData','ncdf4','rjson','zoo','xts','dygraphs','hydroTSM','shinyBS','shinyWidgets','rgdal','sf','rgeos','leaflet','colorRamps','zip','grid','gridExtra','readr','shinyjs','leaflet.esri','httpuv','mime','jsonlite','xtable','digest','htmltools','R6','sourcetools','later','promises','crayon','rlang','fastmap','Rcpp','BH','magrittr','sp','lattice','base64enc','crosstalk','htmlwidgets','markdown','png','RColorBrewer','raster','scales','viridis','leaflet.providers','lazyeval','ggplot2','yaml','xfun','farver','labeling','munsell','viridisLite','lifecycle','gtable','MASS','mgcv','reshape2','tibble','withr','glue','colorspace','nlme','Matrix','plyr','stringr','cli','fansi','pillar','pkgconfig','assertthat','utf8','vctrs','stringi','ellipsis','hms','clipr','leaflet.extras','evaluate','pkgload','praise','desc','pkgbuild','rprojroot','rstudioapi','callr','prettyunits','backports','processx','ps','highr','knitr','tinytex','foreign','classInt','DBI','units','e1071','class','KernSmooth','rex','httr','curl','openssl','askpass','sys','commonmark','xml2','hunspell','testthat','rmarkdown','reactlog','maptools','XML','maps','RJSONIO','purrr','covr','egg','spelling','shinyAce','V8'), repos='http://cran.rstudio.com/')\""

Debugging
----

Para revisar posibles errores al hacer modificaciones a la aplicación hay que editar el archivo /etc/shiny-server/shiny-server.conf, esto que guarda un .log. En el archivo deben agregarse las siguientes líneas :: 

   # Instruct Shiny Server to run applications as the user "shiny"
   run_as shiny;
   
   # my add
   preserve_logs true;
   sanitize_errors false;
   
   # Define a server that listens on port 3838

Ahora los .log se respaldan en /var/log/shiny-server/ además de mostrar un mensaje en pantalla cada vez que se ingrese a la aplicación (y exista un error)



