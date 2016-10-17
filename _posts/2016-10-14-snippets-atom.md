---
layout: post
title: "Snippets - Crie seus próprios fragmentos de código!"
description: "Se você é um desenvolvedor Titanium e já é adepto do Atom, esse 'post' pode lhe interessar!"
tags: [atom,snippets]
---


Se você é um desenvolvedor Titanium e já é adepto do Atom, esse 'post' pode lhe interessar!


<figure style="text-align: center;" >
	<a><img src="/images/posts/2016/10/snippet.png" alt="imagem do código"></a>
</figure>   

<!-- more -->


<!-- PARA JS -->
{% highlight CoffeeScript %}
################
### para JS ###
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
### para XML ###
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
### para TSS ###
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