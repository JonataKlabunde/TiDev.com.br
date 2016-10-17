---
layout: post
title: TiDev é open source, contribua!
description: "Gostou? quer contribuir ? veja como!"
tags: [github,opensource,contribuir]
---


# O blog
tidev é um blog voltado para desenvolvedores titanium, facilitando o acesso das informações para você!

<!-- more -->

# onde posso encontralo?
[www.tidev.com.br](www.tidev.com.br)

[github](https://github.com/JonataKlabunde/TiDev.com.br)

# Gostei! posso colaborar?
Que bom que gostou!, esse blog está aberto a toda a comunidade, vejá a baixo como pode coloborar!

## 1 - Clonando o repositório
* baixe o repositório
![clone](/images/readme_clone_git.png)

* discompacte e salve no diretório desejado
![repositorio](/images/readme_repositorio.png)

* altere a url em _config.yml
![_config.yml](/images/readme_config.png)

* instale o 'Jekyll' [instalação jekyll](https://jekyllrb.com/docs/quickstart/) (via terminal)
* ~ $ gem install jekyll bundler
* ~ $ cd /Users/malcus/Documents/TiDev.com.br (entre no seu repositorio)
* ?master ~/Documents/TiDev.com.br> $ bundle exec jekyll serve
* Agora abra um navegador com o seguinte link http://localhost:4000

# Criando um post
para criar um post basta ir no diretório "_post" e criar um novo arquivo com a seguinte nomenclatura "ano-mes-dia-nomedopost.md"
no diretório de post existe varios exemplos de posts (iniciando com 'examplo') neles você pode encontrar varios exemplos de como
formatar os posts

* Todo post criado deve ter esta estrutura definida (layout, title, description, tags)
{% highlight md %}
---
layout: post
title: TiDev é open source, contribua!
description: "Gostou? quer contribuir ? veja como!"
tags: [github,opensource,contribuir]
---
{% endhighlight %}
