---
date:
tags:
  - faculdade
  - programacao-web-backend
  - backend
  - spring-boot
---
**Questão 1**

ORM (Mapeamento Objeto-Relacional) é uma técnica usada para integrar sistemas orientados a objetos com bancos de dados relacionais. Assinale **todas as alternativas corretas** sobre essa técnica:

Escolha uma ou mais:

- [ ] ORM ignora o modelo relacional, pois trabalha exclusivamente com objetos.
- [ ] A técnica ORM permite mapear classes e atributos de uma linguagem orientada a objetos para tabelas e colunas de um banco de dados relacional.
- [ ] ORM, não é mais necessário aprender ou compreender a linguagem SQL.
- [ ] O uso de ORM elimina automaticamente qualquer problema de performance causado por consultas ao banco.
- [ ] O uso de ORM automatiza operações como inserção, atualização, deleção e consulta de registros no banco de dados

---

**Questão 2**

Considere as anotações fornecidas pelo Spring Boot comumente utilizadas em Controllers REST. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] @PathVariable serve para injetar configurações do application.properties no Controller.
- [ ] @GetMapping é uma especialização de @RequestMapping usada para mapear requisições HTTP GET.
- [ ] @RequestBody é usada para vincular o corpo da requisição a um parâmetro de método em um Controller.
- [ ] @RequestMapping pode ser usada para mapear classes ou métodos a caminhos e verbos HTTP.
- [ ] @Entity é uma anotação usada em métodos de Controller para transformar respostas em entidades do banco.
- [ ]

---

**Questão 3**

Associe cada descrição ao padrão de projeto correspondente.

- [ ] Permite trocar dinamicamente o algoritmo usado em um objeto: **Strategy**
- [ ] Permite que múltiplos objetos sejam notificados automaticamente quando outro objeto muda de estado: **Observer**
- [ ] Permite integrar duas interfaces incompatíveis sem alterar o código original: **Adapter**

---

**Questão 4**

O padrão de projeto **Strategy** permite encapsular algoritmos ou comportamentos que podem ser escolhidos em tempo de execução. Assinale **todas as alternativas corretas** sobre esse padrão:

Escolha uma ou mais:

- [ ] Strategy é útil quando temos diversas variações de um algoritmo que podem ser alternadas conforme o contexto.
- [ ] O padrão Strategy depende de uma hierarquia rígida de herança entre classes concretas.
- [ ] O padrão Strategy é apenas uma forma de organizar estruturas condicionais, como if/else.
- [ ] O padrão Strategy permite encapsular algoritmos diferentes e tornar o comportamento de um objeto intercambiável em tempo de execução.
- [ ] O padrão Strategy é usado exclusivamente em algoritmos de ordenação e busca.

---

**Questão 5**

Sobre o uso de anotações no Spring Framework, assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] A anotação @Service permite que uma classe seja detectada automaticamente como bean pelo Spring.
- [ ] A anotação @Autowired pode ser usada normalmente em qualquer classe Java, mesmo fora de aplicações Spring.
- [ ] Toda classe em um projeto Spring precisa ser anotada com @Component para funcionar.
- [ ] A anotação @Autowired é usada para injeção automática de dependências entre beans do Spring.
- [ ] A anotação @Repository é recomendada para classes que realizam operações com o banco de dados.

---

**Questão 6**

A camada Service pode conter lógica de apresentação, como formatação de HTML ou manipulação direta de objetos HTTP.

- [ ] Verdadeiro
- [ ] Falso

---

**Questão 7**

Associe cada descrição à ação HTTP (verbo) mais adequada para uma API REST.

- [ ] Criar um novo recurso no servidor: **POST**
- [ ] Solicitar os dados de um recurso, sem alterar nada no servidor: **GET**
- [ ] Verificar quais métodos HTTP são permitidos em um determinado endpoint: **OPTIONS**
- [ ] Atualizar completamente um recurso existente, substituindo todos os dados: **PUT**
- [ ] Atualizar parcialmente um recurso existente, modificando apenas alguns campos: **PATCH**
- [ ] Remover um recurso existente do servidor: **DELETE**

---

**Questão 8**

