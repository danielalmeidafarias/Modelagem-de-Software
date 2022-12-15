# Modelo Conceitual de Dados
* Mostrar o que precisa ser armazenado no banco de dados, suas características importantes e como se relacionam entre elas
* Modelo abstrato que descreve a estrutura do banco de dados
    - Entender o funcionamento de processos e regras de negócio
    - Expressar as necessidades de informações da empresa
    - Facilitar a comunicação entre usuários e desenvolvedores

## Diagrama Entidade Relacionamento

### 1. Entidades
- Representada com um __RETANGULO__

- Conjunto de um determinado tipo de informação
    - Objeto
    - Pessoa
    - Evento

    * Entidades fortes
        - Independem de outras entidades
    * Entidades fracas
        - Dependem de outras entidades. Individualmente não fazem sentido

### 2. Atributos
- Descrevem as características de uma entidade

    * Atributo simples
        - Representados por __ELIPSE__ ou __CIRCULO__

    * Atributo identificador
        - Representados por __ELIPSE com o nome sublinhado__ ou __CIRCULO preenchido__
            
    * Atributo multivalorado
        - __ELIPSE__ ou __CIRCULO__ com __cardialidade máxima e mínima__ ao lado do nome

    * Atributo composto
        - __ELIPE__ ou __CIRCULO__ __ligado a outros atributos__ por meio de relacionamentos

### 3. Relacionamentos
- Associação entre duas entidades
- Grau de um relacionamento: número de entidades participantes

    * Relacionamento binário
    * Relacionamento ternário
    * Relacionamentos recursivos (autorrelacionamentos)
            
### 4. Cardialidade
- Quantas ocorrências de uma entidade podem estar associadas a uma determinada ocorrência através do relacionamento

    * Cardialidade máxima
    * Cardialidade mínima

    * Relacionamento 1:1 e 1:N
        - Representado por um __LOSANGO__

    * Relacionamento N:N
        - Representado por um __LOSANDO dentro de um RETANGULO__

## Modelo estendido ou expandido
- Inclui os conceitos de __superclasse__ e __subclasse__

    * Especialização
        - Definir um conjunto de subclasses de um tipo de entidade, chamada de superclasse da especialização

    * Generalização
        - Definir um tipo de entidade generalizada, a partir de tipos de entidades fornecidas

    * Herança
        
        * TOTAL
            - Para cada entidade genérica existe sempre uma ocorrência na específica
        
        * PARCIAL
            - Nem toda ocorrência da entidade genérica possui uma ocorrência correspondente em uma entidade específica
        
        * COMPARTILHADA
            - Indica uma hierarquia, uma ocorrência da entidade genérica pode aparecer em várias entidades
            
        * Multipla
            - Ocorre quando uma mesma entidade é uma especialização de diversas entidades genéricas

