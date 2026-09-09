---
date:
tags:
  - faculdade
  - programacao-web-backend
  - backend
  - spring-boot
---
**1. ORM (Mapeamento Objeto-Relacional) é uma técnica usada para integrar sistemas orientados a objetos com bancos de dados relacionais. Assinale todas as alternativas corretas sobre essa técnica:**

Escolha uma ou mais:

- [ ] ORM ignora o modelo relacional, pois trabalha exclusivamente com objetos.
    
- [x] A técnica ORM permite mapear classes e atributos de uma linguagem orientada a objetos para tabelas e colunas de um banco de dados relacional.
    
- [ ] Com ORM, não é mais necessário aprender ou compreender a linguagem SQL.
    
- [ ] O uso de ORM elimina automaticamente qualquer problema de performance causado por consultas ao banco.
    
- [x] O uso de ORM automatiza operações como inserção, atualização, deleção e consulta de registros no banco de dados.
    
- Resposta:
    
    A técnica ORM permite mapear classes e atributos de uma linguagem orientada a objetos para tabelas e colunas de um banco de dados relacional.
    
    O uso de ORM automatiza operações como inserção, atualização, deleção e consulta de registros no banco de dados.
    

**2. Considere as anotações fornecidas pelo Spring Boot comumente utilizadas em Controllers REST. Assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] @PathVariable serve para injetar configurações do application.properties no Controller.
    
- [x] @GetMapping é uma especialização de @RequestMapping usada para mapear requisições HTTP GET.
    
- [x] @RequestBody é usada para vincular o corpo da requisição a um parâmetro de método em um Controller.
    
- [x] @RequestMapping pode ser usada para mapear classes ou métodos a caminhos e verbos HTTP.
    
- [ ] @Entity é uma anotação usada em métodos de Controller para transformar respostas em entidades do banco.
    
- Resposta:
    
    @GetMapping é uma especialização de @RequestMapping usada para mapear requisições HTTP GET.
    
    @RequestBody é usada para vincular o corpo da requisição a um parâmetro de método em um Controller.
    
    @RequestMapping pode ser usada para mapear classes ou métodos a caminhos e verbos HTTP.
    

**3. Associe cada descrição ao padrão de projeto correspondente.**

- [ ] Permite trocar dinamicamente o algoritmo usado em um objeto
- [x] Permite que múltiplos objetos sejam notificados automaticamente quando outro objeto muda de estado
- [ ] Permite integrar duas interfaces incompatíveis sem alterar o código original
- Resposta:
    - Permite trocar dinamicamente o algoritmo usado em um objeto → **Strategy**
    - Permite que múltiplos objetos sejam notificados automaticamente quando outro objeto muda de estado → **Observer**
    - Permite integrar duas interfaces incompatíveis sem alterar o código original → **Adapter**

**4. O padrão de projeto Strategy permite encapsular algoritmos ou comportamentos que podem ser escolhidos em tempo de execução. Assinale todas as alternativas corretas sobre esse padrão:**

Escolha uma ou mais:

- [x] Strategy é útil quando temos diversas variações de um algoritmo que podem ser alternadas conforme o contexto.
- [ ] O padrão Strategy depende de uma hierarquia rígida de herança entre classes concretas.
- [ ] O padrão Strategy é apenas uma forma de organizar estruturas condicionais, como if/else.
- [x] O padrão Strategy permite encapsular algoritmos diferentes e tornar o comportamento de um objeto intercambiável em tempo de execução.
- [ ] O padrão Strategy é usado exclusivamente em algoritmos de ordenação e busca.
- Resposta:
    - Strategy é útil quando temos diversas variações de um algoritmo que podem ser alternadas conforme o contexto.
    - O padrão Strategy permite encapsular algoritmos diferentes e tornar o comportamento de um objeto intercambiável em tempo de execução.

**5. Sobre o uso de anotações no Spring Framework, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [x] A anotação @Service permite que uma classe seja detectada automaticamente como bean pelo Spring.
- [ ] A anotação @Autowired pode ser usada normalmente em qualquer classe Java, mesmo fora de aplicações Spring.
- [ ] Toda classe em um projeto Spring precisa ser anotada com @Component para funcionar.
- [x] A anotação @Autowired é usada para injeção automática de dependências entre beans do Spring.
- [x] A anotação @Repository é recomendada para classes que realizam operações com o banco de dados.
- Resposta:
    - A anotação @Service permite que uma classe seja detectada automaticamente como bean pelo Spring.
    - A anotação @Autowired é usada para injeção automática de dependências entre beans do Spring.
    - A anotação @Repository é recomendada para classes que realizam operações com o banco de dados.

**6. A camada Service pode conter lógica de apresentação, como formatação de HTML ou manipulação direta de objetos HTTP.**

- [ ] Verdadeiro
    
- [x] Falso
    
- Resposta:
    
    Falso
    

**7. Associe cada descrição à ação HTTP (verbo) mais adequada para uma API REST.**

