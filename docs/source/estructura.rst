****
Estructura de la aplicación
****

.. Estructura:

Con el objetivo de llevar a cabo un monitoreo operativo eficiente, es fundamental establecer una estructura clara y ordenada para los archivos generados y recopilados de fuentes externas. Para ello, se ha establecido un directorio base denominado ``hw_dynamic``, en el cual se agrupan las distintas componentes utilizadas en `hw-monitor <https://www2.dgeo.udec.cl/shiny/hw-monitor/>`_ en subdirectorios que siguen una jerarquía bien definida. El sistema de archivos se organiza de la siguiente manera:
::

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

   ├── ETI
       ├── data
       ├── figures
       ├── files
       ├── logfiles
       ├── output
       ├── scripts
       ├── tmp
       └── upload
   
   ├── JMA
   ├── mjo_repo
   └── SERVIMET

En las secciones siguientes, se describirá con más detalle el contenido de cada uno de estos subdirectorios.

.. note::

   Es importante tener en cuenta que el esquema presentado anteriormente no muestra la totalidad de los archivos almacenados en cada uno de los subdirectorios y sub-subdirectorios. No obstante, se pretende ofrecer una visión general y clara de la estructura general del sistema de archivos utilizado en `hw-monitor <https://www2.dgeo.udec.cl/shiny/hw-monitor/>`_. Para obtener información más detallada sobre los archivos específicos contenidos en cada subdirectorio, se recomienda revisar las secciones correspondientes en este documento. 
