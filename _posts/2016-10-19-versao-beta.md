---
layout: post
title: "Beta Releases for 6.0.0 of SDK, CLI, 4.8.0 of Studio and GA 1.2.8 & 2.0.0 for Hyperloop "
description: "Versão beta para SDK 6.0.0, CLI, Studio 4.8.0 e Hyperloop GA 1.2.8 & 2.0.0"
tags: [Beta Release]
---

<figure style="text-align: center;" >
	<a><img src="/images/posts/2016/10/Beta-release.png" alt="Capa"></a>
</figure>  

## Hoje, publicamos os seguintes lançamentos
 * Versão Beta para Titanium SDK 6.0.0
 * Versão Beta para Appcelerator CLI 6.0.0
 * Versão Beta para Appcelerator Estúdio 4.8.0
 * lançamento para Hyperloop 2.0.0 GA
 * lançamento para Hyperloop 1.2.8 GA

<!-- more -->

## Gostaríamos de agradecer aos membros da comunidade Appcelerator que contribuíram para esta versão.
 * [Michael GANGOLF](https://github.com/m1ga) por seu trabalho com o Android: adicionou setRequestHeaders ({}) ;, docs, adicionou getter, alterando a documentação, adicionando parâmetros, e a atualização da documentação
 * [Rene Pot](https://github.com/Topener) por ter adicionado responseHeaders que faltavam e atualizar a HTTPClient.yml [(TIDOC-2628)](https://jira.appcelerator.org/browse/TIDOC-2628)
 * [Jason Kneen](https://github.com/jasonkneen) por atualizar os recursos e remover a ênfase em tecnologias web em HTML, focando no Nativo

## Nós sabemos que você está animado para testar, mas antes de atualizar, por favor, note:
 * SDK Titanium 6.0.0 Beta é uma versão MAIOR, que requer atualizações para seus aplicativos. Leia este blog e todas as notas da versão ANTES de atualizar.
 * Hyperloop 2.0.0 GA só funcionará com SDK Titanium 6.0.0 e acima.
 * Hyperloop 1.2.8 GA é uma versão que inclui novos recursos, melhorias e correções de bugs. Esta versão só suporta até Titanium SDK 5.5.1.

## As grandes alterações
Nós introduzimos grandes características e melhorias com Titanium SDK 6.0.0. No entanto, algumas dessas mudanças não são compatíveis com as características das versões anteriores. Abaixo está um resumo das alterações significativas, bem como a forma de lidar com elas.

### Node.js
SDK 6.0.0 traz suporte completo Node.js, assim os usuários podem usar módulos de NPM para plataformas Android e iOS [(TIMOB-16078)](https://jira.appcelerator.org/browse/TIMOB-16078). Node 4.2.0 é a nova versão mínima suportada e 4.6.x é a versão máxima suportada. Por favor, instalar ou atualizar o Node.js em conformidade.

### Xcode
Xcode 8.0, que suporta Swift 2.3+, watchOS 2 e 3, e iOS 8+, é a versão mínima suportada. Por favor, instalar ou atualizar Xcode em conformidade.

### APIs desaprovadas
Nós removemos 176+ APIs relacionadas iOS e Android. Por favor, consulte [esta tabela](http://docs.appcelerator.com/platform/latest/#!/guide/Titanium_SDK_6.0.0.Beta_Release_Note-section-48431440_TitaniumSDK6.0.0.BetaReleaseNote-APIchanges) para ver como ele iria afetar seus projetos.

### Watchos 1
A partir do SDK 6.0.0, o modelo watchos 1 e todo o código relacionado não são mais suportados. Veja [TIMOB-20083](https://jira.appcelerator.org/browse/TIMOB-20083) para mais detalhes.

### Escuta androidback
Para SDK 6.0.0, mudou a forma com a substituição do comportamento padrão para o botão Voltar do Android. Esta alteração requer o aplicativos com esta versão para substituir o botão de volta e atualizar seu código quando for utilizado chamadas como esta: ``` win.addEventListener('androidback', onback); ``` Veja [TIMOB-19919](https://jira.appcelerator.org/browse/TIMOB-19919) para mais detalhes.

### Registrando as portas do sistema e TCP
O novo sistema de registro usa uma porta TCP [(TIMOB-23786)](https://jira.appcelerator.org/browse/TIMOB-23786). O número da porta é SEMPRE determinado em tempo de compilação, não em tempo de execução. Isto significa que se você construir dois aplicativos de titânio diferentes, eles não podem usar a mesma porta ao mesmo tempo. Existem algumas maneiras com ferramentas para superar isso. Veja as notas de versão para obter detalhes.

### Reconstruir Modules Android
V8 foi atualizado para a última versão 'Long Term Support' (LTS) [(TIMOB-19790)](https://jira.appcelerator.org/browse/TIMOB-19790). módulos de titânio Android devem ser reconstruído com este V8 a fim de ser suportado no titânio SDK 6.0.0.

### Você precisará atualizar o android / manifest da seguinte forma:
 1. Altere apiversion 2-3.
 2. Remover "armeabi" ABI da lista (mantenha "armeabi-v7a").
 3. Altere a versão do modulo (nolmalmente uma versão importante, já que não é compativel com as versões anteriores).
 4. Atualizar minsdk para 6.0.0.
 5. Em seguida, reconstruir o módulo.
Nota, você também pode precisar editar o código Java para remover referências e depreciar as classes que foram removidos no 6.0.0 (como TiContext).

## Outros Itens notáveis ​​na liberação
 Aqui estão mais algumas características notáveis ​​e melhorias desta versão:
  * Capacidade de ativar Multi-dex para evitar o limite de 65k método durante Android constrói
  * Capacidade para aplicativos usando <use-jscore-framework> para usar Studio debugger. No iOS, você vai precisar definir True para funcionar. Além disso, você pode usar o Safari para debugar seu aplicativo.
  * Suporte para 'iphone 7 haptic engine api'

## Problemas conhecidos
  * Hyperloop: Erros durante a execução de projeto com visualização ao vivo e hyperloop habilitados [(TIMOB-23761)](https://jira.appcelerator.org/browse/TIMOB-23761)
  * Android: Depuração não funciona com o hyperloop habilitado com run-on-main-thread definido como verdadeiro ou falso [(TIMOB-24037)](https://jira.appcelerator.org/browse/TIMOB-24037)
  * iOS Debugger: Breakpoint não é atingido pela primeira vez para um projeto de liga limpo [(TISTUD-8613)](https://jira.appcelerator.org/browse/TISTUD-8613)

## Notas da versão
 Esses lançamentos incluem 190 correções de bugs, 49 melhorias e 23 novos recursos. Para uma visão mais detalhada, problemas conhecidos e problemas resolvidos consulte os seguintes links

 * [SDK Titanium 6.0.0 Beta Release Note](http://docs.appcelerator.com/platform/latest/#!/guide/Titanium_SDK_6.0.0.Beta_Release_Note)

 * [Appcelerator Estúdio 4.8.0 Beta Release Note](http://docs.appcelerator.com/platform/latest/#!/guide/Studio_4.8.0.Beta_Release_Note)

 * [Appcelerator CLI 6.0.0 Beta Release Note](http://docs.appcelerator.com/platform/latest/#!/guide/Appcelerator_CLI_6.0.0.Beta_Release_Note)

 * [Hyperloop 2.0.0 Release Note](http://docs.appcelerator.com/platform/latest/#!/guide/Hyperloop_2.0.0_Release_Note)

 * [Hyperloop 1.2.8 Release Note](http://docs.appcelerator.com/platform/latest/#!/guide/Hyperloop_1.2.8_Release_Note)

## Atualização Titanium SDK
Para atualizar o SDK Titanium partir da linha de comando:
{% highlight md %}[appc] ti sdk install --branch 6_0_X 6.0.0.v20161017194738{% endhighlight %}

Para reverter:
{% highlight md %}[appc] ti sdk select latest{% endhighlight %}


## Atualização Appcelerator CLI
 Tanto o Appcelerator CLI Installer e o 'core packge' foram atualizados.

 Para atualizar a partir da linha de comando:

 {% highlight md %}[sudo] npm install -g appcelerator@4.2.8-7 appc use 6.0.0-61{% endhighlight %}

 Para reverter:

 {% highlight md %}[sudo] npm install -g appcelerator{% endhighlight %}

## Atualização Appcelerator Estúdio
 Obter a versão beta do [Estúdio alterando o tipo de atualização para versão beta](http://docs.appcelerator.com/platform/latest/#!/guide/Changing_the_Update_Type-section-30083272_ChangingtheUpdateType-ChangingtheUpdateType) e, em seguida, verificar se há atualizações.

 Para reverter/excluir a versão beta e [baixar e instalar a última versão estável](https://platform.appcelerator.com/#/product/studio).

## atualização Hyperloop

 Para usar Hyperloop 1.2.8, você não precisa atualizar SDK Titanium. Você pode atualizar a partir da linha de comando usando:
 {% highlight md %}appc new{% endhighlight %}

 Para usar Hyperloop 2.0.0, atualização para Titanium SDK 6.0.0, em seguida, atualizar a partir da linha de comando usando:

 {% highlight md %}appc new{% endhighlight %}

 NOTA: O método acima só funciona usando appc cli 6.0.0-61. Alternativamente, Insira ```appc config set lastUpdateCheckTiDownloads null``` antes de executar a configuração appc, irá desencadear o download dos módulos.

## Reportar erros
 Se você tiver quaisquer problemas que parecem relacionadas com as atualizações, por favor informe-los no [JIRA](https://jira.appcelerator.org).

 Primeiro, verifique se é um problema conhecido que você pode assistir. Se você não consegue encontrar um ticket existente, em seguida, crie um no projeto Appcelerator Community (AC) e adicione o máximo de [informações relevantes](http://docs.appcelerator.com/platform/latest/#!/guide/How_to_Submit_a_Bug_Report) quanto possível, incluindo a versão que você está usando.

 Você pode deixar comentários gerais como uma resposta a este post.

 Para Mais informações acesso o [Blog oficial](http://www.appcelerator.com/blog/2016/10/beta-releases-for-6-0-0-of-sdk-cli-4-8-0-of-studio-and-ga-1-2-8-2-0-0-for-hyperloop/)
