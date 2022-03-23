****
Estructura
****

.. Estructura:

Con la finalidad de realizar un monitoreo operacional, es necesario establecer un orden en los archivos tanto generados como recopilados desde fuentes externas. Debe tener un directorio base, referido aqui como ``hw_dynamic``. Los archivos se agrupan en directorios, que a su vez se organizan en una jerarquía. Cada uno de los directorios se describe en las secciones siguientes. ::

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
       ├──  data
       ├──  figures
       ├── files
       ├── logfiles
       ├── output
       ├── scripts
       ├── tmp
       └── upload
   
   ├── JMA
   ├── mjo_repo
   └── SERVIMET

