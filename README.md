# Install

`apt-get install ruby-full make gcc`

`gem install jekyll bundler`

`bundle install`

Si explotar por que falta la libreria  `nokogiri`

	`apt-get install build-essential patch`

	`apt-get install ruby-dev zlib1g-dev liblzma-dev`

Vuelve a correr el install dentro del directorio

`bundle install`

Para correr localmente el proyecto

`bundle exec jekyll serve -P 5000`

## Demo
View this jekyll theme in action [here](https://vormwald.github.io/joon)

## Screenshot
![screenshot](https://raw.githubusercontent.com/vormwald/joon/master/screenshot.png)

## Font Options

This theme comes with two font options; a serif and sans-serif (the default). 
Switching between them is done in the HTML, by adding `serif` to the `class` of 
the `<body>` element in [head.html](https://github.com/vormwald/joon/blob/master/_layouts/default.html.hbs#L6).

## Colour Options

This theme uses an accent colour for links and the border at the top of pages.

To change this colour, you need to edit [assets/css/screen.css](https://github.com/vormwald/joon/blob/master/assets/css/screen.css).

There are only two values you need to change, conveniently **located at the very
top of the file**.

## For More Information
For more on Jekyll, read the [documentation](http://jekyllrb.com/)


## Copyright & License

Roon is Copyright (c) 2013-2015 Sam Soffes & Ghost Foundation - Released under 
the [MIT license](LICENSE).
