Anexo A: ETI
=====

.. Anexo A: ETI:

ETI contiene una serie de subdirectorios, rutinas y scripts que generan un pronóstico diario del índice sETI. Donde se debe programar a medio dia en crontab la ejecución del script run.csh ::

  hw_dynamic
  ├── ETI
      ├── data
      ├── figures
      ├── files
      ├── logfiles
      ├── output
      ├── scripts
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

1) run.csh ::

  set diri=/home/matlab/hw_dynamic

2) runSETI.csh ::

  set diri=/home/matlab/hw_dynamic
  /usr/local/bin/ncdump -v lat temp.nc | sed -e '1,/data:/d' -e '$d' >& latitudes.log
  /usr/local/bin/matlab -nodisplay -nosplash -nodesktop < sETI.m

3) recoverSETI.csh ::

  set diri=/home/matlab/hw_dynamic

4) get_GFS_ana.csh ::

  set diri=/home/matlab/hw_dynamic

5) get_GFS_oper.sh ::

  SCRIPTPATH=/home/matlab/hw_dynamic/ETI/scripts
  EXDATAPATH=/home/matlab/hw_dynamic/ETI/tmp

6) get_GFS_eavg.sh ::

  SCRIPTPATH=/home/matlab/hw_dynamic/ETI/scripts
  EXDATAPATH=/home/matlab/hw_dynamic/ETI/tmp

7) get_GFS_ens.sh ::

  SCRIPTPATH=/home/matlab/hw_dynamic/ETI/scripts
  EXDATAPATH=/home/matlab/hw_dynamic/ETI/tmp
