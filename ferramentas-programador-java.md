<!--
---
title: 'Ferramentas que todo programador Java deveria conhecer! 🛠️'
date: Mon, 20 Apr 2020 21:30:44 +0000
draft: false
tags: ['Ferramentas', 'Iniciantes', 'InteliJ', 'Java', 'Java', 'JetBrains', 'Lombok', 'Maven', 'sdkman', 'UML', 'VS Code']
---
-->

<p align="center">
  <a href="#" target="_blank">
    <img src="./img/header_note.jpg">
  </a>
</p>

# Ferramentas que todo programador Java deveria conhecer! 🛠️

Java é uma linguagem de programação que possui muita história e legado. Este ano a Linguagem completou os seus 25 anos de existência e em no mínimo 18 anos dessa história ela foi a linguagem de programação mais popular do mundo segundo o índice Tiobe \[[1](#link1)\]. Muito dessa popularidade deve-se a ser uma linguagem que trouxe a promessa de tornar a vida dos programadores mais fácil e produtiva através da Orientação a Objetos nos anos 2000 e a aderência do mercado corporativo a ela nos anos que se seguiram. Hoje muitos serviços modernos utilizam Java como linguagem principal de Back-end como Netflix \[[2](#link2)\], Uber \[[3](#link3)\] e Hotel? (Trivago \[[4](#link4)\]). Muito do que Java é conhecido é como uma linguagem velha, verbosa e difícil de usar e isso deve-se muito a não estarmos habituados a estudar práticas modernas de desenvolvimento em Java. Para que possamos explorar todo o poder da linguagem é necessário conhecer 3 coisas muito importantes - features recentes, ferramentas modernas e bibliotecas novas - vamos abordar cada um destes itens em posts futuros, mas por hoje vamos começar pelo que o Java mais se destaca: as ferramentas - _tooling_. Talvez esse seja o item que o Java mais é conhecido e admirado entre todas as linguagens, as melhores ferramentas de programação são desenvolvidas em Java e a linguagem possui ferramentas excelentes de desenvolvimento. Aqui vamos falar sobre apenas algumas e mais essenciais, mas se deseja tornar-se um programador Java em grandes empresas locais ou exteriores, recomendamos fortemente que se mantenha atento as novidades.

### #1 sdkman

Essa é uma ferramenta essencial para a caixa de ferramentas do programador Java. O [sdkman](https://sdkman.io/) é responsável por gerenciar as versões de Java instaladas no seu computador sem a necessidade de sujar o sistema com várias instalações diferentes e configurar um monte de variáveis de ambiente. Muitos não sabem disso, mas Java além de múltiplas versões (hoje as em uso são 8 e 11) também possui múltiplas distribuições. Como assim? Então, Java é muito conhecido pela sua associação com a Oracle - empresa que comprou a empresa que originalmente desenvolveu a linguagem a Sun Microsystems. Só que a versão do JDK da Oracle não é mais gratuita para projetos comerciais a partir da versão 11 \[[5](#link5)\]. A própria Oracle tem uma versão Open Source conhecida como Oracle Open JDK. Nos últimos anos, inúmeras fabricantes desenvolveram suas próprias JVM e JDKs entre elas Amazon ([Coretto](https://aws.amazon.com/corretto)), Azul ([Zulu](https://www.azul.com/downloads/zulu/)), SAP ([SAPMachine](https://sap.github.io/SapMachine)), IBM ([IBM sdk](https://www.ibm.com/developerworks/java/jdk)) e Red Hat ([Open JDK](https://developers.redhat.com/products/openjdk/overview)). Para quem quiser saber mais sobre essa questão e conhecer o licenciamento de cada versão do Java recomendo ir até o site [Adopt Open JDK](https://adoptopenjdk.net/). Agora imagine que você trabalha em uma empresa que use e dependa da versão 8 do Java da Oracle para rodar - como muitas aqui da Serra -, mas você goste de usar a versão LTS mais moderna - atualmente, a 11 - da Red Hat para desenvolver os trabalhos da faculdade. Como resolver isso? Instala ambas? Como configurar as variáveis de ambiente JAVA\_HOME pra ambas? Ai que entra o brilho do sdkman, com ele você pode usar os comandos para gerenciar a vesão e JDK instalada:

```bash
$ curl -s "https://get.sdkman.io" | bash # instala a ferramenta no Linux ou MAC

$ sdk install java 8.0.242-open # instala a versão 8 da Oracle Open JDK

$ java -version # retorna openjdk version "1.8.0_242"

$ sdk install java 11.0.6.j9-adpt # instala a versão 11 do Adopt Open JDK com a VM j9 do Proj. Eclipse. dar 'Y' no final.

java -version # retorna openjdk version "11.0.6" 2020-01-14 Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.18.0...

$ sdk list java # lista todas jdk instaladas

$ sdk use java 8.0.242-open # ativa Java 8

$ sdk use java 11.0.6.j9-adpt # ativa Java 11
```

Hoje em dia muitos programadores optam por usar Docker para resolver esse problema possuindo uma imagem de máquina para cada ambiente - trabalho e faculdade -, mas certamente o sdkman é uma ferramenta simples que oferece muitas vantagens para quem trabalha com Java. Seu defeito é não possuir uma versão para Windows, apenas para Linux e MAC, para quem usa Windows o melhor caminho talvez seja o mais complexo e bom Docker com a imagem do [Alpine Linux da OpenJDK](https://hub.docker.com/_/openjdk).

### #2 Maven (ou Gradle)

O [Maven](http://maven.apache.org/) é um gerenciador de projetos - ele trabalha como gerenciador de execução, compilação, scripts e dependências - para Java. É uma ferramenta essencial e indispensável para todo o desenvolvedor que deseja trabalhar com Java e requisito na maioria das vagas - até mesmo para Júnior. O Maven é utilizado para instalar bibliotecas de forma automatizada, criar projetos Java de forma estruturada, criar scripts de execução - ex: rodar os testes antes de executar a main - e compilar e executar o código do projeto (seria como o npm é para Javascript). O Maven surgiu como um projeto da Fundação de Software Apache que tem como objetivo suportar projetos Open Source e tem uma grande história de contribuições para o desenvolvimento do Java. Outra ferramenta que surgiu como um projeto independente foi o [Gradle](https://www.gradle.org/), com o objetivo de ser um Maven mais moderno, sua principal diferença está no uso de linguagens de script modernas como Groovy e Kotlin para gerenciar as dependências e scripts do projeto em contraste ao Maven que usa a  linguagem de marcação XML, assim permitindo muito mais flexibilidade e poder no gerenciamento de projetos. Apesar de Groovy ser uma ferramenta mais nova e com mais funcionalidades ela teve baixa adesão ao mercado que já estava acostumado a utilizar Maven para essa tarefa e teve algum crescimento após a Google torná-la a ferramenta oficial para o desenvolvimento de apps para Android. Para tornar tudo mais simples, vamos recomendar - pelo menos em primeiro momento - e nos ater no Maven, que é uma ferramenta simples, eficiente e dominante no mercado para explicar a importância de um gerenciador de projetos. Para instalar o Maven podemos utilizar o sdkman - para quem usa Linux e MAC -, para quem usa Windows será necessário entrar no site, ir em 'Downloads' e baixar o arquivo .exe. Para instalar e iniciar um projeto:

```bash
$ sdk install maven # instala o maven pelo sdkman

$ mvn archetype:generate -DgroupId=br.com.daads -DartifactId=tutorial-maven -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
# a linha acima inicia um projeto Java novo chamado 'Tutorial Maven'
```

Pronto! Agora temos nosso projeto 'tutorial-maven' criado, mas o que é esse monte de parâmetros?

* archetype:generate diz que queremos criar um  novo projeto Maven
* \-DgroupId é a identificação do desenvolvedor, empresa ou grupo que está criando e/ou mantendo o projeto por convenção deve ser o site do mesmo ao contrário como colocamos o do daads ali
* \-DartifactId é o nome do projeto no caso 'tutorial-maven', por padrão o nome deve ser todo em minúsculas, sem acentos e com hífens como espaços
* \-DarchetypeArtifactId é o 'modelo' de projeto que estamos tentando criar, existem modelos para projetos Web, projetos Java SE, Java EE ou seja define para qual plataforma ou tipo de projeto estamos criando este programa.
* \-DarchetypeVersion é a versão do 'modelo' que estamos usando.
* \-DinteractiveMode é para usar os valores padrão das demais configurações ao invés de perguntar-nos

Após executarmos esse comando veremos que foi criada uma pasta 'tutorial-maven' que pode ser importada como um 'Projeto Maven' para qualquer IDE de preferência - a maioria hoje tem ferramentas modernas para gerenciar projetos Maven. Dentro desta pasta teremos um arquivo '**pom.xml**' - donde vamos colocar todas nossas configurações e dependências do projeto e o próprio Maven irá gerenciar para nós essas coisas - e a pasta '**src**' que é onde ficará nosso código e nossos testes. Agora para instalarmos uma biblioteca como a Lombok basta procurarmos no [repositório maven](http://search.maven.org) e pegar a configuração XML do pacote que queremos, e colarmos dentro de do arquivo pom.xml, no caso:

```xml
 <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
    <dependency>
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok</artifactId>
      <version>1.18.12</version>
      <scope>provided</scope>
    </dependency>
  </dependencies>

```

Note que além de colocar a dependência como estava nos repositórios, também adicionamos a tag **scope** que compila a biblioteca junto ao projeto. Agora vamos navegar no nosso código fonte dentro da pasta **src**, podemos perceber que uma série de outras pastas foram criadas e isso é feito para organizar os pacotes do nosso projeto, se navegarmos até **src/main/java/br/com/daads** vamos agora criar uma classe User que irá usar nossa biblioteca e alterar o método main dentro de App para mostrar as informações: 

**User.java**
```java
package br.com.daads.tutorial;

import lombok.AccessLevel;
import lombok.Getter;
import lombok.Setter;

@Getter @Setter 
public class User {
    private Long id; 
    private String firstName;
    private String lastName;
    private String email;
    private String gender;
 
    public User(String firstName, String lastName, String email, String gender) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.email = email;
        this.gender = gender;
    }
 } 
```

**App.java**
```java
package br.com.daads.tutorial;

public class App 
{
    public static void main( String[] args )
    {
        // String firstName, String lastName, String email, String gender)
        User aluno = new User("Oscar", "Neirinhos", "oscar.neirinhos@gmail.com", "M");
        System.out.println( "O aluno " + aluno.getFirstName() + " " + aluno.getLastName() + " tem o email " + aluno.getEmail() );
    }
}
```

Pronto, agora precisamos compilar e executar nosso projeto. Para isso devemos ter um terminal aberto na pasta raiz do projeto e então digitar os comandos:

```bash
$ mvn package # compila

$ java -cp target/tutorial-maven-1.0-SNAPSHOT.jar br.com.daads.App # executa, imprime: O aluno Oscar Neirinhos tem o email oscar.neirinhos@gmail.com
```

Percebeu que invocamos métodos getter da Classe sem declararmos e eles funcionaram? Isso é justamente o que a biblioteca Lombok faz - e falaremos dela em um post mais para frente. Tudo isso parece muito complicado, mas fique tranquilo, é mais simples do que parece. IDEs como o Eclipse ou InteliJ IDEA abstraem todo esse trabalho que fizemos no terminal em botões e menus que são bem mais simples de usar. Aprenda Maven - ou Gradle - e use em seus projetos. Maven é uma ferramenta que é base para qualquer projeto Java e requisito para qualquer emprego com a linguagem. 

**Sugestão de vídeo** (_tutorial para usar o Maven com o Eclipse)_**:** [Começando com Apache Maven em projetos Java](https://www.youtube.com/watch?v=2K_DhuDK5BA)

### #3 IntelijIDEA

Quando estamos falando de Java costumamos lembrar logo das IDEs clássicas: NetBeans - da Oracle - e Eclipse - da Eclipse Foundation - e de fato são excelentes ferramentas com inúmeros plugins e suporte a muitas linguagens. Com o tempo surgiu novas alternativas muito interessantes para o desenvolvimento em Java que possuem features modernas _out of the box_ e grandes melhorias se comparado com as IDEs clássicas. O melhor exemplo do poder de uma IDE moderna é a IDE [IntelijIDEA](https://www.jetbrains.com/idea/) da JetBrains que promete ter forma mais ergonômica - melhores atalhos, disposições de tela... -, mais inteligente - melhor autocomplete, melhor análise de código... -, adaptável - com suporte a diversos frameworks e linguagens da JVM - e com excelentes plugins de integração com outras ferramentas - como Docker e GitHub. A empresa que produz a IDE, a JetBrains é conhecida por produzir diversas IDEs excelentes pagas para as mais diversas linguagens e todas elas são baseadas em seu principal produto: o IntelijIDEA. Hoje o Intelij tem três versões: education, community e professional. A versão community é open source e gratuita, voltada para quem quer usar as principais funções do programa, a versão education é gratuita e voltada para professores e alunos, ela nada mais é que a versão gratuita do IntelijIDEA com vários tutoriais inclusos e ferramentas para sala de aula e a versão professional é a versão paga que oferece features extras e suporte para frameworks web. No mundo profissional o ideal é que o desenvolvedor page pela licença da versão professional e tenha todo o poder da IDE para trabalhar com os frameworks que a empresa usa. Porém, para estudantes que apenas irão usar Java SE - como nas disciplinas de Orientação a Objetos - a versão community gratuita é mais que suficiente e oferece excelentes features e plugins. A JetBrains também oferece a IDE professional gratuitamente a estudantes matriculados em Universidades de Ensino Superior pelo tempo em que conseguirem comprovar a matrícula.

### #4 Visual Studio Code Installer for Java

Muitas vezes ouvi dos colegas: "Gosto mesmo de usar o Visual Studio Code, mas tenho que ter o NetBeans só para usar Java". Em junho de 2019 a Microsoft anunciou uma novidade: **um instalador do VS Code com o ambiente Java configurado _out of the box_**. Para acessar o download deste instalador basta acessar [esse](https://devblogs.microsoft.com/java/announcing-visual-studio-code-java-installer/) link. Esse instalador baixa e instala o VS Code, a JDK da versão LTS do Java e os plugins necessários para desenvolver no VS Code e também os configura não sendo necessário nenhum procedimento a mais. Esse instalador atualmente apenas está disponível para Windows e a Microsoft já anunciou que irá lançar também para MAC, para quem usa Linux é necessário instalar a parte tanto o JDK quanto o VS Code e depois instalar as seguintes extensões para obter o mesmo resultado:

* [Debugger for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-debug) da Microsoft
* [Java Dependency Viewer](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-dependency) da Microsoft
* [Java Extension Pack](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack) da Microsoft
* [Java Test Runner](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-test) da Microsoft
* [Maven for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-maven) da Microsoft
* [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode) da Microsoft
* [Language Support for Java(TM)](https://marketplace.visualstudio.com/items?itemName=redhat.java) da Red Hat

Após instalar tudo o que é necessário, seja através do instalador oficial, ou cada componente individualmente tudo estará pronto e funcionando para trabalhar com Java no Visual Studio Code. Agora o VS Code é capaz de autocompletar, compilar, executar, debugar e todas as demais necessidades de qualquer programador Java. Caso queira testar, após a instalação digite ctrl+shift+p para abrir a paleta de comandos do VS Code e digite "Java:", haverá muitas opções, uma delas será "Java: Create Java Project" que irá criar um novo projeto dentro da pasta que está aberta no VS Code, após selecionar essa opção, dê enter e digite o nome do projeto, após confirmar o nome do projeto ele irá abrir já com os arquivos do projeto Java, então basta abrir o arquivo App.java que contêm a main, clicar dentro para tornar a janela ativa e acima do método main irá aparecer o link 'run' ao clicar nele o projeto será executado.

### #5 Jshell

Quem já trabalhou com linguagens como Python, LISP ou Ruby sabe o quão útil é ter uma ferramenta REPL - Read, Evaluate, Print and Loop -, esse tipo de ferramenta auxilia o programador a rapidamente testar e prototipar trechos de código e funções e é especialmente indicada para que todos que programam na linguagem, seja por hobby, aprendizado ou profissionalmente. O [Jshell](https://docs.oracle.com/javase/9/jshell/introduction-jshell.htm#JSHEL-GUID-465BA4F5-E77D-456F-BCB7-D826AC1E18AE) é instalado por padrão em qualquer instalação do Java posterior a versão 9, não sendo necessário instalar nada mais para começar a usar. Para começar a usar basta abrir um terminal e digitar 'jshell', pronto já pode começar a escrever e debbugar seus programas. Apesar de parecer uma ferramente muito simples ela possui muitos comandos e funcionalidades e dominá-la certamente é um ótimo investimento a longo prazo caso tenha a intenção de ser um programador em Java. 

**Obs**: para sair da ferramenta o comando é '\\q', para ajuda '\\h'. De nada. 

**Sugestão de vídeo** (_em Inglês)_**:** [JShell basics - Java Brains](https://www.youtube.com/watch?v=mdafxtP4RZU&list=PLqq-6Pq4lTTZh5EDIPZuaD3S25z49Rodz)

### Bônus: StarUML

[StarUML](http://staruml.io/) é uma ferramenta paga de desenho de diagramas UML. Hoje muitas IDEs possuem plugins para essa função, como Papyrus para Eclipse, PlantUML para VS Code e o InteliJIDEA tem essa função _out of the box_. O diferencial do programa StarUML é que além de ser reconhecida como melhor ferramenta do mercado para esse fim, ela é capaz de produzir praticamente toda a documentação do projeto dentro da ferramenta, desde de Diagrama de Classes até Casos de Uso do projeto. Apesar de UML não ser tão utilizado nas empresas é uma excelente ferramenta para qualquer desenvolvedor que trabalhe com orientação à objetos e apesar de ser paga ela é vendida como um valor único, ou seja, após comprar a versão é sempre sua por tempo indetermidado.

* * *

1.  Disponível em: [https://www.tiobe.com/tiobe-index/](https://www.tiobe.com/tiobe-index/)
2.  Fonte: [https://netflix.github.io/](https://netflix.github.io/)
3.  Fonte: [https://eng.uber.com/tech-stack-part-one/](https://eng.uber.com/tech-stack-part-one/)
4.  Fonte: [https://www.quora.com/What-is-the-technology-stack-of-trivago-com-How-does-it-work](https://www.quora.com/What-is-the-technology-stack-of-trivago-com-How-does-it-work)
5.  Licença disponível em: [https://www.oracle.com/downloads/licenses/javase-license1.html](https://www.oracle.com/downloads/licenses/javase-license1.html)
