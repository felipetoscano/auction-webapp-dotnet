# Leilão Online
Projeto de site de um leilão online, com o objetivo de explicar os princípios SOLID.

## Explicando conceitos SOLID

**SOLID** se trata de um conjunto de princípios de boas práticas para melhorar a qualidade do seu software e fazer com que ele permaneça sempre estável e cresça com facilidade, conforme são feitas manutenções e melhorias.

Conforme um projeto cresce, se ele não for bem estruturado e seguir boas práticas desde o início, irá gerar vários "débitos técnicos", fazendo com que ele fique estagnado e futuramente "morra". Um código de má qualidade possui alta dívida técnica que com o tempo se torna cada vez mais difícil de quitar.

O **SOLID** vem para nos ajudar a resolver estes problemas. Cada uma das letras é a abreviação de um conceito e cada um deles será explicado abaixo.

Para a aplicação destes conceitos no nosso software, utilizamos a experiência de outros desenvolvedores através de princípios e design patterns.

## S (Single Responsability Principle)
- Cada método/classe/módulo deve ter sua responsabilidade bem definida. Apenas desta forma manterão a coesão.
- "Uma classe deve ter um, e apenas um, motivo para ser modificada".
- Além disso, a repetição de código entra neste princípio, pois caso um mesmo código esteja em vários lugares, pode indicar que os métodos e classes possuem muitas responsabilidades.
- O príncipio explicado ao código repetido refere-se ao conceito DRY (Don't Repeat Yourself).
## O (Open Closed Principle)
- Minimize a alteração de código que está pronto (fechado) mas garanta que seu projeto continue estensível (aberto).
- Ou seja, caso surja uma nova regra de negócio ou uma implementação a mais dentro de um método de uma classe já criada e estável, em vez de alterarmos a própria classe e a mantermos instável, podemos utilizar algumas técnicas para não alterarmos ela diretamente, com Design Pattern Decorator por exemplo, criando uma nova classe para essa nova implementação, complementando as implementações originais.
## L (Liskov Substitution Principle)
- Resumidamente, este princípio prega que sempre devemos manter a promessa da implementação de uma abstração. 
- Ou seja, se uma classe abstrata possui os métodos Adiciona() e Remove(), devemos sempre implementar corretamente estes métodos nas subclasses.
- Isso requer que os objetos de suas subclasses se comportem da mesma forma que os objetos de sua superclasse.
- Um método substituído de uma subclasse precisa aceitar os mesmos valores de parâmetro de entrada que o método da superclasse. Isso significa que você pode implementar regras de validação menos restritivas, mas você não está autorizado a impor regras mais rigorosas em sua subclasse. Caso contrário, qualquer código que chame esse método em um objeto da superclasse pode causar uma exceção, se for chamado com um objeto da subclasse.
## I (Interface Segregation Principle)
- Classes genéricas como abstratas ou interfaces, apesar de serem bem genéricas, ainda sim podem perder a sua coesão.
- Caso percam, correm o risco de propagar promessas que em algum momento não vão ser cumpridas pelas suas subclasses, furando a letra "L" do SOLID.
- Para manter a coesão nestas classes abstratas, podemos separar estas operações de interfaces em outras menores, utilizando conceitos de CQRS (Command and Query Responsability Segregation).
- Em um exemplo de interface Dao (Data Access Object, cuida da camada de dados da aplicação, realizando operações básicas no repositório de dados), podemos separar esta interface em outras duas, uma voltada para os comandos e outra para as querys.
## D (Dependency Inversion Principle)
- O acoplamento diz respeito à dependencia entre dois tipos. Num sistema orientado a objetos, os acoplamentos são inevitáveis. O que devemos fazer é cuidar de sua qualidade. Acoplamentos bons são aqueles para tipos estáveis (que não vão mudar ou tem alta probabilidade de não mudar). Acoplamentos ruins são aqueles para tipos instáveis. Exemplos dessa categoria são os tipos criados especificamente para nossa aplicação e principalmente implementações para mecanismos específicos.
- Para reduzir o acoplamento ruim entre as classes e mantê-las mais independentes, foi criado o princípio de inversão de dependência, que prega que quem chama a classe deve cuidar das suas dependencias, não ela mesma. 
- Exemplo: a classe ClienteController necessita da classe ClienteService. Em vez da própria Controller cuidar de resolver a dependência da ClienteService, quem chama a Controller é quem deve resolver isso, passando via construtor essa dependência. 
- Implementando este conceito, as classes literalmente invertem a sua dependência, resultando que no final quem deve resolver todas elas é a própria API do .Net, através da injeção de dependências.




