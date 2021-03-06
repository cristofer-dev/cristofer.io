---
layout: post
title: "CodeCommit"
image: aws.png
---

Creando el repositorio GIT en aws

# Primero
Para poder acceder a los repositorios de AWS las conexiones pueden ser hecha por `SSH` y `https`, para este caso usaremos `SSH`.

Las conexiones `SSH` en una terminal linux tienen la siguiente estructura:

{% highlight Bash %}
git clone ssh://XXXXXXXXXXXXXXXXXXXX@git-codecommit.uk-west-6.amazonaws.com/v1/repos/ProyectoEjemplo
{% endhighlight %}  


`XXXXXXXXXXXXXXXXXXXX` corresponde al **`SSH key ID`** generado para cada usuario desde la consola de IAM de AWS en la pestaña **users > Security credentials > SSH keys for AWS CodeCommit**

Para poder generar el **`SSH key ID`** AWS necesitaremos un par de llaves SSH e indicarle a AWS la `.pub` para que nos genere un **`SSH key ID`** y poder hacer las conexiones con el servicio por protocolo seguro.


Lo que sigue despues de `@` es en `endpoint` del repositorio que te lo entregara CodeCommit una vez creado el repositorio. 


Dicho lo anterior

# Creando un Repositorio para un proyecto nuevo

- Crear repositorio en CodeCommit
- Clonar el repo

Ya puedes empezar a crear tu proyecto, hacer tus commits, pull y push al repo.

# Creando un Repositorio para un proyecto existente

- Crear repositorio en CodeCommit

En la carpeta local donde ya esta tu proyecto versionado apuntando a otro `origin` agregaremos un segundo origen remoto pero con otro nombre para no confundirnos.


{% highlight Bash %}
git remote add amazon XXXXX@git-codecommit.uk-west-6.amazonaws.com/v1/repos/ProyectoEjemplot
{% endhighlight %}  

ya Agregado el segundo repo remoto, podemos verificar si esta todo bien ejecutando

{% highlight Bash %}
git remote -v
{% endhighlight %}  


Ya podemos hacer `push`

{% highlight Bash %}
git push amazon master
{% endhighlight %}  

Si todo salio bien, deberiamos tener nuestro código fuente en CodeCommit