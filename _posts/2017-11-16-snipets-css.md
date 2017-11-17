---
layout: post
title: "CSS Snippet"
image: css-code.jpg
published: true
---

Las cosas básicas de **CSS** que siempre usamos y que siempre olvidamos...


Selectores por elemento
=======================================

###### Universal  
{% highlight CSS %}
* {}
{% endhighlight %}

###### tag (elemento)
{% highlight CSS %}
div {}
{% endhighlight %}

###### Clase
{% highlight CSS %}
.menu {}
{% endhighlight %}

###### ID
{% highlight CSS %}
#miId {}
{% endhighlight %}

###### Hijos
{% highlight CSS %}
p > span {}
.menu > div {}
#menu > span > i {}
{% endhighlight %}

###### Adyacentes
{% highlight CSS %}
elemento1 + elemento2 { }
#menu + #menu2 {}
{% endhighlight %}


Selectores por atributos
=======================================


{% highlight CSS %}
/* Todos los elementos que tengan el atributo indicado (independiente de su valor)*/
selector[atributo] { }

/* Todos los elementos que tengan el atributo indicado y cuyo valor sea = valor*/
selector[atributo="valor"] { }

/* Todos los elementos que tengan el atributo indicado  en el que al menos uno de sus valores sea "valor1" */
selector[atributo~="valor1"] { }

{% endhighlight %}