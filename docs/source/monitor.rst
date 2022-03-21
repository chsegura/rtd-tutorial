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
   
.. note::
   Para generar hw-monitor lo primero es tener instalado R. 
