---
layout: post
title: "Android Logs"
image: android.jpg
---

Ver logs de un dispositivo ANDROID en Debian 8.


###### Actualizamos

{% highlight Bash %}
apt-get update
apt-get upgrade
{% endhighlight %}


###### Instalamos
{% highlight Bash %}
apt-get install android-tools-adb
{% endhighlight %}


###### Para ver la version instalada
{% highlight Bash %}
adb version

# deberia retornar algo como:
Android Debug Bridge version 1.0.31
{% endhighlight %}

###### Ver dispositivos conectados
{% highlight Bash %}
adb devices

# Retornara algo como:

* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 
ZY223RJ27V  offline
{% endhighlight %}


###### Ver logs
Para ello usaremos logcat
{% highlight Bash %}
adb -d logcat com.miapp
{% endhighlight %}