- [ ] Criar um novo recurso no servidor
- [ ] Solicitar os dados de um recurso, sem alterar nada no servidor
- [ ] Verificar quais métodos HTTP são permitidos em um determinado endpoint
- [ ] Atualizar completamente um recurso existente, substituindo todos os dados
- [ ] Atualizar parcialmente um recurso existente, modificando apenas alguns campos
- [ ] Remover um recurso existente do servidor
- Resposta:
    - Criar um novo recurso no servidor → **POST**
    - Solicitar os dados de um recurso, sem alterar nada no servidor → **GET**
    - Verificar quais métodos HTTP são permitidos em um determinado endpoint → **OPTIONS**
    - Atualizar completamente um recurso existente, substituindo todos os dados → **PUT**
    - Atualizar parcialmente um recurso existente, modificando apenas alguns campos → **PATCH**
    - Remover um recurso existente do servidor → **DELETE**

**8. Considere as boas práticas ao implementar a camada Service em um projeto Spring Boot. Assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] É aceitável que uma Service contenha lógica de apresentação, como montar HTML ou formatar resposta para o usuário.
- [x] A Service deve atuar como intermediária entre o Controller e o Repository, centralizando a lógica de negócio.
- [x] Services bem definidas facilitam a criação de testes unitários, pois isolam a lógica de negócio.
- [x] O retorno de uma Service pode ser a própria entidade do banco, especialmente quando se deseja reutilização em outras Services ou reduzir repetição de código.
- [ ] Services não devem depender de outras Services sob nenhuma hipótese, pois isso causa acoplamento excessivo.
- Resposta:
    - A Service deve atuar como intermediária entre o Controller e o Repository, centralizando a lógica de negócio.
    - Services bem definidas facilitam a criação de testes unitários, pois isolam a lógica de negócio.
    - O retorno de uma Service pode ser a própria entidade do banco, especialmente quando se deseja reutilização em outras Services ou reduzir repetição de código.

**9. Sobre boas práticas e responsabilidades da camada Service em uma aplicação Spring Boot, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [x] A injeção de dependência em Services deve ser feita preferencialmente via construtor, pois isso facilita testes e manutenção.
- [ ] A Service deve conter anotações como @Entity e @Id para persistência correta no banco de dados.
- [ ] É recomendável que a Service manipule diretamente os dados da requisição (DTO de entrada) e da resposta (DTO de saída).
- [x] É comum que uma Service reutilize lógica de negócio agrupando funcionalidades que podem ser compartilhadas entre diferentes Controllers.
- [x] A Service não deve acessar diretamente objetos da camada de visualização (como DTOs ou objetos HTTP), mantendo a separação de responsabilidades.
- Resposta:
    - **A injeção de dependência em Services deve ser feita preferencialmente via construtor, pois isso facilita testes e manutenção.**
    - **É comum que uma Service reutilize lógica de negócio agrupando funcionalidades que podem ser compartilhadas entre diferentes Controllers.**
    - **A Service não deve acessar diretamente objetos da camada de visualização (como DTOs ou objetos HTTP), mantendo a separação de responsabilidades.**

**10. Analise as afirmações a seguir sobre boas práticas e responsabilidades dos Controllers em uma API REST com Spring Boot. Assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] Controllers devem sempre retornar diretamente entidades JPA para evitar mapeamentos e simplificar o código.
    
- [x] O Controller atua como um intermediador: recebe requisições, valida dados e repassa para o Service tratar a lógica de negócio.
    
- [ ] É recomendável que os Controllers contenham diretamente a lógica de acesso ao banco para simplificar o código.
    
- [x] Controllers devem receber e validar os dados de entrada, utilizando anotações como @Valid em conjunto com DTOs.
    
- [x] Controllers devem retornar respostas apropriadas à API, podendo usar objetos como ResponseEntity para controlar status, cabeçalhos e corpo.
    
- Resposta:
    
    O Controller atua como um intermediador: recebe requisições, valida dados e repassa para o Service tratar a lógica de negócio.
    
    Controllers devem receber e validar os dados de entrada, utilizando anotações como @Valid em conjunto com DTOs.
    
    Controllers devem retornar respostas apropriadas à API, podendo usar objetos como ResponseEntity para controlar status, cabeçalhos e corpo.
    

**11. Sobre o uso de anotações na definição de entidades em projetos com Spring Data JPA, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [x] A anotação @Id define qual atributo será utilizado como chave primária da entidade.
    
- [ ] A anotação @Autowired deve ser usada nos atributos da entidade para injetar os repositórios necessários.
    
- [x] A anotação @Entity é usada para indicar que uma classe representa uma tabela no banco de dados.
    
- [x] A anotação @GeneratedValue permite que a chave primária seja gerada automaticamente pelo banco ou provedor JPA.
    
- [ ] A anotação @RestController é usada nas entidades para que elas possam ser expostas diretamente via API.
    
- Resposta:
    
    A anotação @Id define qual atributo será utilizado como chave primária da entidade.
    
    A anotação @Entity é usada para indicar que uma classe representa uma tabela no banco de dados.
    
    A anotação @GeneratedValue permite que a chave primária seja gerada automaticamente pelo banco ou provedor JPA.
    