Considere as boas práticas ao implementar a camada **Service** em um projeto Spring Boot. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] É aceitável que uma Service contenha lógica de apresentação, como montar HTML ou formatar resposta para o usuário.
- [ ] A Service deve atuar como intermediária entre o Controller e o Repository, centralizando a lógica de negócio.
- [ ] Services bem definidas facilitam a criação de testes unitários, pois isolam a lógica de negócio.
- [ ] O retorno de uma Service pode ser a própria entidade do banco, especialmente quando se deseja reutilização em outras Services ou reduzir repetição de código.
- [ ] Services não devem depender de outras Services sob nenhuma hipótese, pois isso causa acoplamento excessivo.

---

**Questão 9**

Sobre boas práticas e responsabilidades da camada **Service** em uma aplicação Spring Boot, assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] A injeção de dependência em Services deve ser feita preferencialmente via construtor, pois isso facilita testes e manutenção.
- [ ] A Service deve conter anotações como @Entity e @Id para persistência correta no banco de dados.
- [ ] É recomendável que a Service manipule diretamente os dados da requisição (DTO de entrada) e da resposta (DTO de saída).
- [ ] É comum que uma Service reutilize lógica de negócio agrupando funcionalidades que podem ser compartilhadas entre diferentes Controllers.
- [ ] A Service não deve acessar diretamente objetos da camada de visualização (como DTOs ou objetos HTTP), mantendo a separação de responsabilidades.

---

**Questão 10**

Analise as afirmações a seguir sobre boas práticas e responsabilidades dos **Controllers** em uma API REST com Spring Boot. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] O Controller atua como um intermediador: recebe requisições, valida dados e repassa para o Service tratar a lógica de negócio.
- [ ] Controllers devem sempre retornar diretamente entidades JPA para evitar mapeamentos e simplificar o código.
- [ ] É recomendável que os Controllers contenham diretamente a lógica de acesso ao banco para simplificar o código.
- [ ] Controllers devem receber e validar os dados de entrada, utilizando anotações como @Valid em conjunto com DTOs.
- [ ] Controllers devem retornar respostas apropriadas à API, podendo usar objetos como ResponseEntity para controlar status, cabeçalhos e corpo.

---

**Questão 11**

Sobre o uso de anotações na definição de entidades em projetos com Spring Data JPA, assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] A anotação @Id define qual atributo será utilizado como chave primária da entidade.
- [ ] A anotação @Autowired deve ser usada nos atributos da entidade para injetar os repositórios necessários.
- [ ] A anotação @Entity é usada para indicar que uma classe representa uma tabela no banco de dados.
- [ ] A anotação @GeneratedValue permite que a chave primária seja gerada automaticamente pelo banco ou provedor JPA.
- [ ] A anotação @RestController é usada nas entidades para que elas possam ser expostas diretamente via API.

---

**Questão 12**

Os códigos da família **4xx** indicam que houve um erro por parte do cliente em uma requisição HTTP. Assinale **todas as alternativas corretas** sobre o uso desses códigos em APIs REST:

Escolha uma ou mais:

- [ ] O código 422 Unprocessable Entity deve ser usado para indicar que o servidor teve um erro interno ao processar a requisição.
- [ ] O código 409 Conflict é apropriado quando há um conflito de estado, como tentar cadastrar um e-mail já existente.
- [ ] O código 404 Not Found é utilizado quando o recurso solicitado não existe na API.
- [ ] O código 401 Unauthorized é usado quando o usuário está autenticado, mas não tem permissão para acessar o recurso.
- [ ] O código 400 Bad Request é usado quando a requisição está malformada ou os dados enviados são inválidos.

---

**Questão 13**

Considere a seguinte resposta HTTP, retornada por uma API ao tentar cadastrar um e-mail que já existe:

`HTTP/1.1 409 Conflict  
Content-Type: application/json  
Content-Length: 88

{  
"erro": "E-mail já cadastrado.",  
"codigo": "EMAIL_DUPLICADO",  
"timestamp": "2025-04-05T10:30:00Z"  
}`

Com base nessa resposta, assinale **todas as afirmações corretas**:

Escolha uma ou mais:

- [ ] O cabeçalho Content-Length define o número de linhas retornadas no corpo da resposta.
- [ ] O código 409 Conflict indica que houve um conflito de dados ao processar a requisição.
- [ ] O corpo da resposta está estruturado em JSON e fornece detalhes sobre o erro ocorrido.
- [ ] O código 409 indica que o recurso solicitado não foi encontrado.
- [ ] É uma boa prática que APIs retornem mensagens de erro claras e estruturadas, como visto nessa resposta.

---

**Questão 14**

Ao receber uma resposta de uma requisição HTTP, a estrutura da resposta segue um padrão definido pelo protocolo. Assinale **todos os componentes que estão presentes em toda resposta HTTP válida**:

Escolha uma ou mais:

- [ ] Cookies devem ser incluídos em toda resposta HTTP para manter a sessão ativa.
- [ ] O código de status HTTP, como 200, 404 ou 500, indicando o resultado da requisição.
- [ ] A versão do protocolo HTTP, como HTTP/1.1 ou HTTP/2.
- [ ] O corpo da resposta (body), com os dados retornados pela API, é sempre obrigatório.
- [ ] Cabeçalhos de resposta (headers), como Content-Type ou Content-Length.

---

**Questão 15**

Sobre o conceito de injeção de dependência no Spring Framework e o uso da anotação **@Autowired**, assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] A anotação @Autowired pode ser utilizada para injetar dependências em atributos, métodos ou construtores.
- [ ] O uso de @Autowired exige que a classe anotada esteja definida como final.
- [ ] O uso de injeção de dependência ajuda a reduzir o acoplamento entre as classes, facilitando testes e manutenção.
- [ ] @Autowired funciona normalmente em qualquer classe Java, mesmo fora de um projeto Spring.
- [ ] Para usar @Autowired corretamente, é necessário instanciar os objetos manualmente com new.

---

**Questão 16**

No contexto de uma API REST, os cabeçalhos HTTP são utilizados para fornecer informações adicionais sobre a requisição ou a resposta. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] O cabeçalho Content-Type indica o formato dos dados enviados no corpo da requisição, como application/json.
- [ ] Cabeçalhos HTTP são ignorados pelas APIs REST, já que toda a informação necessária está na URL ou no corpo da requisição.
- [ ] O cabeçalho Authorization é usado para enviar tokens de autenticação, como Bearer tokens em APIs REST.
- [ ] O cabeçalho Accept é usado pelo cliente para indicar qual formato deseja receber na resposta, como JSON ou XML.
- [ ] O cabeçalho Host define quais campos devem ser obrigatórios em um formulário enviado via POST.

---

**Questão 17**

Padrões de Projeto são soluções reutilizáveis? Assinale **todas as alternativas corretas** sobre os Padrões de Projeto e suas classificações:

Escolha uma ou mais:

- [ ] Padrões de Projeto são soluções genéricas que ajudam a resolver problemas comuns de arquitetura e design de software.
- [ ] Padrões criacionais estão relacionados à forma como objetos são instanciados, como Singleton e Factory Method.
- [ ] Um padrão de projeto define a implementação exata e obrigatória que o desenvolvedor deve seguir.
- [ ] Padrões de Projeto só se aplicam em projetos grandes e com muitos desenvolvedores.
- [ ] Os padrões de projeto são geralmente organizados em três categorias: criacionais, estruturais e comportamentais.

---

**Questão 18**

Sobre o uso de **Service** no Spring Boot e as anotações do framework, assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] O Spring exige que as Services sejam instanciadas manualmente usando a palavra-chave new.
- [ ] Classes anotadas com @Service são, por padrão, beans singleton no Spring.
- [ ] A injeção de dependência em Services pode ser feita via construtor, sendo essa a abordagem mais recomendada.
- [ ] Para que o Spring reconheça uma classe como Service, é obrigatório criar um arquivo XML de configuração manual.
- [ ] A anotação @Service registra a classe no contexto do Spring para ser gerenciada como um bean.

---

**Questão 19**

