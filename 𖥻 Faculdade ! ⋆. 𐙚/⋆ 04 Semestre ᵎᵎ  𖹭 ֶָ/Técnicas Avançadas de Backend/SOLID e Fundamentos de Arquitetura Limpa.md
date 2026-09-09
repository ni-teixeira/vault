---
date:
tags:
  - faculdade
  - tecnicas-avancadas-de-backend
  - arquitetura-de-software
  - solid
---
## **Análise dos Princípios SOLID**

O acrônimo SOLID representa cinco princípios fundamentais de design orientado a objetos:

|Sigla|Princípio|Descrição Concisa|
|---|---|---|
|**S**|_Single Responsibility Principle_|Uma classe deve ter apenas um motivo para mudar.|
|**O**|_Open/Closed Principle_|Aberto para extensão, fechado para modificação.|
|**L**|_Liskov Substitution Principle_|Subtipos devem ser substituíveis por seus tipos base.|
|**I**|_Interface Segregation Principle_|Não forçar dependência em interfaces não utilizadas.|
|**D**|_Dependency Inversion Principle_|Depender de abstrações, não de implementações.|

### **1. Princípio da Responsabilidade Única (SRP)**

Cada classe deve possuir uma única responsabilidade clara dentro do sistema.

- **Identificação de Atores:** Um "ator" é qualquer pessoa, grupo ou sistema que solicita uma alteração no software. Se múltiplos atores (ex: Garçom, Operador de Caixa, Sistema de Persistência) solicitam mudanças na mesma classe, o SRP está sendo violado.
- **Impactos da Violação:**
    - Dificuldade em realizar testes unitários.
    - Dificuldade no reuso de componentes.
    - Alterações em um layout de recibo ou banco de dados acabam impactando a lógica de negócio principal.
- **Solução:** Separar as responsabilidades em classes distintas. Uma classe de orquestração pode gerenciar o fluxo, mas não deve deter as regras específicas de cada processo.

### **2. Princípio do Aberto/Fechado (OCP)**

O comportamento de um sistema deve ser extensível sem a necessidade de modificar o código fonte original.

- **Violando o OCP:** Quando a adição de um novo tipo de produto ou regra exige a modificação de uma classe existente.
- **Aplicando o OCP:** O design deve permitir que novas regras sejam adicionadas sem alterar a lógica base, geralmente através de abstrações.

### **3. Princípio da Substituição de Liskov (LSP)**

Os subtipos devem poder ser usados no lugar de seus tipos base sem que o comportamento esperado seja quebrado ou o contrato seja violado.

- **O Caso Clássico (Retângulo vs. Quadrado):** Um `Quadrado` que herda de `Retângulo` pode violar o LSP se, ao alterar a altura, ele forçar a alteração da largura (comportamento típico de um quadrado, mas inesperado para um retângulo). Isso quebra o contrato da classe base.
- **Aplicação Correta:** Utilizar interfaces (ex: `Forma`) que garantam o comportamento esperado (como um método `getArea()`) sem forçar hierarquias de herança inadequadas.

### **4. Princípio da Segregação de Interface (ISP)**

Uma classe não deve ser forçada a implementar métodos de uma interface que ela não utiliza.

- **Contexto:** Ao criar interfaces genéricas demais, classes específicas (como um `BoloGelado`) podem ser forçadas a implementar comportamentos irrelevantes para sua natureza.
- **Solução:** Isolar comportamentos em interfaces menores e específicas, separando as implementações.

### **5. Princípio da Inversão de Dependência (DIP)**

Módulos de alto nível não devem depender de módulos de baixo nível; ambos devem depender de abstrações.

- **Acoplamento:** Se um serviço (`PedidoService`) conhece detalhes de implementação de um repositório específico (como `MySQLPedidoRepository`), o código torna-se rígido.
- **Inversão:** Utilizar injeção de dependência via construtor. O serviço passa a depender de uma interface (`PedidoRepository`), permitindo que ele trabalhe com qualquer implementação futura sem necessidade de alteração.

---

## **Clean Architecture e Microserviços**

A aplicação dos princípios SOLID é um pré-requisito para a implementação da **Arquitetura Limpa**, especialmente em projetos de microserviços assíncronos.

### **Camadas da Clean Architecture**

O modelo organiza o sistema em círculos concêntricos onde as dependências apontam apenas para dentro:

1. **Entities (Núcleo):** Regras de negócio da empresa.
2. **Use Cases:** Regras de negócio da aplicação que expressam o comportamento do sistema.
3. **Interface Adapters:** Controladores, Gateways e Presenters que adaptam os dados entre o núcleo e o mundo externo.
4. **Frameworks & Drivers:** Camada mais externa contendo detalhes de infraestrutura como Bancos de Dados (DB), Interfaces Web, Dispositivos e Interface de Usuário (UI).

### **Diretrizes para Microserviços**

- **Independência:** Casos de uso devem ser o centro do sistema.
- **Intercambiabilidade:** A infraestrutura (como o tipo de banco de dados) deve ser separada da lógica de negócio e ser facilmente substituível.
- **Abstração:** O fluxo de controle entre Controladores, Interactors e Presenters deve sempre respeitar as fronteiras das camadas por meio de portas (Input/Output Ports) e abstrações.

---

## **Conclusão da Síntese**

A base fornecida pela Programação Orientada a Objetos (Encapsulamento, Herança, Polimorfismo e Abstração) é potencializada pelos princípios SOLID. Ao segui-los, evita-se a criação de códigos frágeis, reduz-se o acoplamento e aumenta-se a coesão, resultando em um software preparado para evoluções constantes e testes rigorosos.
