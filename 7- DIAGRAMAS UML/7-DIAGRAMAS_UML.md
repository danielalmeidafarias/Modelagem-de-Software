# Diagramas UML
- Desenho da "planta" do sistema
- Visão orientada a objetos

## Diagrama de Casos de Uso
- Especificar requisitos funcionais
- Especificar o comportamento que cada parte do sistema deve ter
- Etapa de Planejamento e Análise

### Notação do Diagrama de Casos de Uso

* Caso de Uso
    - __ELIPSE com o caso de uso dentro__
    - Conjunto de ações que o sistema realiza para produzir um resultado para um ator

* Ator
    - __Boneco__
    - "Alguém" ou "Alguma coisa" que não faz parte do sistema, mas que interage com ele
    - O papel executado por alguém

* Associação
    - __Seta com a ponta preenchida__
    - Relacionamento entre um _ator_ e o _caso de uso_

#### Notação complementar do diagrama

* Relacionamento entre atores
    * Generalizaçao
        - __Seta com a ponta vazia__
    
* Relacionamento entre casos de uso
    * Generalização
        - __Seta vazia__

    * Inclusão (<<include>>)
        - __Seta com corpo pontilhado__

    * Extensão (<<extend>>)
        - __Seta com corpo pontilhado__
     
### Passo a passo para a elaboração de um Diagrama de Casos de Uso

1. Identificação dos atores
    - Listar os possíveis usuários diretos do sistema, os sistemas externos e hardwares específicos

2. Identificação dos casos de uso
    - Listar os possíveis __objetos__ do sistema

3. Associação entre atores e casos de uso
    - Elaboração do diagrama. Deve-se verificar se cada ator possui, pelo menos, uma associação com um caso de uso e vice versa

### Descrição do Diagrama de Casos de Uso
- Além da notação gráfica, deve possuir um detalhamento do diagrama

    - Catálogo de atores
    - Nomes do caso de uso
    - Breve descrição do caso de uso
    - Fluxo básico (passo a passo do caso de uso)
    - Fluxos alternativos
    - Pré-condições
    - Pós-condições



## Diagrama de Classes
- Propor a estrutura do sistema
- Auxiliar na definição de componentes e na implementação
- Etapa de Análise e/ou Projeto

    * Diagrama de Classes de Análise
        - Classes de negócio do sistema
        - Primeiro modelo conceitual. Não se preocupa com particularidades da linguagem

    * Diagrama de Classes de Projeto
        - Classes de negócio e de implementação
        - Realização dos casos de uso

### Notação Básica do Diagrama de Classes

                 CLASSE                  X           OBJETO
        - representa algo no mundo real     - Ocorrência de uma classe
        - define as características e       - Criado durante a execução do
         comportamento dos objetos            sistema


|           | - Conjunto de objetos que possuem características e comportamentos comuns;
|   CLASSE  | - Qualquer elemento que seja relevante dentro do domínio do problema
|           | - Iniciar com letra maiúscula e no singular;
|           | - Podem ter nomes compostos;
|-----------|------------------------------------------------------------------------------
|           | - Descrevem as características dos objetos;
| ATRIBUTOS | - Definem os dados que devem ser armazenados;
|           | - Informações que uma classe deve ter em si mesma;
|-----------|------------------------------------------------------------------------------
|           | - Realizar ações e manipular atributos;
|  MÉTODOS  | - Pertencem às classes e somente podem ser aplicados aos objetos da classe;
|           | - Definem os serviçoes da classe;


* Relacionamentos
- Conexão entre classes: interações

    * Associação
        * __FLECHA SIMPLES  __
        - conexão entre classes
        - normalmente é bidirecional
        - possui nome (usualmente um verbo) escrito próximo à linha de associação
        - deve ser representado a cardialidade

    * Agregação
        * __FLECHA COM TRIANGULO VAZIO_
        - uma ou mais classes fazem parte de uma outra classe
        - as partes são independentes

    * Composição
        * __FLECHA COM TRIANGULO PREENCHIDO__
        - agregação que uma parte depende de outra

    * Generalização
        * __FLECHAS PREENCHIDAS COM PONTILHADO__
        - relação entre grupos de "coisas"

    * Dependência
        * __FLECHA SIMPLES COM PONTILHADO__
        - uma classe utiliza atributos de operações de outra classe

### Elaboração do Diagrama de Classes

1. Identificação das classes
    - Identificação
    - Classificação
    - Avaliação
    - Esboço

2. Identificação de Associações entre classes
    - Associações
    - Cardialidades
    - Hierarquia de generalização (herança)

3. Identificação de Atributos e Operações
    - Baseado nas responsabilidades


## Diagramas de Interação
- Modelam o comportamento dinâmico dos objetos
- Realização de um caso de uso

* Diagrama de Sequência
- Como os objetos interagem e se comunicam
- Troca de mensagens entre objetos
- Ênfase na ordem temporal

* Diagrama de Colaboração (comunicação)
- Ênfase na organização estrutural dos objetos

### Notação do Diagrama de Interação

* Atores
    * __BONECO__
    - Agentes externos que realizam interações com o sistema

* Objeto
    - __RETANGULO com o nome do objeto e da classe, separados por dois pontos__
    - Instâncias de uma classe

* Especificação da execução
    
    * Linha de vida
        * __PONTILHADO__
        - Representa a existência do objeto em um período de tempos

    * Ativação  
        * __BLOCO__
        - É o estímulo recebido pelo objeto e pela ação realizada

* Mensagens

    * __SETA COM PONTA CHEIA__
        - Chamada de procedimento (operação/método)
        - Objeto concorente que envia um sinal e aguarda o fim da execução das atividades

    * __SETA COM PONTA ABERTA__
        - Mensagem assíncrona entre os objetos

    * __SETA COM LINHA INTERROMPIDA__
        - Retorno de uma chamada de procedimento

### Construção do Diagrama de Interação

1. Definição
    - O cenário que irá representar

2. Identificação
    - Quais objetos participarão

3. Alinhamento
    - Objetos que iniciam a interação à esquerda e os demais à direita

4. Ordenação
    - As mensagens enviadas na ordem crescente de tempo, de cima para baixo

5. Importância
    - Coloque as mensagens de retorno relevantes para o cenário

## Diagrama de Atividade
- Ilustra graficamente como será o funcionamento do software
- Demonstra o fluxo de atividades em um único processo

### Notação Diagrama de Atividade

* Estado inicial
    - __CAIXA com o nome + CIRCULO FECHADO E SETA__
    - Indica o local de inicio do diagrama
    - Obrigatório e único no diagrama

* Estado final
    - __CIRCULO FECHADO__
    - Indica o fim do diagrama
    - Opcional

* Transição
    - __SETAS indicando a direção__
    - Quando uma atividade está completa, o fluxo (transições) passa para a atividade seguinte

* Ramificações
    - __LOSANGO com setas indicando a origem de entrada e a direção das saidas__
    - São caminhos alternativos de um fluxo
    - Uma transição de entrada e duas ou mais de saída

* Bifurcação
    - __BLOCOS RETANGULARES__
    - Divisão de um mesmo fluxo em dois ou mais
    - Uma única transição de entrada e duas ou mais de saída

* União 
    - __BLOCOS RETANGULARES__
    - Sincronização de dois ou mais fluxos
    - Duas ou mais entradas e uma única transição de saída

* Raias
    - __"CAIXAS" para separas os fluxos__
    - Particiona as atividades em grupos
