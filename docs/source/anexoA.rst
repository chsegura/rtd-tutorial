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
      ├── files
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
      
``data/``: 

``figures/``: 

``files/``: 

``logfiles/``: 

``output/``: 

``scripts/``: 

``tmp/``: 

``upload/``: 
   
Antes de ejecutar estas rutinas se deben cambiar algunas direcciones de los archivos 

1) run.csh 

.. code:: bash

  set diri=/home/matlab/hw_dynamic

2) runSETI.csh 

.. code:: bash

  set diri=/home/matlab/hw_dynamic
  /usr/local/bin/ncdump -v lat temp.nc | sed -e '1,/data:/d' -e '$d' >& latitudes.log
  /usr/local/bin/matlab -nodisplay -nosplash -nodesktop < sETI.m

3) recoverSETI.csh 

.. code:: bash

  set diri=/home/matlab/hw_dynamic

4) get_GFS_ana.csh 

.. code:: bash

  set diri=/home/matlab/hw_dynamic

5) get_GFS_oper.sh 

.. code:: bash

  SCRIPTPATH=/home/matlab/hw_dynamic/ETI/scripts
  EXDATAPATH=/home/matlab/hw_dynamic/ETI/tmp

6) get_GFS_eavg.sh 

.. code:: bash

  SCRIPTPATH=/home/matlab/hw_dynamic/ETI/scripts
  EXDATAPATH=/home/matlab/hw_dynamic/ETI/tmp

7) get_GFS_ens.sh 

.. code:: bash

  SCRIPTPATH=/home/matlab/hw_dynamic/ETI/scripts
  EXDATAPATH=/home/matlab/hw_dynamic/ETI/tmp
