<!--
---
title: 'Features modernas do Java que fazem toda diferença no código'
date: Mon, 22 Feb 2021 14:30:10 +0000
draft: false
tags: ['Iniciantes', 'Java']
---
-->

# Features modernas do Java que fazem toda diferença no código

Continuando nossa série de matérias sobre Java onde já falamos de bibliotecas e ferramentas que todo desenvolvedor que programa em Java deveria conhecer, vamos agora das novidades que vieram desde o Java 8 em 2014 e que trouxeram diversas features muito modernas para a linguagem que tornam o código muito mais sucinto, legível e moderno. Muitas vezes a dor relacionada a programar em Java está diretamente ligada ao fato de a maioria do material e das aplicações Java que encontramos por aí está escrita em Java 7 ou anterior e utiliza formas arcaicas, mais verbosas e por vezes complicadas de resolver problemas que poderiam ser simplesmente resolvidos por utilizar alguma dessas novas funções. Muitas dessas novidades vieram por influência de outras linguagens, como as Lambda Functions, Streams e Inferência de Tipos que já era bastante comum em outras linguagens de programação como C++, Optionals e Records que vieram diretamente da influência que Kotlin teve para modernizar Java.

### **#1 - Lambda Functions**

A partir do Java 8 ou posterior temos acesso a funções lambda também conhecidas como funções anônimas ou arrow functions que nada mais são que uma forma simples de função que nos ajudam a diminuir o código necessário para escrever funções simples ou callbacks e são úteis em muitas situações e contexto, sendo uma feature moderna que precisa ser dominada pelo programador Java para que possam escrever códigos mais claros e menos verbosos. O exemplo abaixo mostra como criar uma nova Thread que executa um código para imprimir na tela mensagens usando println(). Como podemos  ver conseguimos reduzir muita verbosidade sabendo onde e como usar lambda functions.

```java
public class LambdaExample {
   public static void main(String ...args) {
   // Runnable r1 é como fariamos em Java 7<   
   new Thread(new Runnable() { 
            @Override
            public void run() {
                System.out.println("Java 7");
            }
        }
   ).run();

  // A mesma coisa usando Lambda do Java 8>
   new Thread( () -> System.out.println("Hello Lambda Functions") )
      .run();
 }
}
```
**Para saber mais sobre**:

