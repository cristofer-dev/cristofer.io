---
layout: post
title: "Apuntes Terminal Linux"
image: img2.png
video: false
---

Comandos utiles de uso cotidiano. Las cosas que siempre olvidas ;)

<div class="table-responsive" markdown="1">

 **Moverse por el sistema de archivos** |
Directorio actual | `pwd`


**Agente SSH** |
Terminar agente			    | `killall ssh-agent`
Iniciar Agente			    | `eval $(ssh-agent -s)`
Agregar llave al agente	| `ssh-add /ruta/llave_privada` 
Crear par de llaves SSH	| `ssh-keygen`


**Sistema** |
ver procesos corriendo						          | `top`
matar proceso indicando el id				        | `kill 9999`
Ver tamaño de carpeta ( DU = Disk Usage ) 	| `du -bsh /fichero_carpeta`
Uso del disco duro                          | `df`
Uso del disco duro (iNodos)                 | `df -i`
buscar texto recursivo en un directorio		  | `grep -ri "izitdb.com" /srv/websites/`
Guardar salida en archivo				          	| `[comando] > archivo.txt`
agregar salida al final del archivo			    | `[comando] >> archivo.txt`
Crear usuario								                | `adduser luis`
Cambiar clave de otro usuario				        | `passwd luis`
Apagar Sistema                              | `sudo shutdown -h now`
Reiniciar                                   | `sudo shutdown -r now`


**Liberar Espacio** |
Elimina cache de los paquetes antiguos instalados    | `apt-get autoclean`
Elimina cache de los paquetes actuales instalados    | `apt-get clean`
Elimina paquetes huérfanos            | `sudo apt-get autoremove`

</div>



<script>
  $( "table" ).addClass( "table table-hover" );
  
	
</script>