**12. Os códigos da família 4xx indicam que houve um erro por parte do cliente em uma requisição HTTP. Assinale todas as alternativas corretas sobre o uso desses códigos em APIs REST:**

Escolha uma ou mais:

- [ ] O código 422 Unprocessable Entity deve ser usado para indicar que o servidor teve um erro interno ao processar a requisição.
    
- [x] O código 409 Conflict é apropriado quando há um conflito de estado, como tentar cadastrar um e-mail já existente.
    
- [x] O código 404 Not Found é utilizado quando o recurso solicitado não existe na API.
    
- [ ] O código 401 Unauthorized é usado quando o usuário está autenticado, mas não tem permissão para acessar o recurso.
    
- [x] O código 400 Bad Request é usado quando a requisição está malformada ou os dados enviados são inválidos.
    
- Resposta:
    
    O código 409 Conflict é apropriado quando há um conflito de estado, como tentar cadastrar um e-mail já existente.
    
    O código 404 Not Found é utilizado quando o recurso solicitado não existe na API.
    
    O código 400 Bad Request é usado quando a requisição está malformada ou os dados enviados são inválidos.
    

**13. Considere a seguinte resposta HTTP, retornada por uma API ao tentar cadastrar um e-mail que já existe:**

`HTTP/1.1 409 Conflict  
Content-Type: application/json  
Content-Length: 88

{  
"erro": "E-mail já cadastrado.",  
"codigo": "EMAIL_DUPLICADO",  
"timestamp": "2025-04-05T10:30:00Z"  
}`

Com base nessa resposta, assinale todas as afirmações corretas:

Escolha uma ou mais:

- [ ] O cabeçalho Content-Length define o número de linhas retornadas no corpo da resposta.
    
- [x] O código 409 Conflict indica que houve um conflito de dados ao processar a requisição.
    
- [x] O corpo da resposta está estruturado em JSON e fornece detalhes sobre o erro ocorrido.
    
- [ ] O código 409 indica que o recurso solicitado não foi encontrado.
    
- [x] É uma boa prática que APIs retornem mensagens de erro claras e estruturadas, como visto nessa resposta.
    
- Resposta:
    
    O código 409 Conflict indica que houve um conflito de dados ao processar a requisição.
    
    O corpo da resposta está estruturado em JSON e fornece detalhes sobre o erro ocorrido.
    
    É uma boa prática que APIs retornem mensagens de erro claras e estruturadas, como visto nessa resposta.
    

**14. Ao receber uma resposta de uma requisição HTTP, a estrutura da resposta segue um padrão definido pelo protocolo. Assinale todos os componentes que estão presentes em toda resposta HTTP válida:**

Escolha uma ou mais:

- [ ] Cookies devem ser incluídos em toda resposta HTTP para manter a sessão ativa.
- [x] O código de status HTTP, como 200, 404 ou 500, indicando o resultado da requisição.
- [x] A versão do protocolo HTTP, como HTTP/1.1 ou HTTP/2.
- [ ] O corpo da resposta (body), com os dados retornados pela API, é sempre obrigatório.
- [x] Cabeçalhos de resposta (headers), como Content-Type ou Content-Length.
- Resposta:
    - O código de status HTTP, como 200, 404 ou 500, indicando o resultado da requisição.
    - A versão do protocolo HTTP, como HTTP/1.1 ou HTTP/2.
    - Cabeçalhos de resposta (headers), como Content-Type ou Content-Length.

**15. Sobre o conceito de injeção de dependência no Spring Framework e o uso da anotação @Autowired, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] A anotação @Autowired pode ser utilizada para injetar dependências em atributos, métodos ou construtores.
    
- [ ] O uso de @Autowired exige que a classe anotada esteja definida como final.
    
- [ ] O uso de injeção de dependência ajuda a reduzir o acoplamento entre as classes, facilitando testes e manutenção.
    
- [ ] @Autowired funciona normalmente em qualquer classe Java, mesmo fora de um projeto Spring.
    
- [ ] Para usar @Autowired corretamente, é necessário instanciar os objetos manualmente com new.
    
- Resposta:
    
    A anotação @Autowired pode ser utilizada para injetar dependências em atributos, métodos ou construtores.
    
    O uso de injeção de dependência ajuda a reduzir o acoplamento entre as classes, facilitando testes e manutenção.
    

**16. No contexto de uma API REST, os cabeçalhos HTTP são utilizados para fornecer informações adicionais sobre a requisição ou a resposta. Assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] O cabeçalho Content-Type indica o formato dos dados enviados no corpo da requisição, como application/json.
    
- [ ] Cabeçalhos HTTP são ignorados pelas APIs REST, já que toda a informação necessária está na URL ou no corpo da requisição.
    
- [ ] O cabeçalho Authorization é usado para enviar tokens de autenticação, como Bearer tokens em APIs REST.
    
- [ ] O cabeçalho Accept é usado pelo cliente para indicar qual formato deseja receber na resposta, como JSON ou XML.
    
- [ ] O cabeçalho Host define quais campos devem ser obrigatórios em um formulário enviado via POST.
    
