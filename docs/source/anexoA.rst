****
Repositorios de datos
****

.. Repositorios: interno:

Repositorio interno
==== 

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

Repositorios externos
====

JMA, mjo_repo y SERVIMET almacenan figuras descargadas mediante un script simple programado para ejecutarse una vez al día (3 veces en el caso de SERVIMET). ::

  hw_dynamic
  ├── JMA
      └── jma_repo.csh
  ├── mjo_repo
      ├── bom
          ├── RMM_40_days
          └── RMM_90_days
      ├── ncpe
      └── mjo_repo.csh
  └── SERVIMET
      ├── cartas_color
      └── servimet.csh
      
.. warning::

  En estos scripts hay que modificar las siguientes líneas para adecuarlas a la configuración propia..

1. jma_repo.csh

.. code:: bash
  
  cd /home/matlab/hw_dynamic/JMA
  
2. mjo_repo.csh

.. code:: bash

  cd /home/matlab/hw_dynamic/mjo_repo
  
3. servimet.csh

.. code:: bash

  cd /home/matlab/hw_dynamic/SERVIMET

JMA
=====

.. figure:: images/main3.gif
   :width: 75%
   :align: center
   :alt: GitHub template for the tutorial

   OLR y función corriente de 200 hPa y el flujo de actividad de onda (anomalía) emitido por la Agencia Meteorológica de Japón (JMA)

mjo_repo
=====

.. figure:: images/main4.gif
   :width: 75%
   :align: center
   :alt: GitHub template for the tutorial

   Pronóstico basado en MJO GFS emitido por el Centro de Predicción Climática de la NOAA de EE. UU

SERVIMET
=====

.. figure:: images/main5.jpeg
   :width: 75%
   :align: center
   :alt: GitHub template for the tutorial

   Cartas sinóptica emitida por el Servicio Meteorológico de la Armada de Chile (SERVIMET)
