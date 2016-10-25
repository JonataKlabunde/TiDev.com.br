---
layout: post
title: "Manipulando seu banco de dados com mais velocidade!"
description: "Se você está enfrentando problemas de lentidão para inserir uma grande quantidade de informação e não sabe mais onde pode melhorar, certifique-se de utilizar BEGIN IMMEDIATE TRANSACTION, ou UNION"
tags: [sql,insert,begin immediate transaction,big data, union]
---

Se você está enfrentando problemas de lentidão para inserir(*) uma grande quantidade de informação e não sabe mais onde pode melhorar, certifique-se de estar fazendo da melhor maneira

<figure style="text-align: center;" >
	<a><img src="/images/posts/2016/10/slow.jpg" alt="Lentidão"></a>
</figure>  

<!-- more -->

##### (*) para outras operações pode ajudar também

## bd.execute
Para cada `bd.execute` é enviado uma instrução ao banco para `abrir`, `executar sua instrução sql` e `fechar`, exemplo:

{% highlight javascript %}
bd.execute -->
	Abrir banco -->
		execute o sql -->
	Fechar banco.
{% endhighlight %}

Até aqui tudo bem, agora imagine repetir essas instruções para 10, 500, 20000 vezes, você vai acabar se deparando com uma lentidão em seu aplicativo para processar tudo, exemplo:

{% highlight javascript %}
bd.execute -->
	Abrir banco -->
		execute o sql -->
	Fechar banco.

bd.execute -->
	Abrir banco -->
		execute o sql -->
	Fechar banco.

bd.execute -->
	Abrir banco -->
		execute o sql -->
	Fechar banco.
...
{% endhighlight %}

por isso vou lhe aprensentar duas opções de melhoria, o "BEGIN IMMEDIATE TRANSACTION" e o "UNION".

## BEGIN IMMEDIATE TRANSACTION

Você já verificou que abrir e fechar o banco para cada instrução sql pode deixar o seu aplicativo lento, e vamos otimizar isso, com `BEGIN IMMEDIATE TRANSACTION`, entenda como ele funciona :


{% highlight javascript %}
bd.execute -->
	Abrir banco (BEGIN IMMEDIATE TRANSACTION) -->
		execute o sql -->
		execute o sql -->
		execute o sql -->
		execute o sql -->
		execute o sql -->
		execute o sql -->
		...
	Fechar banco. (COMMIT TRANSACTION)
{% endhighlight %}

Com o `BEGIN IMMEDIATE TRANSACTION` você deixa uma conexão com o banco ativa enquanto executar multiplas instruções sqls, e isso lhe reduzirá drasticamente o tempo de execução dos seus sqls.

Porém como nem tudo é flores, verifiquei que existe um problema com mais de 400 linhas de instruções.Mas que podemos solucionar executando um comite a cada 400 linhas, sollução:

{% highlight javascript %}
var contador = 0;
bd.execute("BEGIN IMMEDIATE TRANSACTION");
for (var index=0; index < 20000; index++) {

	//** sua instrução sql aqui
	bd.execute("INSERT INTO minha_tabela (codigo) values ("+index+")");

	if (contador > 400){
		//** comita em um periodo de 400 instruções
		contador=0;
		bd.execute("BEGIN IMMEDIATE TRANSACTION");
		bd.execute("COMMIT TRANSACTION");
	}
	contador++;
}
bd.execute("COMMIT TRANSACTION");
{% endhighlight %}


## UNION
Esta semana encontrei um post bacana que acabei aprendendo sobre o union e suas vantagens, gostou de aprender sobre o `BEGIN IMMEDIATE TRANSACTION`, então vai gostar também de usar o `UNION` para seus inserts.

#### Não vou me aprofundar neste operador, pois acredito que existe muito material bom na internet para isso, e eu posso acabar deixando informação de fora, então vou comentar para que ele me ajudou!

O union monta uma "pré-estrutura" da tabela com os valores para o insert, você informa a tabela e os campos da tabela somente uma vez (podendo ser somente a tabela), e depois você passa todos os valores!

{% highlight javascript %}
INSERT INTO minha_tabela
SELECT "1", "test"
UNION
SELECT "2", "test"
{% endhighlight %}

Como o `BEGIN IMMEDIATE TRANSACTION` o `UNION` deve ter o maximo de 500 instruções para não ocorrer erros!, veja ele ná pratica:

{% highlight javascript %}
var novoSql = true;
var sql = '';
var count = 0;
for (var index=0; index<20000; index++) {
	//** monta cabeçalho do sql
	if (novoSql) {
		novoSql = false;
		sql = 'INSERT INTO minha_tabela (id, nome, descricao)';
	}else {
		sql += ' UNION';
	}

	//** adiciona os valores para inserir
	sql += ' SELECT "'+values[i][0]+'", "'+values[i][1]+'", "'+values[i][2]+'"';

	//** verifica quantidade de instruções maximas
	if (count > 499) {
		novoSql = true;
		count = 0;
		db.execute(sql);
	}
	count++;
}

//** executa ultima linha
if (count > 1) {
	db.execute(sql);
}
{% endhighlight %}

## Informações
Vejá o ganho de performance que podemos ter:

* Varios INSERTs : 2500ms
* Usando BEGIN e COMMIT : 90ms
* Usando SELECT e UNION : 40ms

(em um teste realizado, com as mesmas informações)

[select union referência](https://archive.appcelerator.com/question/104531/sqlite-multiple-insert)

[Documentação oficial para minipulação do bando de dados](http://docs.appcelerator.com/platform/latest/#!/guide/Working_with_a_SQLite_Database)
