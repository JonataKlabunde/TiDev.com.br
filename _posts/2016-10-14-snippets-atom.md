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


{% highlight CoffeeScript %}
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
