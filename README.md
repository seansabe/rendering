# rendering

El Dockerfile contiene la máquina virtual con Blender para realizar Batch Rendering, es decir, a través de comandos.

1. Para usar esta imagen cree una carpeta del proyecto. Use el terminal para ir al directorio creado.
2. Deje el Dockerfile en dicho directorio y ejecútelo con el comando docker build -t blender .
3. Se debe contar con un archivo .blend dentro del mismo directorio creado.
4. El comando para hacer batch rendering es docker run --rm -v $(pwd):/media/ \
             -u "$(id -u):$(id -g)" \
             eparker05/blender:2.78c \
             blender -b /media/classroom/classroom.blend -o /media/result/frame_### -f 1
             
             Donde $(pwd) es el directorio actual, /media el directorio de la máquina que hace relación al directorio creado en la máquina host, frame_### -f 1 hace referencia el frame 1 del archivo .blend, por lo que si re requiere renderizar otro frame, se debe cambiar el número 1 por el necesario.