- Resposta:
    
    O cabeçalho Content-Type indica o formato dos dados enviados no corpo da requisição, como application/json.
    
    O cabeçalho Authorization é usado para enviar tokens de autenticação, como Bearer tokens em APIs REST.
    
    O cabeçalho Accept é usado pelo cliente para indicar qual formato deseja receber na resposta, como JSON ou XML.
    

**17. Padrões de Projeto são soluções reutilizáveis? Assinale todas as alternativas corretas sobre os Padrões de Projeto e suas classificações:**

Escolha uma ou mais:

- [ ] Padrões de Projeto são soluções genéricas que ajudam a resolver problemas comuns de arquitetura e design de software.
- [ ] Padrões criacionais estão relacionados à forma como objetos são instanciados, como Singleton e Factory Method.
- [ ] Um padrão de projeto define a implementação exata e obrigatória que o desenvolvedor deve seguir.
- [ ] Padrões de Projeto só se aplicam em projetos grandes e com muitos desenvolvedores.
- [ ] Os padrões de projeto são geralmente organizados em três categorias: criacionais, estruturais e comportamentais.
- Resposta:
    - Padrões de Projeto são soluções genéricas que ajudam a resolver problemas comuns de arquitetura e design de software.
    - Padrões criacionais estão relacionados à forma como objetos são instanciados, como Singleton e Factory Method.
    - Os padrões de projeto são geralmente organizados em três categorias: criacionais, estruturais e comportamentais.

**18. Sobre o uso de Service no Spring Boot e as anotações do framework, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] O Spring exige que as Services sejam instanciadas manualmente usando a palavra-chave new.
    
- [ ] Classes anotadas com @Service são, por padrão, beans singleton no Spring.
    
- [ ] A injeção de dependência em Services pode ser feita via construtor, sendo essa a abordagem mais recomendada.
    
- [ ] Para que o Spring reconheça uma classe como Service, é obrigatório criar um arquivo XML de configuração manual.
    
- [ ] A anotação @Service registra a classe no contexto do Spring para ser gerenciada como um bean.
    
- Resposta:
    
    Classes anotadas com @Service são, por padrão, beans singleton no Spring.
    
    A injeção de dependência em Services pode ser feita via construtor, sendo essa a abordagem mais recomendada.
    
    A anotação @Service registra a classe no contexto do Spring para ser gerenciada como um bean.
    

**19. Considere as seguintes afirmações sobre a camada Service em uma aplicação Spring Boot. Assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] a. A camada Service deve conter apenas chamadas de banco de dados e não pode conter nenhuma lógica de negócio.
    
- [ ] b. A camada Service deve conter regras de negócio e orquestrar chamadas para outras camadas, como repositórios e APIs externas.
    
- [ ] c. A camada Service é responsável por receber requisições HTTP diretamente dos clientes e encaminhá-las para o Repository.
    
- [ ] d. Uma classe Service pode depender de outras classes Service para organizar melhor responsabilidades.
    
- [ ] e. É uma boa prática anotar as classes da camada Service com @Service para que o Spring as registre como beans gerenciados.
    
- Resposta:
    
    A camada Service deve conter regras de negócio e orquestrar chamadas para outras camadas, como repositórios e APIs externas.
    
    Uma classe Service pode depender de outras classes Service para organizar melhor responsabilidades.
    
    É uma boa prática anotar as classes da camada Service com @Service para que o Spring as registre como beans gerenciados.
    

**20. É considerado boa prática que um Controller acesse diretamente o banco de dados usando Repositories.**

- [ ] Verdadeiro
    
- [ ] Falso
    
- Resposta:
    
    Falso
    

**21. O padrão Strategy permite que um objeto altere seu comportamento em tempo de execução, ao trocar dinamicamente a estratégia utilizada.**

- [ ] Verdadeiro
    
- [ ] Falso
    
- Resposta:
    
    Verdadeiro
    

**22. Repositórios definidos como interfaces que estendem JpaRepository são, por padrão, gerenciados como beans singleton pelo Spring.**

- [ ] Verdadeiro
    
- [ ] Falso
    
- Resposta:
    
    Verdadeiro
    

**23. Sobre JPQL (Java Persistence Query Language), assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] JPQL permite o uso de alias para entidades na cláusula FROM, facilitando a escrita e leitura de consultas.
    
- [ ] JPQL permite usar SELECT * para retornar todos os dados de uma entidade.
    
- [ ] Em JPQL, usamos os nomes das entidades Java e seus atributos, e não os nomes das tabelas e colunas do banco de dados.
    
- [ ] Em JPQL, joins são realizados entre tabelas diretamente, como em SQL tradicional.
    
- [ ] É possível usar funções específicas de banco de dados como NOW() diretamente em JPQL sem adaptações.
    
- Resposta:
    
    JPQL permite o uso de alias para entidades na cláusula FROM, facilitando a escrita e leitura de consultas.
    
    Em JPQL, usamos os nomes das entidades Java e seus atributos, e não os nomes das tabelas e colunas do banco de dados.
    

**24. Em qualquer requisição HTTP válida, alguns componentes são obrigatórios e formam a estrutura mínima da requisição. Assinale todos os componentes que estão presentes em toda requisição HTTP:**

