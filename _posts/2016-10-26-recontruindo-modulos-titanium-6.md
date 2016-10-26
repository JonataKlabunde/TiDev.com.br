---
layout: post
title: "Reconstruindo seus modulos para o Titanium 6"
description: "Varios módulos que usamos em nossos aplicativos não são suportados. Então, eu fiz o meu melhor para atualizá-los para apoiar o Titanium 6. Se você estiver interessado nos passos necessários para obter um módulo compativel vejá esse post! [Tim Poulsen](http://skypanther.com/2016/10/rebuilding-modules-for-titanium-6/)"
tags: [Tim Poulsen,Titanium 6,Módulos]
---

<figure style="text-align: center;" >
	<a><img src="/images/posts/2016/10/rebuilding.png" alt="Rebuilding"></a>
</figure>  

Varios módulos que usamos em nossos aplicativos não são suportados. Então, eu fiz o meu melhor para atualizá-los para apoiar o Titanium 6. Se você estiver interessado nos passos necessários para obter um módulo compativel vejá esse post! [Tim Poulsen](http://skypanther.com/2016/10/rebuilding-modules-for-titanium-6/)



<!-- more -->

Não sou especialista com módulos, nem sou um guru do Android nativo. Mas, quando o seu aplicativo depende de oito ou dez módulos nativos e Appcelerator anuncia alterações significativas na sua SDK, às vezes você tem que apenas mergulhar e dar o seu melhor tiro.

Appcelerator lançou a versão beta do Titanium 6. Com isso, foi atualizado o motor V8 usado no Android. Isso nos promete maior desempenho e várias correções de bugs. Mas, isso também significa que todos os módulos Android nativas que você usa em seu aplicativo devem ser atualizado e recompilados com "Ti 6 tooling".

Eu tenho ido através dos módulos que os nossos aplicativos usam. Até agora, tudo foi bem tranquilo. Para aqueles que enfrentam uma situação semelhante, eu pensei em compartilhar as minhas notas do que eu encontrei, e o que foi necessário para este processo.

Aqui estão os passos que eu tive que fazer até agora:

## Atualizar o arquivo manifest do seu módulo:
* Altere o 'apiversion' 2 -> 3.
* Remova "armeabi" ABI da lista (mantenha "armeabi-v7a").
* Atualize o minsdk para 6.0.0.v20161017194738 (você vai definir isso para 6.0.0 uma vez que o SDK for para GA)
* Altere sua versão do módulo (normalmente um número importante uma vez que esta é uma mudança incompátivel com as anteriores).

## Atualizar o arquivo build.properties do seu módulo:
* titanium.platform deve apontar para o 6.0.0.v20161017194738 TiSDK (mais uma vez, use a versão 6.0.0.GA assim que estiver disponível)
* certificar-se da API / níveis de API do Google estão definidas para algo como 23
* você vai querer usar android-ndk-r10e NDK ou mais recente (veja as minhas notas abaixo para o meu ambiente de compilação)

## Alterações no código
Você precisará remover todas as referências do TiContext, como ele foi removido a partir do SDK. Até agora, as únicas referências que eu vi foram em construtores sobrecarregados. Nesses casos, eu simplesmente excluídos aqueles construtores, bem como as instruções de importação.

Dependendo da idade da base de código que você está trabalhando, você também pode ter de atualizar algumas declarações de importação. Eu encontrei estas mudanças de classe nos módulos já atualizados:

`org.appcelerator.titanium.util.TiConfig está agora org.appcelerator.kroll.common.TiConfig`
`org.appcelerator.titanium.util.Log está agora org.appcelerator.kroll.common.Log`

Você pode encontrar informações úteis para fazer referência em alguns dos módulos que a Appcelerator atualizou para ver os tipos de mudanças que foram feitas. Por exemplo:

* ti.facebook: <https://github.com/appcelerator-modules/ti.facebook/pull/55/>
* ti.map: <https://github.com/appcelerator-modules/ti.map/pull/167/files>
* ti.touchid: <https://github.com/appcelerator-modules/ti.touchid/pull/19/files>

## Meu ambiente de compilação

Apenas para referência, este é o meu ambiente. Provavelmente, você pode usar outras versões de todos estes componentes.

* Ti SDK 6.0.0.v20161017194738
* APPC CLI 6.0.0-61
* Nó 4.2.4 (mais recente seria provavelmente muito melhor, já que esta é a versão suportada min)
* APIs do Android / APIs do Google: 23
* Android NDK-ndk-r10e (versão R11c também deve ser compatível, eu somente não atualizei ainda)

Um grande obrigado a [@hans](https://github.com/hansemannn) no TiSlack por me ajudar a descobrir os procedimentos.

por [Tim Poulsen](http://skypanther.com/2016/10/rebuilding-modules-for-titanium-6/)
