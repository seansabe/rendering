# rendering

El Dockerfile contiene la máquina virtual con Blender para realizar Batch Rendering, es decir, a través de comandos.

1. Para usar esta imagen cree una carpeta del proyecto. Use el terminal para ir al directorio creado.
2. Deje el Dockerfile en dicho directorio y ejecútelo con el comando 

docker build -t blender .

3. Se debe contar con un archivo .blend dentro del mismo directorio creado. 3d y classroom son los ficheros con los .blend ejemplo para renderizar.
4. El comando para hacer batch rendering es 

docker run --rm -v $(pwd):/media/ \
             -u "$(id -u):$(id -g)" \
             eparker05/blender:2.78c \
             blender -b /media/classroom/miarchivo.blend -o /media/frame_### -f 1
             
Donde $(pwd) es el directorio actual, /media el directorio de la máquina que hace relación al directorio creado en la máquina host, frame_### -f 1 hace referencia el frame 1 del archivo .blend, por lo que si re requiere renderizar otro frame, se debe cambiar el número 1 por el necesario. /media/frame_### -f 1 es el directorio donde se creará el frame renderizado.


Dockerfile2 contiene la máquina virtual con los comandos para aprovicionar Blender y HTCondor. (Remover el 2 del nombre)

1. Crear un directorio en el equipo host.
2. Llegar al directorio por consola y ejecutar el comando

docker build -t htcondor_blender .