Escolha uma ou mais:

- [ ] O método HTTP (como GET, POST, etc.), que define qual ação será executada no recurso.
    
- [ ] Cabeçalhos HTTP mínimos, como o cabeçalho Host, que identifica o servidor de destino.
    
- [ ] O caminho (URL) para o recurso que está sendo solicitado.
    
- [ ] O corpo da requisição (body), onde os dados são enviados.
    
- [ ] Parâmetros de requisição, como ?pagina=1, são obrigatórios em todas as requisições HTTP.
    
- Resposta:
    
    O método HTTP (como GET, POST, etc.), que define qual ação será executada no recurso.
    
    Cabeçalhos HTTP mínimos, como o cabeçalho Host, que identifica o servidor de destino.
    
    O caminho (URL) para o recurso que está sendo solicitado.
    

**25. É permitido e, em muitos casos, recomendado que uma classe Service chame outra classe Service quando há lógica de negócio compartilhada.**

- [ ] Verdadeiro
    
- [ ] Falso
    
- Resposta:
    
    Verdadeiro
    

**26. Um Controller no Spring Boot deve receber as requisições HTTP, validar os dados e delegar a lógica de negócio para a camada Service.**

- [ ] Verdadeiro
    
- [ ] Falso
    
- Resposta:
    
    Verdadeiro
    

**27. Considere a resposta abaixo, retornada por uma API REST após uma requisição:**

`HTTP/1.1 200 OK  
Content-Type: application/json  
Content-Length: 58

{  
"id": 101,  
"nome": "João",  
"email": "[joao@email.com](mailto:joao@email.com)"  
}`

Com base nessa resposta, assinale todas as afirmações corretas:

Escolha uma ou mais:

- [ ] Como o código 200 foi retornado, o corpo obrigatoriamente deve conter um token JWT para autenticação.
    
- [ ] O corpo da resposta contém os dados do recurso solicitado, no caso, um usuário com nome, e-mail e ID.
    
- [ ] O cabeçalho Content-Type informa que o corpo da resposta está no formato JSON.
    
- [ ] O código 200 OK indica que a requisição foi processada com sucesso.
    
- [ ] O cabeçalho Content-Length indica a quantidade de campos retornados no JSON.
    
- Resposta:
    
    O corpo da resposta contém os dados do recurso solicitado, no caso, um usuário com nome, e-mail e ID.
    
    O cabeçalho Content-Type informa que o corpo da resposta está no formato JSON.
    
    O código 200 OK indica que a requisição foi processada com sucesso.
    

**28. Um Controller pode receber instâncias de Services via injeção de dependência, seja por construtor ou com a anotação @Autowired.**

- [ ] Verdadeiro
    
- [ ] Falso
    
- Resposta:
    
    Verdadeiro
    

**29. Sobre DTOs, é correto afirmar:**

I. É o anagrama para Data Transfer Object. São classes criadas para não terem nenhuma regra complexa nelas. Basicamente possuem atributos e getters/setters.  
II. É um padrão de projetos que só existe em Java e só deve ser aplicado em projetos REST.  
III. Podemos usar anotações de validação em DTO's, como @NotBlank, @Min, @Past etc.  
IV. É apenas outro nome para as classes de Entidade, usadas para mapear as tabelas em classes. V. Serve para transferir dados, entre camadas da própria aplicação e/ou para outras aplicações.

- [ ] a. Apenas II, IV e V estão corretas.
    
- [ ] b. Apenas II, III e IV estão corretas.
    
- [ ] c. Apenas I, III e V estão corretas.
    
- [ ] d. Nenhuma das alternativas.
    
- [ ] e. Apenas I, II e V estão corretas.
    
- Resposta:
    
    Apenas I, III e V estão corretas.
    

**30. O padrão Singleton garante que uma classe tenha apenas uma instância em todo o sistema. No contexto do Spring Boot, assinale todas as alternativas corretas sobre o uso desse padrão:**

Escolha uma ou mais:

- [ ] Em aplicações Spring Boot, deve-se evitar beans singleton, pois eles não são thread-safe.
    
- [ ] Para que um bean seja singleton no Spring, é obrigatório usar variáveis estáticas e métodos sincronizados.
    
- [ ] O escopo padrão de um bean no Spring é singleton, ou seja, apenas uma instância é criada e compartilhada.
    
- [ ] O Spring Boot gerencia automaticamente os beans singleton, não sendo necessário implementar o padrão manualmente.
    
- [ ] É necessário criar uma instância manualmente com "new" e armazená-la em cache para simular o comportamento singleton no Spring.
    
- Resposta:
    
    O escopo padrão de um bean no Spring é singleton, ou seja, apenas uma instância é criada e compartilhada.
    
    O Spring Boot gerencia automaticamente os beans singleton, não sendo necessário implementar o padrão manualmente.
    

**31. Em APIs REST, o design das URLs (endpoints) deve seguir algumas boas práticas para manter a API semântica, padronizada e de fácil entendimento. Assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] É recomendado usar URLs como /getLivros ou /criarUsuario para deixar claro o que a API faz.
    
