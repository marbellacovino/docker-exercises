# Indica la diferencia entre el uso de la instrucción ADD y COPY (Dockerfile)

COPY y ADD son instrucciones similares que permiten copiar archivos a un directorio especifico en una imagen Docker. 
COPY pernite copiar archivos o carpetas del sistema local a una imagen Docker. ADD permite lo mismo pero la source puede ser el sistema local o una URL y ademas permite extraer un archivo tar de la fuente directamente al destino.