* [Caelum - Java 8 Lambda e Methods Reference?](https://blog.caelum.com.br/java-8-lambda-ou-method-reference-entenda-a-diferenca/amp/)
* [Como usar funções lambda em Java](https://www.devmedia.com.br/como-usar-funcoes-lambda-em-java/32826)

### **#2 - Streams**

Streams é a uma **API** (**A**pplication **P**rogramming **I**nterface, uma coleção de funções assim como java.io ou java.math) que está disponível na instalação padrão do Java em qualquer versão acima do 8. Se tratando de uma API ela contêm muitas funcionalidades, entre elas a possibilidade de usar **map**, **filter** e **reduce** e outras operações importantes sobre lista. Streams ajudam a trabalhar de uma forma mais declarativa com listas, isso é dizendo o resultado que esparamos ao invés de como a operação tem que ser feita, o que nos ajuda a escrever um código mais claro, menos verboso.

```java
public class StreamExample {
   public static void main(String ...args) {
      // cria uma nova lista (coleção) da interface List
      List<String> myList =
      Arrays.asList("a1", "a2", "b1", "c2", "c1");
      
      // aplica os streams
      myList
            .stream()                       // inicia o stream
            .filter(s -> s.startsWith("c")) // filtra os items que começam com c 
            .map(String::toUpperCase)       // aplica a função toUpperCase em cada item
            .sorted()                       // coloca em ordem alfabética
            .forEach(System.out::println);  // imprime
  }
}
```

Imprime:
```
C1
C2
```
**Para saber mais sobre**:

* [Oracle - Iniciando o desenvolvimento com a Streams API](https://www.oracle.com/br/technical-resources/articles/java-stream-api.html)
* [Streams no Java 8 e no Java 9](https://medium.com/@racc.costa/streams-no-java-8-e-no-java-9-36177c5c3313)

### **#3 - Optionals**

Todas as versões de Java anteriores a 8 ficaram bastante conhecidas pelo erro NullPointerException que basicamente ocorria quando se tentava acessar uma referência ou valor nulo, isso se dá porque essas versões tinham inúmeros problemas para lidar com valores nulos e em Java 8 e posteriores temos a Classe Optionals que veio para resolver esses problemas. Quando trabalhamos com Optionals estamos fazendo com que valores que podem ser nulos retornem algum valor o que evita excessões e erros causados por valores nulos resolvendo a maioria se não todos os erros e problemas causados por esse tipo de problema no seu projeto. Basicamente o que a Classe Optional faz é te dar um grande número de funções para trabalhar e tratar dados nulos, passando um valor string vazio que vem da própria classe caso o valor da referência na memória seja nulo ou um valor da classe passada por seu paramêtro de [Generics](http://www.mauda.com.br/?p=468) para a função seguinte.

```java
public class OptionalsExample {
   public static void main(String ...args) {
       // Cria um novo objeto Address (Endereço)
       Address enderecoJoao = new Address("Rua Dr. Casa Grande, N5",
                                   "Bento Gonçalves", "Brasil", "95707-089");
       
       // cria uma pessoa joao passando um Optional de Endereço
       Person joao = new Person("João",Optional.of(enderecoJoao), "643.563.600-10");
       
       // cria mais duas pessoas passando um Optional sem valor
       Person maria = new Person("Maria", Optional.empty(), "");
       Person carlos = new Person("Carlos", Optional.empty(), "132.134.720-00");
       
       // cria uma coleção de pessoas
       List<Person> pessoas = new ArrayList<>();
       // add as pessoas criadas a coleção
       people.add(joao);
       people.add(maria);
       people.add(carlos);
       
       // itera a coleção usando stream e para cada pessoa p
       // imprime "{nome} de {endereço}" e caso não tenha endereço vazio
        people.stream().forEach((p) -> {
            System.out.printf("%s do Endereco %s %n",
                       p.nome(),
            p.address().orElse(Address.EMPTY_ADDRESS));
        });
    }
}
```

Saída:
```
João do Addrress{line=Rua Dr. Casa Grande, N5, city=Bento Gonçalves, country=Brasil, zipcode=95707-089}
Maria do Address{line1=, city=, country=, zipcode=0}
Carlos do Address{line1=, city=, country=, zipcode=0}

```
**Para saber mais sobre**:

* [Optional no Java 8 e no Java 9](https://medium.com/@racc.costa/optional-no-java-8-e-no-java-9-7c52c4b797f1)
* [Chega de NullPointerException! ](https://blog.algaworks.com/chega-de-nullpointerexception/)

### **#4 - Inferência de Tipos (var)**

Essa é uma feature que parece simples mas tornou o código Java muito mais simples de escrever e agradou a muitos programadores, trata-se da inferência de tipos que é um tipo especial de variável que faz com que o commpilador insira o tipo da váriavel para nós em tempo de compilação! Ou seja em Java 10 ou superior o que antes escreviamos assim:

```java
ArrayList<String> palavras = new ArrayList<String>();
```

Agora pode ser escrito assim:

```java
var palavras = new ArrayList<String>()
```

E isso funciona para qualquer tipo nativo ou objeto do Java e em qualquer **variável local**. Além de var também temos a palavra reservada **val** que define o valor como imutável caso desejamos criar uma constante ou trabalhar com valores que não podem ser mudados. 

**Para saber mais sobre**:

* [Primeiro contato com “var” no Java 10](https://medium.com/collabcode/primeiro-contato-com-var-no-java-10-ac9ff5baaf17)
* [Explore o novo tipo "var" do Java 10](https://www.infoq.com/br/articles/java-10-var-type/)

### **#5 - Records**

Talvez você nunca tenha tido que criar DAO (Data Access Object) ou POJO (Plain Old Java Objects), mas todos que já tiveram que criar classes para a representação de dados em seus programas Java sabe o quão verboso é criar essas classes, mas a partir do Java 14 é possível reduzir em até 95% o código necessário para criar essas classes apenas declarando a classe como uma Record Class. O que antes precisava ser escrito assim:

```java
public class Person {

    private final String name;
    private final String address;

    public Person(String name, String address) {
        this.name = name;
        this.address = address;
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, address);
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) {
            return true;
        } else if (!(obj instanceof Person)) {
            return false;
        } else {
            Person other = (Person) obj;
            return Objects.equals(name, other.name)
              && Objects.equals(address, other.address);
        }
    }

    @Override
    public String toString() {
        return "Person \[name=" + name + ", address=" + address + "\]";
    }

    // e precisamos escrever mais os getters e setters
}
```

Agora podem ser escritos assim utilizando Records:

```java
public Person(String name, String address) {
    this.name = name;
    this.address = address;
}
```

e essa classe ainda recebe os métodos getter e setter sem precisarmos escrevê-los! Muito bacana, não? Com isso reduzimos muito o código necessário para realizar abstração de dados e se torna muito mais rápido e produtivo desenvolver com Java que continua evoluindo e cada vez mais trazendo novidades fantásticas como essa. 

**Para saber mais sobre**:

* [Records no Java 14](https://www.infoq.com/br/articles/records-no-java-14/)
* [(vídeo) O que são Records, a preview feature do Java 14?](https://www.youtube.com/watch?v=eg9L9UJwQGM)

Esse foi o último post da série de posts sobre Java Moderno em que também falei sobre [ferramentas modernas](https://daads.com.br/site/2020/04/ferramentas-programador-java/) e [bibliotecas que ajudam em um código moderno](https://daads.com.br/site/2020/05/bibliotecas-java-moderno/), espero que tenham gostado dessa série e que tenha sido de algum proveito para alguém que ficou com alguma mágoa de Java após as cadeiras de Programação Orientada a Objetos devido a dificuldades com as versões e ferramentas antigas e/ou a falta do uso de bibliotecas para auxiliar na programação ou que está cursando essa matéria atualmente e talvez possa usar algo dessa série para resolver seus problemas! Muito obrigado a todos que acompanharam!
