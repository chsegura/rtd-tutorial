Repositorios: interno
=====

.. Repositorios: interno:

El directorio ``ETI`` contiene una serie de subdirectorios, rutinas y scripts que generan un pronóstico diario del índice sETI. 

.. figure:: images/main2.png
   :width: 100%
   :align: center
   :alt: GitHub template for the tutorial

   Índice sETI (panel superior)

Los archivos y directorios de mayor importancia se detallan a continuación: ::

  hw_dynamic
  ├── ETI
      ├── run.csh
      ├── runSETI.csh
      ├── data
      ├── figures
      ├── logfiles
      ├── output
      ├── scripts
          ├── get_GFS_ana.sh
          ├── get_GFS_eavg.sh
          ├── get_GFS_ens.sh
          ├── get_GFS_ens_temp.sh
          ├── get_GFS_oper.sh
          ├── get_GFS_oper_temp.sh
          ├── recoverSETI.sh
          └── sETI.m
      ├── tmp
      └── upload
      
``run.csh``: Este script es programado en crontab para ejecutarse diariamente. En él se definen algunas variables que luego son utilizadas en ``runSETI.csh``. 

``runSETI.csh``: Este es el script principal donde es generado el índice sETI. Dentro de él se ejecutan una serie de otros scripts secundarios. 

``data/``: Aquí son guardados los archivos utilizados en la generación del índice. 

``figures/``: Este es el repositorio de figuras generadas. 

``logfiles/``: En este directorio se guarda un archivo de cada ejecución de run.csh. Si por algún motivo la figura del día no es generada, en este archivo se pueden revisar los errores de la ejecución. 

``output/``: Aquí se guardan todos los archivos de la ejecución del día. 

``scripts/``: En este directorio se encuentran todos los scripts utilizados en la generación de sETI.

``tmp/``: Directorio para almacenar las descargas temporales de archivos antes de ser procesados.  

``upload/``: Aquí se guardan una serie de figuras actualizadas utilizadas en hw-monitor.

``seti.m``:  En este script de MATLAB se produce la figura. 

.. warning::
   
   Antes de ejecutar ``run.csh`` se deben cambiar algunas direcciones en los siguientes scripts para adecuarlas a la configuración propia. 

1) run.csh 

.. code:: bash

  set diri=/home/matlab/hw_dynamic

2) runSETI.csh 

.. code:: bash

  set diri=/home/matlab/hw_dynamic
  /usr/local/bin/ncdump -v lat temp.nc | sed -e '1,/data:/d' -e '$d' >& latitudes.log
  /usr/local/bin/matlab -nodisplay -nosplash -nodesktop < sETI.m