- [ ] As URLs em uma API REST devem usar substantivos no plural para representar coleções de recursos, como /livros ou /usuarios.
    
- [ ] Hierarquia entre recursos pode ser representada nas URLs, como em /usuarios/42/livros.
    
- [ ] Deve-se incluir o tipo de retorno na URL, como /livros.json ou /usuarios.xml.
    
- [ ] Evita-se o uso de verbos nas URLs, pois a ação é representada pelo método HTTP (GET, POST, etc.).
    
- Resposta:
    
    As URLs em uma API REST devem usar substantivos no plural para representar coleções de recursos, como /livros ou /usuarios.
    
    Hierarquia entre recursos pode ser representada nas URLs, como em /usuarios/42/livros.
    
    Evita-se o uso de verbos nas URLs, pois a ação é representada pelo método HTTP (GET, POST, etc.).
    

**32. Considere a entidade Livro com os seguintes atributos:**

Java

`public class Livro { private Long id; private String titulo; private String autor; private Integer anoPublicacao; }`

**Quais dos métodos abaixo seriam válidos para declarar em uma interface LivroRepository, utilizando Dynamic Finders do Spring Data JPA?**

Escolha uma ou mais:

- [ ] findLivroTitulo
    
- [ ] findByAutorOrderByAnoPublicacaoAsc
    
- [ ] findByTituloContainingIgnoreCase
    
- [ ] buscarPorAutorOrdenadoPorAno
    
- [ ] findByAnoPublicacaoBetween
    
- Resposta:
    
    findByAutorOrderByAnoPublicacaoAsc  
    findByTituloContainingIgnoreCase  
    findByAnoPublicacaoBetween
    

**33. Spring Data JPA permite retornar apenas campos específicos da entidade usando interfaces como projeções, sem a necessidade de escrever consultas manuais.**

- [ ] Verdadeiro
    
- [ ] Falso
    
- Resposta:
    
    Verdadeiro
    

**34. Sobre a integração dos Controllers com o Spring Framework, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] É possível injetar Services diretamente em Controllers usando a anotação @Autowired ou injeção via construtor.
    
- [ ] Controllers são beans gerenciados pelo Spring, detectados automaticamente via anotações como @RestController.
    
- [ ] Controllers precisam ser registrados manualmente no Spring via arquivos XML de configuração.
    
- [ ] Controllers podem delegar chamadas para Repositories indiretamente, utilizando Services como intermediários.
    
- [ ] Controllers devem ser criados como classes estáticas para permitir que o Spring as injete automaticamente.
    
- Resposta:
    
    É possível injetar Services diretamente em Controllers usando a anotação @Autowired ou injeção via construtor.  
    Controllers são beans gerenciados pelo Spring, detectados automaticamente via anotações como @RestController.  
    Controllers podem delegar chamadas para Repositories indiretamente, utilizando Services como intermediários.
    

**35. Associe cada descrição abaixo à anotação de validação (Bean Validation) correspondente.**

- [ ] O número inteiro deve ser menor ou igual a um valor:
    
- [ ] O número pode ser zero ou positivo:
    
- [ ] O número inteiro deve ser maior ou igual a um valor:
    
- [ ] O valor deve ser uma data no futuro:
    
- [ ] O campo deve ter tamanho dentro de um intervalo de caracteres:
    
- [ ] O valor deve obedecer a um formato definido por expressão regular:
    
- [ ] O campo deve conter um e-mail válido:
    
- [ ] O valor deve ser uma data no passado:
    
- [ ] O campo deve ser nulo (usado em campos controlados pelo sistema):
    
- [ ] O campo não pode ser vazio e deve conter caracteres visíveis:
    
- [ ] O número pode ser zero ou negativo:
    
- [ ] O número decimal deve ser maior ou igual a um valor mínimo:
    
- [ ] O número deve ser positivo (maior que zero):
    
- [ ] O campo não pode ser nulo:
    
- Resposta:
    
    O número inteiro deve ser menor ou igual a um valor: @Max  
    O número pode ser zero ou positivo: @PositiveOrZero  
    O número inteiro deve ser maior ou igual a um valor: @Min  
    O valor deve ser uma data no futuro: @Future  
    O campo deve ter tamanho dentro de um intervalo de caracteres: @Size  
    O valor deve obedecer a um formato definido por expressão regular: @Pattern  
    O campo deve conter um e-mail válido: @Email  
    O valor deve ser uma data no passado: @Past  
    O campo deve ser nulo (usado em campos controlados pelo sistema): @Null  
    O campo não pode ser vazio e deve conter caracteres visíveis: @NotBlank  
    O número pode ser zero ou negativo: @NegativeOrZero  
    O número decimal deve ser maior ou igual a um valor mínimo: @DecimalMin  
    O número deve ser positivo (maior que zero): @Positive  
    O campo não pode ser nulo: @NotNull
    

**36. Swagger é uma ferramenta amplamente utilizada para documentar e testar APIs REST. Com base nisso, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] Swagger só funciona se todas as classes da API estiverem anotadas com @RestController.
    
- [ ] Swagger/OpenAPI permite gerar uma documentação interativa que descreve os endpoints da API, métodos HTTP, parâmetros e respostas.
    
