---
layout: post
title: TiDev é open source, contribua!
description: "Gostou? Quer contribuir? Veja como:"
tags: [github,opensource,contribuir]
---


### O blog
O tidev é um blog voltado para desenvolvedores [Titanium](http://www.appcelerator.org/#titanium), facilitando o acesso das informações para nós!

<!-- more -->

### Onde posso encontra-lo?
[www.tidev.com.br](www.tidev.com.br)

[github](https://github.com/JonataKlabunde/TiDev.com.br)

### Gostei! Posso colaborar?
Que bom que gostou! Esse blog está aberto a toda a comunidade. Veja abaixo como colaborar!

##### 1 - Clonando o repositório
* Baixe o repositório
![clone](/images/readme_clone_git.png)

* Descompacte e salve no diretório desejado
![repositorio](/images/readme_repositorio.png)

* Altere a url em _config.yml
![_config.yml](/images/readme_config.png)

* instale o 'Jekyll' [instalação jekyll](https://jekyllrb.com/docs/quickstart/) (via terminal)
* ~ $ gem install jekyll bundler
* ~ $ cd /Users/malcus/Documents/TiDev.com.br (entre no seu repositório)
* ?master ~/Documents/TiDev.com.br> $ bundle exec jekyll serve
* Agora abra um navegador com o seguinte link http://localhost:4000

# Criando um post
Para criar um post basta ir no diretório "_post" e criar um novo arquivo com a seguinte nomenclatura "ano-mes-dia-nomedopost.md".  
No diretório de posts você pode encontrar vários exemplos (iniciando com 'exemplo') com diferentes maneiras de como formatar seus posts

* Todo post criado deve ter esta estrutura definida: (layout, title, description, tags)
{% highlight md %}
---
layout: post
title: TiDev é open source, contribua!
description: "Gostou? Quer contribuir? Veja como:"
tags: [github,opensource,contribuir]
---
{% endhighlight %}
