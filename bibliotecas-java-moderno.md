<!--
---
title: 'Bibliotecas Java que devemos conhecer para um código moderno 🚀'
date: Mon, 04 May 2020 21:30:14 +0000
draft: false
tags: ['Apache Commons', 'Banco de Dados', 'bibliotecas', 'collections', 'GNU', 'Google Guava', 'GSON', 'Iniciantes', 'Jackson', 'Java', 'Java', 'jooq', 'JSON', 'Lombok', 'Trove']
---
-->

<p align="center">
  <a href="#" target="_blank">
    <img src="./img/header_bibliotecas.jpg">
  </a>
</p>

# Bibliotecas Java que devemos conhecer para um código moderno 🚀

No [último post](http://daads.com.br/site/2020/03/ferramentas-que-todo-programador-java-deveria-conhecer/) prometi continuar abordando sobre como podemos trabalhar com Java de forma mais efetiva e usando ferramentas e bibliotecas modernas para ter um código mais fácil e produtivo utilizando esta tecnologia. Começar pelas ferramentas foi proposital já que muitas delas como o Maven e o IntelijIDEA ajudam à trabalhar com bibliotecas que é o assunto deste post. Ao longo dos anos já ouvi muitas reclamações sobre a dor de escrever códigos em Java, desde pessoas que acham a linguagem demasiadamente verbosa até pessoas que tiveram dificuldades com certas features da linguagem como trabalhar com datas, mas a verdade é que esse não é um problema exclusivo dessas pessoas, muitos programadores já passaram pelos mesmos problemas e muitas bibliotecas foram criadas para tentar resolver esses problemas sendo que muitas delas são utilizadas na maioria dos projetos comerciais justamente para evitar essas dores e aumentar a produtividade. Java possui uma grande comunidade e isso deve-se ao fato da grande aderência que a linguagem tem com grandes empresas de TI. Grandes projetos Open Source como o Projeto Apache e grandes empresas como o Google tem milhares de programadores trabalhando com a linguagem e publicam muitas bibliotecas que eles mesmo criaram para tornar Java uma linguagem mais moderna. Além de bibliotecas esses grandes projetos que utilizam a linguagem também contribuem com documentação, palestras, projetos e vale muito a pena seguir o que elas andam fazendo. Algumas bibliotecas terão mais de uma opção, mas isso deve-se ao fato de que existe mais de uma opção para resolver o mesmo problema e ambas são populares sendo que a escolha depende muito da preferência de cada programador.

### #1 Lombok

Essa biblioteca foi utilizada no [último post](http://daads.com.br/site/2020/03/ferramentas-que-todo-programador-java-deveria-conhecer/) para demonstrar um pouco do Maven e sem dúvidas é a mais importante da lista. O [Lombok](https://projectlombok.org/) é uma biblioteca que utiliza notations para reduzir a quantidade de código repetitivo em Java, ela é utilizada para gerar automaticamente construtores, getters, setters, hashcode... tudo o que precisamos escrever de forma repetitiva. Isso ajuda não somente a escrever um código Orientado à Objetos de qualidade com muito menos código, mas também facilita muito - muito mesmo - para quem precisa escrever POJO/Beans para projetos Web. Alguns exemplos retirados da documentação do projeto: 

**Com Lombok:**
```java
import lombok.AccessLevel;
import lombok.Getter;
import lombok.Setter;

public class GetterSetterExample {

  @Getter @Setter private int age = 10;
  
  @Setter(AccessLevel.PROTECTED) private String name;
  
  @Override public String toString() {
    return String.format("%s (age: %d)", name, age);
  }
}
```

**Sem Lombok:**
```java
public class GetterSetterExample {

  private int age = 10;

  private String name;
  
  @Override public String toString() {
    return String.format("%s (age: %d)", name, age);
  }
  
  public int getAge() {
    return age;
  }
  
  public void setAge(int age) {
    this.age = age;
  }
  
  protected void setName(String name) {
    this.name = name;
  }
}
```
Olhando assim pode até parecer simples, mas existem certos projetos que utilizar annotations ao invés de escrever os métodos pode reduzir em até 70% o código das classes, tornando o código muito mais organizado e legível, além de aumentar em muito a produtividade já que o programador perde menos tempo implementando códigos repetitivos e mais resolvendo o problema proposto em si. 

**Sugestão de vídeo**: [Lombok | Wende Mendes | Papo Reto | T3E71 | BlueSoft Labs](https://youtu.be/ANqkqAqgUqA?t=19)

### #2 Google Guava ou Apache Commons

Aqui teremos duas opções que são concorrentes e muito populares. Na verdade não se tratam de bibliotecas em si, mas sim uma coleção de bibliotecas que resolvem problemas recorrentes que os programadores Java enfrentam, gosto muito da analogia que vi em uma palestra de um Eng. da Google no Youtube falando sobre o Guava de que: "Se os programadores Java fossem o Batman, essa coleção de bibliotecas seria o cinto de utilidades." O mesmo aplica-se ao Apache Commons. A principal diferença que tem divido ambas as coleções de bibliotecas é filosófica: enquanto o Guava apesar de ser Open Source não aceita contribuições externas - de pessoas fora do Google - o Apacahe Commons é um projeto comunitário. Entre as inúmeras bibliotecas que essas coleções possuem existem podemos dar exemplos como:

*   facilitar o uso de Banco de Dados com DbUtils (Commons)
*   trabalhar de forma simples e rápida com arquivos CSV utilizando Commons CSV (Commons)
*   facilitar a manipulação de Objetos como Date com Commons Lang3 (Commons)
*   fazer regex de texto de forma simples com CharMatcher (Guava)
*   criar inteiros sem sinal com UnsignedInts (Guava)
*   fazer operações matemáticas com precisão utilinado Math Utilities (Guava)

Quando estiver em um aperto e achar que esse problema não é só seu e que alguém pode ter resolvido isso antes vale a pena dar uma olhada se já não existe alguma biblioteca nessas coleções que resolvem esse problema. Para saber tudo sobre as coleções que o Guava possui e ver a documentação de cada biblioteca basta acessar a [Guava Wiki](https://github.com/google/guava/wiki) e para o mesmo com o Apache Commons basta acessar a [página do projeto](https://commons.apache.org/).

### #3 GSON ou Jackson

Não importa em que área do desenvolvimento você irá trabalhar, certamente irá precisar trabalhar com JSON. Isso vai desde comunicar com uma API externa até compartilhar informações do back-end com o front em Javascript. Para isso temos excelentes bibliotecas em Java que fazer a **serialização** de Objetos para JSON e vice-versa. Isso significa que tanto a GSON (do Google) quanto a Jackson (projeto comunitário) são capazes de convertes Objetos Java em strings JSON automaticamente, utilizando a Classe User do nosso [último projeto](http://daads.com.br/site/2020/03/ferramentas-que-todo-programador-java-deveria-conhecer/) poderíamos utilizar a biblioteca GSON da seguinte forma:

```java
package br.com.daads.gson;

import com.google.gson.Gson;

public class App 
{
    public static void main( String[] args )
    {
  	User professor = new User("Mary", "Keller", "may.keller@gmail.com", "F");
  	Gson gson = new Gson();
  		
        String json = gson.toJson(professor);
  		
        System.out.println( json );
    }
}
```

E isso iria imprimir:
```json
{"firstName":"Mary","lastName":"Keller","email":"may.keller@gmail.com","gender":"F"}
```
Da mesma forma poderíamos transformar uma String JSON de um arquivo ou API em um objeto (os backslashes '\\' são para escapar as aspas):

```java
package br.com.daads.gson;

import com.google.gson.Gson;

public class App 
{
    public static void main( String[] args )
    {
  	Gson gson = new Gson();
  		
  	String stringJson = "{\"firstName\":\"Carol\",\"lastName\":\"Shaw\",\"email\":\"carol.shaw@gmail.com\",\"gender\":\"F\"}";
  	User programadora = gson.fromJson(stringJson, User.class);
  		
        System.out.println("A criadora de Pitfall foi " + programadora.getFirstName() + " " +  programadora.getLastName());
    }
}
```

E isso iria imprimir:
```
A criadora de Pitfall foi Carol Shaw
```
Tanto GSON quanto Jackson são usadas em grandes projetos, porém a biblioteca Jackson é mais conhecida por ser o padrão dos de dois grandes frameworks Java, o Dropwizard e o Spring Boot. Já a biblioteca GSON além de ser mantida e usada pelo Google também é o padrão do framework GWT. Ambas bibliotecas são excelentes escolhas, aprenda uma, os exemplos acima usam GSON porque ela é mais simples de entender e explicar, enquanto a Jackson é extremamente baseada em configurações e annotations que tornam seu entendimento um pouco mais complexo. 

**Sugestão de vídeo**: [Converter JSON para objetos ou Listas usando java | Welton Silva](https://youtu.be/XxTAX3QEGrQ)

### #4 GNU Trove (ou outra biblioteca de coleções)

Então, aqui elegemos uma biblioteca entre várias que tem o mesmo objetivo não por sua popularidade,  mas pela sua eficiência. Java possui nativamente uma excelente biblioteca de coleções - ArrayList, LinkedList, HashMap... - que estudamos e aprendemos na disciplina de Orientação à Objetos II, porém ao longo dos anos muitos desenvolvedores e empresas tentaram recriar essa biblioteca adicionando coleções que não estão presentes ou tentando otimizar as coleções que existem. Entre essas bibliotecas temos:

*   [Eclipse Collections](https://www.eclipse.org/collections/) da Eclipse Foundation
*   [Commons Collections](https://commons.apache.org/proper/commons-collections/) da Apache Foundation
*   [Collections Utilities](https://github.com/google/guava/wiki/CollectionUtilitiesExplained) da Google

Essas bibliotecas não só desenvolveram-se ao longo dos anos como também uniram-se à outros projetos de grandes empresas com os mesmos objetivos como no caso da financeira Goldman Sachs que tinha a GS Collections que se uniu à Eclipse Collections e a Google Collections que uniu-se à Collection Utilities passando à fazer parte do projeto Guava. Porém, entre todas as opções a que ficou conhecida por ter o melhor desempenho foi a [Trove](http://trove4j.sourceforge.net/html/overview.html) que é um dos projetos do grupo de Free Software [GNU](https://www.gnu.org/). Apesar da Trove possuir as mesmas estruturas da biblioteca padrão de coleções do Java ela consegue executar as mesmas operações consumindo menos memória e de forma muito mais rápida que a bilioteca padrão da linguagem, para ver um pouco desse poder na página do projeto tem [benchmarks](http://trove4j.sourceforge.net/html/benchmarks.shtml) que mostram a eficiência da biblioteca processando grandes volumes de dados. 

**Exemplo usando Trove**:

```java
package br.com.daads.trove;

import gnu.trove.iterator.TLongIterator;
import gnu.trove.set.hash.TLongHashSet;

public class App {

	public static void main(String[] args) {
		long startTime = System.currentTimeMillis();
		final TLongHashSet longs = new TLongHashSet();  
		for(int i=0; i < 1000000; i++) {
			longs.add(i);
		} 
	    TLongIterator longIterator = longs.iterator();  
	    while (longIterator.hasNext())  
	    {  
	    	final long longValue = longIterator.next();  
	    	System.out.println(longValue);  
	    }
	    long endTime = System.currentTimeMillis();
	    System.out.println("O tempo total de execução foi: " + (endTime-startTime) + "ms"); 
	}

}
```

O resultado será:

```
O tempo total de execução foi: 4763ms
```

Apesar de ser algo que possa parecer simples utilizar uma biblioteca de coleção - à sua escolha - pode melhorar a execução de um código que possua grande volume de dados ou adicionar possibilidades novas às estruturas de dados da linguagem, por isso é importante que o programador Java conheça e estude as mais diversas bibliotecas de coleções para conhecer qual poderá ser uma escolha interessante para projeto que está trabalhando.

### #5. jOOQ

Alguns de nós já utilizaram JPQL ou HQL em algumas disciplinas que nada mais são do bibliotecas que facilitam a operação de SQL através de uma sintaxe mais próxima da linguagem SQL que usamos no Banco de Dados. Porém nada disso chega perto da facilidade e eficiência que a biblioteca [jOOQ](https://www.jooq.org/) - jOOQ Object Oriented Querying - traz. Essa biblioteca uma vez que conectada com o Banco de Dados cria as tabelas que o banco possui como objetos e os armazena em um pacote dentro do projeto assim permitindo que eles sejam usados em conjunto com os métodos da biblioteca que fornecem uma experiência idêntica a estar trabalhando com o idioma SQL dentro do projeto Java. 

**Exemplo usando jOOQ**:
```java
import org.jooq.generated.Tables;

import java.sql.Connection;
import java.sql.SQLException;

import static java.sql.DriverManager.getConnection;
import static org.jooq.generated.Tables.*;
import static org.jooq.impl.DSL.using;

public class JooqDemo {
  public static void main(String[] args) {
    try (Connection c = getConnection("jdbc:mysql://localhost:3306", "root", "dijkstra")) {
      using(c)
          .select(ACTOR.FIRST_NAME, ACTOR.LAST_NAME, FILM.TITLE)
          .from(ACTOR)
          .join(Tables.FILM_ACTOR).on(FILM_ACTOR.ACTOR_ID.equal(ACTOR.ACTOR_ID))
          .join(Tables.FILM).on(FILM.FILM_ID.equal(FILM_ACTOR.FILM_ID))
          .where()
          .fetch()
      .stream()
          .forEach(System.out::println);
    } catch (SQLException sqlException) {
      //TODO

    }
  }
}
```

Essa biblioteca tornou-se tão popular que hoje a versão paga é utilizada por grandes companhias que usam Java. A versão gratuita permite a conexão com qualquer banco de dados que seja Open Source como MySQL e Postgres, enquanto a paga dá suporte à bancos pagos como Oracle e SQL Server. Além disso o jOOQ une-se à vantagens do Java como a possibilidade de checar erros de tipo na Query em tempo de compilação e permite escrever com a sintaxe de qualquer banco suportado - incluindo as particularidades de cada um.