- [ ] Swagger substitui totalmente a necessidade de escrever testes automatizados na aplicação.
    
- [ ] Em projetos Spring Boot, é possível integrar Swagger utilizando bibliotecas como springdoc-openapi.
    
- [ ] Swagger é obrigatório em qualquer projeto REST que utiliza Spring Boot.
    
- Resposta:
    
    Swagger/OpenAPI permite gerar uma documentação interativa que descreve os endpoints da API, métodos HTTP, parâmetros e respostas.  
    Em projetos Spring Boot, é possível integrar Swagger utilizando bibliotecas como springdoc-openapi.
    

**37. Sobre o uso e papel da camada Controller em uma aplicação Spring Boot, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] Controllers em APIs REST geralmente são anotados com @RestController, que combina @Controller e @ResponseBody.
    
- [ ] O Controller atua como ponto de entrada da aplicação web, lidando com verbos HTTP como GET, POST, PUT e DELETE.
    
- [ ] Controllers devem conter toda a lógica de negócio, pois estão mais próximos do cliente.
    
- [ ] O Controller deve acessar diretamente o banco de dados para retornar as informações solicitadas.
    
- [ ] O Controller é responsável por lidar com requisições HTTP e delegar a lógica de negócio para a camada Service.
    
- Resposta:
    
    Controllers em APIs REST geralmente são anotados com @RestController, que combina @Controller e @ResponseBody.  
    O Controller atua como ponto de entrada da aplicação web, lidando com verbos HTTP como GET, POST, PUT e DELETE.  
    O Controller é responsável por lidar com requisições HTTP e delegar a lógica de negócio para a camada Service.
    

**38. Ao implementar autenticação em APIs REST, algumas práticas e códigos HTTP são utilizados de forma padronizada. Assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] Tokens opacos são preferíveis quando o cliente precisa acessar diretamente os dados do token, como permissões e ID do usuário.
    
- [ ] Ao realizar login com sucesso, a API pode retornar um código 200 OK e incluir um token no corpo da resposta.
    
- [ ] O código 403 Forbidden deve ser usado quando o login falha por usuário ou senha incorretos.
    
- [ ] O código 401 Unauthorized deve ser usado quando o usuário não fornece ou fornece um token de autenticação inválido.
    
- [ ] JWTs (JSON Web Tokens) são considerados tokens translúcidos, pois podem ser lidos e decodificados sem contato com o servidor.
    
- Resposta:
    
    Ao realizar login com sucesso, a API pode retornar um código 200 OK e incluir um token no corpo da resposta.  
    O código 401 Unauthorized deve ser usado quando o usuário não fornece ou fornece um token de autenticação inválido.  
    JWTs (JSON Web Tokens) são considerados tokens translúcidos, pois podem ser lidos e decodificados sem contato com o servidor.
    

**39. REST é um estilo arquitetural utilizado no desenvolvimento de APIs que se baseia em regras e restrições para promover simplicidade, escalabilidade e padronização. Assinale todas as alternativas corretas relacionadas a REST e sua utilização do protocolo HTTP:**

Escolha uma ou mais:

- [ ] Em REST, cada recurso deve ser identificado por uma URL única que o represente.
    
- [ ] Uma API RESTful deve obrigatoriamente retornar todos os dados da aplicação em uma única chamada.
    
- [ ] Em uma API REST, as operações são representadas por métodos HTTP como GET, POST, PUT e DELETE.
    
- [ ] APIs REST devem utilizar os códigos de status HTTP para informar o resultado das requisições, como 200, 201, 404, entre outros.
    
- [ ] REST é um padrão obrigatório definido por uma organização e deve seguir uma implementação oficial.
    
- Resposta:
    
    Em REST, cada recurso deve ser identificado por uma URL única que o represente.  
    Em uma API REST, as operações são representadas por métodos HTTP como GET, POST, PUT e DELETE.  
    APIs REST devem utilizar os códigos de status HTTP para informar o resultado das requisições, como 200, 201, 404, entre outros.
    

**40. Associe cada descrição abaixo ao código HTTP correto utilizado em APIs REST.**

- Recurso criado com sucesso, normalmente após uma operação POST:
    
- Requisição inválida, dados malformados ou parâmetros ausentes:
    
- Requisição bem-sucedida com retorno de conteúdo no corpo da resposta:
    
- Requisição processada com sucesso, mas sem corpo na resposta:
    
- Falha de autenticação, como token ausente ou inválido:
    
- Recurso solicitado não foi encontrado no servidor:
    
- Resposta:
    
    Recurso criado com sucesso, normalmente após uma operação POST: 201  
    Requisição inválida, dados malformados ou parâmetros ausentes: 400  
    Requisição bem-sucedida com retorno de conteúdo no corpo da resposta: 200  
    Requisição processada com sucesso, mas sem corpo na resposta: 204  
    Falha de autenticação, como token ausente ou inválido: 401  
    Recurso solicitado não foi encontrado no servidor: 404
    

**41. O padrão de projeto Adapter é utilizado para integrar classes com interfaces incompatíveis. Assinale todas as alternativas corretas sobre esse padrão:**

