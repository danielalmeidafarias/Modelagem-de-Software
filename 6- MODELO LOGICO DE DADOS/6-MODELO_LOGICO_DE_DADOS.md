# Modelo Lógico de Dados
* Adequar o modelo conceitual a uma abordagem de Banco de dados
* Modelo Relacional de Dados

## Notação Engenharia de Informações

### Entidade
* Coisa ou objeto, real ou abstrato, no mundo real, com existência independente

* Classificação
    - Primária (forte)
    - Dependente (fraca)
    - Associativo
    - Categoria

### Atributo
* Propriedades que descrevem entidades
* Elemento mais estável em um SGBD (Sistema Gerenciado de Banco de Dados)

* Classificação
    - Natural
    - Calculado (derivado)
    - Artificial

* Atributo de Identificação
    - Chave primária
    - Chave secundária
    - Chava candidata
    - Chave alternativa
    - Super chave
    - Chave composta (concatenada)

### Tupla
* São linhas de entidades
    * Uma entidade é um conjunto de tuplas

### Relacionamento
* Estabele uma relação ou associação entre entidades

* São __SETAS__ que indicam a direção da atividade
    * Ida (voz ativa)
    * Volta (voz passiva)

* Classificação
    - simétrico
    - recursivo
    - condicional
    - normal

* Grau de relacionamento]
    - Quantidade de entidades participantes

### Cardialidade
* Quantificação de um relacionamento

### Dicionário de dados
* Transferir os dados entre os processo
* Descrição das entidades e atributos do projeto
    - Definição dos elementos de dados
    - Perfís de usuário
    - Papéis e privilégios
    - Descrição dos objetos
    - Restrições de integridade

* Nomeclaturqa do Dicionário de Dados

    | Notação |                              Descrição
    |---------|-------------------------------------------------------------------------
    |    =    | Dicionário de dados é composto de (um conjunto de elementos de dados).
    |---------|--------------------------------------------------------------------------
    |   ( )   | Opcional (atributo que não é obrigatório o preenchimento).
    |---------|--------------------------------------------------------------------------
    |   [/]   | Ou (será preenchido um atributo ou outro atributo).
    |---------|--------------------------------------------------------------------------
    |   { }   | Múltiplas ocorrências (1 a várias ocorrências). Quando o mesmo atributo 
    |         | aparece n vezes com tuplas diferentes.
    |---------|--------------------------------------------------------------------------
    |    @    | Indica que o elemento de dado é um atributo chave (caso não esteja no
    |         | protótipo não precisa acrecentar).
    |---------|--------------------------------------------------------------------------
    |    +    | E (concatenção, representa a união a partir do segundo elemento de dado). 
    |---------|--------------------------------------------------------------------------
    |  < / >  | E/ou, ocorre somente nenhum, um ou ambos os atributos preenchidos. 

### Relacionamentos de acordo com as cardialidades

* Relacionamento 1:1
    - Uma única tupla da primeira entidade se relaciona com uma tupla da segunda entidade

* Relacionamento 1:N
    - Sempre gera um atributo estrangeiro (chave estrangeira)

* Relacionamento autorrecursivo
    - Entidade se relaciona com ela mesma

* Relacionamento N:N (M:N)
    - Criaçaõ da Entidade de resolução

    * Mecanismos de Movimentação das cardialidades
        - Criação da Entidade De Resoluçaõ Associativa
        - Se movimentam para resolver o relacionamento do tipo M:N, garantindo assim, o sentido da leitura
        - As cardialidade das entidades-pai passam a ter cardialidade mínima e máxima de 1

### Normalização
* Processo matemático para verificar se as entidades de um banco de dados foram projetadas corretamente
* Estabilização e redução de manutenções
* teoria dos conjuntos
    * Modelo Relacional de Dados

    * Forma Normal
    - Conjunto de regras para verificar entidades relacionadas

        * (1FN) - Diz-se que uma tabela está na primeira __primeira forma normal__ quando ela não contém tabelas aninhadas.


        * Dependência funcional 
            - O valor de um atributo é definido pela relação com outro atributo, ou seja, o valor de um *depende* de outro.
        * Dependência parcial 
            - dependência funcional que ocorre quando um atributo depende apenas de parte de uma chave primária, composta ou concatenada
        * Dependência transitiva 
            - Ocorre quando um atributo, além de depender da chave primária da entidade, depende de outro atributo ou conjunto de atributos da entidade. 
       

        * (2FN) - A __segunda forma normal__ explica que uma entidade encontra-se na segunda formal normal quando, alem de estar da 1FN, não contém depêndencias parciais da chave primária

        * (3FN) - Uma entidade encontra-se na _terceira forma normal_ quando, além de estar na 3FN, não contém dependencias transitivas da chave primária ou composta

