---
layout: post
title: "Snippets - Crie seus próprios fragmentos de código!"
description: "Se você é um desenvolvedor Titanium e já é adepto do Atom, esse 'post' pode lhe interessar!"
tags: [atom,snippets,programação]
---


Se você é um desenvolvedor Titanium e já é adepto do ["Atom"](https://atom.io/), esse 'post' pode-lhe interessar!


<figure style="text-align: center;" >
	<a><img src="/images/posts/2016/10/snippet.gif" alt="imagem do código"></a>
</figure>   

<!-- more -->

Você gosta de utilizar o auto-complete? Saiba que com o ["Atom"](https://atom.io/) é possível você criar seus trechos de códigos (Snippets), para serem chamados no auto-complete, para criar o seu faça o seguintes passos:

* Abra o ["Atom"](https://atom.io/), e no menu Atom, selecione o item "Snippets..."
<figure style="text-align: center;" >
	<a><img src="/images/posts/2016/10/atom snippet.png" alt="imagem do código"></a>
</figure>   

* Agora adicione os trechos de código abaixo:

<!-- PARA JS -->
{% highlight CoffeeScript %}
################
### Para JS ###
################
'.source.js':
  'function(e){}':
    'prefix': 'funExport'
    'body': """
      function ${1:nome}(e){
          $2
      }
      exports.${1:nome} = ${1:nome};
    """
    'description': 'Função com Exports'
    'rightLabelHTML': '<span style="color:#2ef541">Jonata</span>'
    {% endhighlight %}


<!-- PARA XML -->
{% highlight CoffeeScript %}
################
### Para XML ###
################
'.text.alloyxml':
  'initXml':
    prefix: 'xml'
    body: """
      <Alloy>
      	<Window id='${1:index}' onOpen='${2:open}' onFocus='${3:focus}' onAndroid:back="${4:voltar}" >
      		<View id="view" >
      		</View>
      	</Window>
      </Alloy>
    """
    description: 'start my structure xml'
    rightLabelHTML: '<span style="color:#2ef541">Jonata</span>'
{% endhighlight %}

<!-- PARA TSS -->
{% highlight CoffeeScript %}
################
### Para TSS ###
################
'.source.css.tss':
  'minhaClass':
    prefix: 'class'
    body: """
      ".class":{
       	width: Ti.UI.FILL,
       	height: Ti.UI.FILL
       }
    """
    description: 'Class Exemplo'
    rightLabelHTML: '<span style="color:#2ef541">Personalizado</span>'
{% endhighlight %}

* Após adicionar, salve o arquivo e pronto! Já é possivel fazer a chamada do seu código.

## Algumas explicações
* O simbolo ``` "$1", "$2" ``` (sifrão + numero) representa a ordem em que o 'cursor' será posicionado ao dar a tecla 'Tab'.
* ``` id='${1:index}' ``` nesse trecho de código esta definido	 'index' como valor inicial e as chaves '{}' irão selecionar o conteúdo quando o cursor for posicionado.



Para mais detalhes veja a [documentação dos snippets](https://atom.io/packages/snippets)