Escolha uma ou mais:

- [ ] DTOs podem ser vistos como uma forma simples de adaptação de dados entre camadas, apesar de não implementarem o padrão Adapter formalmente.
    
- [ ] O Adapter é útil para integrar bibliotecas ou APIs de terceiros sem precisar modificar seu código original.
    
- [ ] O padrão Adapter pertence à categoria de padrões comportamentais, pois lida com lógica de fluxo.
    
- [ ] O padrão Adapter converte a interface de uma classe para outra esperada pelo cliente, permitindo reutilização de código.
    
- [ ] Para aplicar o padrão Adapter, é necessário alterar diretamente a classe original para que ela implemente a nova interface.
    
- Resposta:
    
    DTOs podem ser vistos como uma forma simples de adaptação de dados entre camadas, apesar de não implementarem o padrão Adapter formalmente.  
    O Adapter é útil para integrar bibliotecas ou APIs de terceiros sem precisar modificar seu código original.  
    O padrão Adapter converte a interface de uma classe para outra esperada pelo cliente, permitindo reutilização de código.
    

**42. Os códigos da família 2xx indicam que a requisição foi bem-sucedida. Sobre o uso desses códigos em APIs REST, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] O código 201 Created é utilizado após a criação bem-sucedida de um recurso, geralmente via POST.
    
- [ ] O código 200 OK é adequado para indicar que o recurso solicitado não existe.
    
- [ ] O código 200 OK indica que a requisição foi processada com sucesso e o corpo da resposta contém dados.
    
- [ ] O código 204 No Content deve ser usado quando a operação foi bem-sucedida, mas não há conteúdo para retornar.
    
- [ ] O código 202 Accepted indica que o recurso foi criado com sucesso e já pode ser usado.
    
- Resposta:
    
    O código 201 Created é utilizado após a criação bem-sucedida de um recurso, geralmente via POST.  
    O código 200 OK indica que a requisição foi processada com sucesso e o corpo da resposta contém dados.  
    O código 204 No Content deve ser usado quando a operação foi bem-sucedida, mas não há conteúdo para retornar.
    

**43. Sobre funcionalidades avançadas da camada Repository com Spring Data JPA, assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] A anotação @Query pode ser usada para definir consultas JPQL diretamente em métodos do Repository.
    
- [ ] Repositories não suportam paginação ou ordenação nativamente.
    
- [ ] É possível executar queries SQL nativas em um Repository utilizando @Query com o atributo `nativeQuery = true`.
    
- [ ] É possível retornar apenas partes da entidade ou projeções customizadas usando interfaces ou DTOs nos métodos do Repository.
    
- [ ] Todos os métodos customizados devem ser implementados manualmente dentro de uma classe concreta, não sendo possível usar anotações.
    
- Resposta:
    
    A anotação @Query pode ser usada para definir consultas JPQL diretamente em métodos do Repository.  
    É possível executar queries SQL nativas em um Repository utilizando @Query com o atributo nativeQuery = true.  
    É possível retornar apenas partes da entidade ou projeções customizadas usando interfaces ou DTOs nos métodos do Repository.
    

**44. Considere as afirmações abaixo sobre a camada Repository em uma aplicação Spring Boot utilizando Spring Data JPA. Assinale todas as alternativas corretas:**

Escolha uma ou mais:

- [ ] Repositories devem conter lógica de negócio e regras específicas da aplicação.
    
- [ ] É possível criar métodos de consulta personalizados apenas seguindo convenções de nomes, como `findByEmail`.
    
- [ ] Em Spring Boot, Repositories são definidos como interfaces que estendem `JpaRepository` ou outras interfaces do Spring Data.
    
- [ ] É necessário implementar manualmente todos os métodos de CRUD em uma interface Repository.
    
- [ ] Repositories são normalmente injetados nas Services para realizar operações de persistência.
    
- Resposta:
    
    É possível criar métodos de consulta personalizados apenas seguindo convenções de nomes, como findByEmail.  
    Em Spring Boot, Repositories são definidos como interfaces que estendem JpaRepository ou outras interfaces do Spring Data.  
    Repositories são normalmente injetados nas Services para realizar operações de persistência.
    

**45. O padrão de projeto Observer é usado para criar um sistema de notificação automática entre objetos. Assinale todas as alternativas corretas sobre esse padrão:**

Escolha uma ou mais:

- [ ] O padrão Observer é considerado um padrão estrutural, pois define a organização das classes.
    
- [ ] O padrão depende de verificação constante (polling) pelos observadores para detectar mudanças no estado.
    
- [ ] O padrão Observer permite que um objeto notifique automaticamente uma lista de outros objetos quando seu estado muda.
    
- [ ] Esse padrão reduz o acoplamento entre quem gera um evento e quem responde a ele.
    
- [ ] Todos os observadores devem executar exatamente a mesma ação ao serem notificados.
    
- Resposta:
    
    O padrão Observer permite que um objeto notifique automaticamente uma lista de outros objetos quando seu estado muda.  
    Esse padrão reduz o acoplamento entre quem gera um evento e quem responde a ele.
