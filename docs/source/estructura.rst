****
Estructura
****

.. Estructura:

Con la finalidad de realizar un monitoreo operacional es necesario establecer un orden en los archivos tanto generados como recopilados desde fuentes externas. Luego de establecer un directorio base, referido aqui como ``hw_dynamic``, las distintas componentes utilizadas en **hw-monitor** se agrupan en subdirectorios, que a su vez se organizan en su propia jerarquía. El sistema de archivos se ve de esta forma: ::

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

Cada uno de estos subdirectorios se describe en las secciones siguientes.

.. note::

   En el esquema mostrado arriba no se muestra la totalidad de archivos contenidos en cada uno de los sub y subsub directorios. 
