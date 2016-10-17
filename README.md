# tidev.com.br
tidev é um blog voltado para desenvolvedores titanium, facilitando o acesso de um maior numero de pessoas!

# onde posso encontralo?
dominio - www.tidev.com.br
github - https://github.com/JonataKlabunde/TiDev.com.br

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

* todo post deve ter estas estrutura definida (layout, title, description, tags)
```
---
layout: post
title: Este é o titulo do post
description: "Essa é a descrição"
tags: [tags relacionadas ao assuto dos post ex, post, tutorial, criar post]
---
```