Considere as seguintes afirmações sobre a camada **Service** em uma aplicação Spring Boot. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] a. A camada Service deve conter apenas chamadas de banco de dados e não pode conter nenhuma lógica de negócio.
- [ ] b. A camada Service deve conter regras de negócio e orquestrar chamadas para outras camadas, como repositórios e APIs externas.
- [ ] c. A camada Service é responsável por receber requisições HTTP diretamente dos clientes e encaminhá-las para o Repository.
- [ ] d. Uma classe Service pode depender de outras classes Service para organizar melhor responsabilidades.
- [ ] e. É uma boa prática anotar as classes da camada Service com @Service para que o Spring as registre como beans gerenciados.

---

**Questão 20**

É considerado boa prática que um Controller acesse diretamente o banco de dados usando Repositories.

- [ ] Verdadeiro
- [ ] Falso

---

**Questão 21** (A partir da 3ª tentativa)

O padrão Strategy permite que um objeto altere seu comportamento em tempo de execução, ao trocar dinamicamente a estratégia utilizada.

- [ ] Verdadeiro
- [ ] Falso

---

**Questão 22** (A partir da 3ª tentativa)

Considere as anotações fornecidas pelo Spring Boot comumente utilizadas em Controllers REST. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] @GetMapping é uma especialização de @RequestMapping usada para mapear requisições HTTP GET.
- [ ] @Entity é uma anotação usada em métodos de Controller para transformar respostas em entidades do banco.
- [ ] @PathVariable serve para injetar configurações do application.properties no Controller.
- [ ] @RequestMapping pode ser usada para mapear classes ou métodos a caminhos e verbos HTTP.
- [ ] @RequestBody é usada para vincular o corpo da requisição a um parâmetro de método em um Controller.

---

**Questão 23** (A partir da 3ª tentativa)

Repositórios definidos como interfaces que estendem JpaRepository são, por padrão, gerenciados como beans singleton pelo Spring.

- [ ] Verdadeiro
- [ ] Falso

---

**Questão 24** (A partir da 3ª tentativa)

Sobre o uso de anotações no Spring Framework, assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] Toda classe em um projeto Spring precisa ser anotada com @Component para funcionar.
- [ ] A anotação @Service permite que uma classe seja detectada automaticamente como bean pelo Spring.
- [ ] A anotação @Repository é recomendada para classes que realizam operações com o banco de dados.
- [ ] A anotação @Autowired pode ser usada normalmente em qualquer classe Java, mesmo fora de aplicações Spring.
- [ ] A anotação @Autowired é usada para injeção automática de dependências entre beans do Spring.

---

**Questão 25** (A partir da 3ª tentativa)

Sobre JPQL (Java Persistence Query Language), assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] JPQL permite o uso de alias para entidades na cláusula FROM, facilitando a escrita e leitura de consultas.
- [ ] JPQL permite usar SELECT * para retornar todos os dados de uma entidade.
- [ ] Em JPQL, usamos os nomes das entidades Java e seus atributos, e não os nomes das tabelas e colunas do banco de dados.
- [ ] Em JPQL, joins são realizados entre tabelas diretamente, como em SQL tradicional.
- [ ] É possível usar funções específicas de banco de dados como NOW() diretamente em JPQL sem adaptações.

---

**Questão 26** (A partir da 3ª tentativa)

Analise as afirmações a seguir sobre boas práticas e responsabilidades dos **Controllers** em uma API REST com Spring Boot. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] Controllers devem sempre retornar diretamente entidades JPA para evitar mapeamentos e simplificar o código.
- [ ] O Controller atua como um intermediador: recebe requisições, valida dados e repassa para o Service tratar a lógica de negócio.
- [ ] Controllers devem receber e validar os dados de entrada, utilizando anotações como @Valid em conjunto com DTOs.
- [ ] Controllers devem retornar respostas apropriadas à API, podendo usar objetos como ResponseEntity para controlar status, cabeçalhos e corpo.
- [ ] É recomendável que os Controllers contenham diretamente a lógica de acesso ao banco para simplificar o código.

---

**Questão 27** (A partir da 3ª tentativa)

Em qualquer requisição HTTP válida, alguns componentes são obrigatórios e formam a estrutura mínima da requisição. Assinale **todos os componentes que estão presentes em toda requisição HTTP**:

Escolha uma ou mais:

- [ ] O método HTTP (como GET, POST, etc.), que define qual ação será executada no recurso.
- [ ] Cabeçalhos HTTP mínimos, como o cabeçalho Host, que identifica o servidor de destino.
- [ ] O caminho (URL) para o recurso que está sendo solicitado.
- [ ] O corpo da requisição (body), onde os dados são enviados.
- [ ] Parâmetros de requisição, como ?pagina=1, são obrigatórios em todas as requisições HTTP.

---

**Questão 28** (A partir da 3ª tentativa)

Considere as boas práticas ao implementar a camada **Service** em um projeto Spring Boot. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] Services não devem depender de outras Services sob nenhuma hipótese, pois isso causa acoplamento excessivo.
- [ ] A Service deve atuar como intermediária entre o Controller e o Repository, centralizando a lógica de negócio.
- [ ] O retorno de uma Service pode ser a própria entidade do banco, especialmente quando se deseja reutilização em outras Services ou reduzir repetição de código.
- [ ] É aceitável que uma Service contenha lógica de apresentação, como montar HTML ou formatar resposta para o usuário.
- [ ] Services bem definidas facilitam a criação de testes unitários, pois isolam a lógica de negócio.

---

**Questão 29** (A partir da 3ª tentativa)

Associe cada descrição à ação HTTP (verbo) mais adequada para uma API REST.

- Solicitar os dados de um recurso, sem alterar nada no servidor: **GET**
- Remover um recurso existente do servidor: **DELETE**
- Atualizar completamente um recurso existente, substituindo todos os dados: **PUT**
- Atualizar parcialmente um recurso existente, modificando apenas alguns campos: **PATCH**
- Verificar quais métodos HTTP são permitidos em um determinado endpoint: **OPTIONS**
- Criar um novo recurso no servidor: **POST**

---

**Questão 30** (A partir da 3ª tentativa)

É permitido e, em muitos casos, recomendado que uma classe Service chame outra classe Service quando há lógica de negócio compartilhada.

- [ ] Verdadeiro
- [ ] Falso

---

**Questão 31** (A partir da 3ª tentativa)

Um Controller no Spring Boot deve receber as requisições HTTP, validar os dados e delegar a lógica de negócio para a camada Service.

- [ ] Verdadeiro
- [ ] Falso

---

**Questão 32** (A partir da 3ª tentativa)

Considere as seguintes afirmações sobre a camada **Service** em uma aplicação Spring Boot. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] a. A camada Service deve conter regras de negócio e orquestrar chamadas para outras camadas, como repositórios e APIs externas.
- [ ] b. É uma boa prática anotar as classes da camada Service com @Service para que o Spring as registre como beans gerenciados.
- [ ] c. A camada Service é responsável por receber requisições HTTP diretamente dos clientes e encaminhá-las para o Repository.
- [ ] d. Uma classe Service pode depender de outras classes Service para organizar melhor responsabilidades.
- [ ] e. A camada Service deve conter apenas chamadas de banco de dados e não pode conter nenhuma lógica de negócio.

---

**Questão 33** (A partir da 3ª tentativa)

Considere a resposta abaixo, retornada por uma API REST após uma requisição:

`HTTP/1.1 200 OK  
Content-Type: application/json  
Content-Length: 58

{  
"id": 101,  
"nome": "João",  
"email": "[joao@email.com](mailto:joao@email.com)"  
}`

Com base nessa resposta, assinale **todas as afirmações corretas**:

Escolha uma ou mais:

- [ ] Como o código 200 foi retornado, o corpo obrigatoriamente deve conter um token JWT para autenticação.
- [ ] O corpo da resposta contém os dados do recurso solicitado, no caso, um usuário com nome, e-mail e ID.
- [ ] O cabeçalho Content-Type informa que o corpo da resposta está no formato JSON.
- [ ] O código 200 OK indica que a requisição foi processada com sucesso.
- [ ] O cabeçalho Content-Length indica a quantidade de campos retornados no JSON.

---

**Questão 34** (A partir da 3ª tentativa)

Considere a seguinte resposta HTTP, retornada por uma API ao tentar cadastrar um e-mail que já existe:

`HTTP/1.1 409 Conflict  
Content-Type: application/json  
Content-Length: 88

{  
"erro": "E-mail já cadastrado.",  
"codigo": "EMAIL_DUPLICADO",  
"timestamp": "2025-04-05T10:30:00Z"  
}`

