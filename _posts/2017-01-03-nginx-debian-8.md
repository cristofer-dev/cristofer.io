---
layout: post
title: "Nginx on Debian 8"
image: img1.png
video: false
---

Instalar Nginx en Debian 8 junto a apache

###### Stop apache

{% highlight Bash %}
service apache2 stop
{% endhighlight %}



###### Update y upgrade

{% highlight Bash %}
apt-get update
apt-get upgrade
{% endhighlight %}



###### Install FPM

{% highlight Bash %}
apt-get install php5-fpm
{% endhighlight %}



###### Install Nginx

{% highlight Bash %}
apt-get install nginx-full
{% endhighlight %}



###### Configure php.ini for work MongoDB

en la ruta <code>/etc/php5/fpm/php.ini</code> agregar

{% highlight Bash %}
[mongo]
extension=mongo.so
{% endhighlight %}

Al hacer cambios en `php.ini` debemos reiniciar el servicio `php5-fpm`

{% highlight Bash %}
service php5-fpm restart
{% endhighlight %}


###### Configurar el HOST 

El archivo de configuración se encuentra en `/etc/nginx/sites-available/`, en este directorio viene por defecto un archivo `default` el cual contiene la configuración basica.

Le cambiaremos en nombre, por que no lo utilizaremos, pero no lo eliminaremos, por si lo necesitamos mas adelante.

{% highlight Bash %}
mv default default.backup
{% endhighlight %}

luego creamos un nuevo archivo `default` haciendo 


{% highlight Bash %}
nano /etc/nginx/site-available/default
{% endhighlight %}

se abrira nano, y pondremos la siguiente configuración:

Dominio: **default**


{% highlight Bash %}

server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/;
        index index.php index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                try_files $uri $uri/ /index.php;
        }

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_buffers 16 16k;
                fastcgi_buffer_size 32k;
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_param ENVIRONMENT production;
        }
        location ~ /\.ht {
                deny all;
        }
}

{% endhighlight %}


luego, copiamos el archivo 

{% highlight Bash %}
cp default blog.cristofer.io
{% endhighlight %}

esto hara que se cree una copia del archivo pero con el nomre `blog.cristofer.io`

lo abrimos y lo editamos con `nano blog.cristofer.io`


Dominio: **blog.cristofer.io**

{% highlight Bash %}

server {
        listen 80;
        listen [::]:80;

        root /var/www/blog.cristofer.io;
        index index.php index.html index.htm index.nginx-debian.html;

        server_name blog.cristofer.io;

        location / {
                try_files $uri $uri/ /index.php;
        }

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_buffers 16 16k;
                fastcgi_buffer_size 32k;
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_param ENVIRONMENT production;
        }
        location ~ /\.ht {
                deny all;
        }
}

{% endhighlight %}


### Seteando variables de entorno para PHP

LINEA 21: `fastcgi_param APP_ENV production;`\\
donde:\\
`APP_ENV` es el nombre de la variable\\
`production` es el valor de la variable

{% highlight Bash linenos%}

server {
	listen 80 default_server;
	listen [::]:80 default_server;

	root /var/www/api.cristofer.com;

	index index.php index.html index.htm index.nginx-debian.html;	

	server_name api.cristofer.com;

	location / {
		try_files $uri $uri/ /index.php;
	}

	location ~ \.php$ {
		include snippets/fastcgi-php.conf;
		fastcgi_buffers 16 16k;
		fastcgi_buffer_size 32k;
		fastcgi_split_path_info ^(.+\.php)(/.+)$;
		fastcgi_pass unix:/var/run/php5-fpm.sock;
		fastcgi_param APP_ENV production;
	}
	location ~ /\.ht {
		deny all;
	}
}


{% endhighlight %}


### Habilitando Puertos

{% highlight Bash linenos%}

Habilitando el HOST en el puerto `8080`

server {
	listen 8080 default_server;
	listen [::]:8080 default_server;
...
...
}

{% endhighlight %}

### Comandos Utiles

<div class="table-responsive" markdown="1">

Iniciar | `service nginx start`
Detener | `service nginx stop`
Recargar configuración | `service nginx reload`
Reinicia el servicio | `service nginx restart`
Estado del servicio | `service nginx status`

</div>


<script>
  $( "table" ).addClass( "table table-hover" );
</script>