Com base nessa resposta, assinale **todas as afirmações corretas**:

Escolha uma ou mais:

- [ ] O corpo da resposta está estruturado em JSON e fornece detalhes sobre o erro ocorrido.
- [ ] O código 409 Conflict indica que houve um conflito de dados ao processar a requisição.
- [ ] O cabeçalho Content-Length define o número de linhas retornadas no corpo da resposta.
- [ ] É uma boa prática que APIs retornem mensagens de erro claras e estruturadas, como visto nessa resposta.
- [ ] O código 409 indica que o recurso solicitado não foi encontrado.

---

**Questão 35** (A partir da 3ª tentativa)

Sobre o uso de **Service** no Spring Boot e as anotações do framework, assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] O Spring exige que as Services sejam instanciadas manualmente usando a palavra-chave new.
- [ ] A anotação @Service registra a classe no contexto do Spring para ser gerenciada como um bean.
- [ ] Para que o Spring reconheça uma classe como Service, é obrigatório criar um arquivo XML de configuração manual.
- [ ] Classes anotadas com @Service são, por padrão, beans singleton no Spring.
- [ ] A injeção de dependência em Services pode ser feita via construtor, sendo essa a abordagem mais recomendada.

---

**Questão 36** (A partir da 3ª tentativa)

Um Controller pode receber instâncias de Services via injeção de dependência, seja por construtor ou com a anotação @Autowired.

- [ ] Verdadeiro
- [ ] Falso

---

**Questão 37** (A partir da 3ª tentativa)

Sobre DTOs, é correto afirmar:  
I. É o anagrama para Data Transfer Object. São classes criadas para não terem nenhuma regra complexa nelas. Basicamente possuem atributos e getters/setters.  
II. É um padrão de projetos que só existe em Java e só deve ser aplicado em projetos REST.  
III. Podemos usar anotações de validação em DTO's, como @NotBlank, @Min, @Past etc.  
IV. É apenas outro nome para as classes de Entidade, usadas para mapear as tabelas em classes. V. Serve para transferir dados, entre camadas da própria aplicação e/ou para outras aplicações.

- [ ] a. Apenas II, IV e V estão corretas.
- [ ] b. Apenas II, III e IV estão corretas.
- [ ] c. Apenas I, III e V estão corretas.
- [ ] d. Nenhuma das alternativas.
- [ ] e. Apenas I, II e V estão corretas.

---

**Questão 38** (A partir da 3ª tentativa)

O padrão Singleton garante que uma classe tenha apenas uma instância em todo o sistema. No contexto do Spring Boot, assinale **todas as alternativas corretas** sobre o uso desse padrão:

Escolha uma ou mais:

- [ ] Em aplicações Spring Boot, deve-se evitar beans singleton, pois eles não são thread-safe.
- [ ] Para que um bean seja singleton no Spring, é obrigatório usar variáveis estáticas e métodos sincronizados.
- [ ] O escopo padrão de um bean no Spring é singleton, ou seja, apenas uma instância é criada e compartilhada.
- [ ] O Spring Boot gerencia automaticamente os beans singleton, não sendo necessário implementar o padrão manualmente.
- [ ] É necessário criar uma instância manualmente com "new" e armazená-la em cache para simular o comportamento singleton no Spring.

---

**Questão 39** (A partir da 3ª tentativa)

Em APIs REST, o design das URLs (endpoints) deve seguir algumas boas práticas para manter a API semântica, padronizada e de fácil entendimento. Assinale **todas as alternativas corretas**:

Escolha uma ou mais:

- [ ] É recomendado usar URLs como /getLivros ou /criarUsuario para deixar claro o que a API faz.
- [ ] As URLs em uma API REST devem usar substantivos no plural para representar coleções de recursos, como /livros ou /usuarios.
- [ ] Hierarquia entre recursos pode ser representada nas URLs, como em /usuarios/42/livros.
- [ ] Deve-se incluir o tipo de retorno na URL, como /livros.json ou /usuarios.xml.
- [ ] Evita-se o uso de verbos nas URLs, pois a ação é representada pelo método HTTP (GET, POST, etc.).
