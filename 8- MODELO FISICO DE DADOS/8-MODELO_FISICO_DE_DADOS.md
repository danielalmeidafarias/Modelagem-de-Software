# Modelo Físico de Dados
- Transformar as entidades em tabelas com colunas e os tipos de dados, ultilizando SQL;

* Última etapa do projeto de Banco de Dados;
* Expressa como as informações serão armazenadas fisicamente;
* Como as informações de relacionarão com sistemas externos;

* Esquema de Banco de Dados
    - Descreve os conceitos (entidades e atributos) e relacionamentos do minimundo;

## SQL -> Structed Query Language

* Categorias da linguagem SQL:
    - DDL - _Data Definition Language_;
    - DML - _Data Manipulation Language_;
    - TCL - _Transact Control Language_;
    - DCL - _Data Control Language_;


### Data Definition Language (DDL)
*  São inciado com as palavras reservadas:
    - CREATE;
    - ALTER;
    - DROP;
    - TRUNCATE;
    - RENAME;
    - FLASHBACK;
    - COMMENT;

* Os principais objetos são:
    - TABLE;
    - VIEW;
    - SEQUENCE;
    - SYNONYM;
    - INDEX;
    - etc;

#### Tabelas

- Local lógico onde são armazenados os dados, formado por colunas e linhas;
- É preciso especificar o **tipo do dado**;

|  *Tipo*  |                          *Descrição*                                 |   *Tamanho máximo*   | *Exemplo*  
|----------|----------------------------------------------------------------------|----------------------|------------------
|CHAR()    | Alfanumérico de tamanho fixo                                         |2000 bytes(caracteres)| unidade_federativa
|----------|----------------------------------------------------------------------|----------------------|------------------
|VARCHAR() | Alfanumérico. O que não for usado não ocupa espaço no banco de dados |4000 bytes caracteres)| endereco_aluno
|----------|----------------------------------------------------------------------|----------------------|-------------------
|LONG      | Alfanumérico. Tamanho não precisa ser informado. Só pode existir um  |   2 Giga bytes       | curriculo_professor
|          | por tabela e não pode ser utilizado em consultas.                    |   (caracteres)       |
|----------|----------------------------------------------------------------------|----------------------|-------------------
|DATE      | Data: século, ano, mês, dia, minuto e segundo                        |                      | data_nascimento
|----------|----------------------------------------------------------------------|----------------------|-------------------
|NUMBER()  | Numérico. Utilizado com casas decimais, primeiro o número total de   |         38           | valor_produto
|          | dígitos (incluindo as casas decimais (escala opcional))              |                      |
|----------|----------------------------------------------------------------------|----------------------|-------------------
|INTEGER   | Números inteiros. Não aceita limitação de tamanho do campo           |         38           | idade_funcionario


##### Criar tabela (CREATE TABLE)

    CREATE TABLE   nome_da_tabela
    (nome_da_coluna   tipo_de_dado1   [(tamanho)]   [restrições],
     nome_da_coluna   tipo_de_dado2   [(tamanho)]   [restrições]..);


##### Restrições de tabelas (CONSTRAINS)

| *Tipo de restrição* |                    *Sintaxe*
|---------------------|----------------------------------------------------
|      DEFAULT        | coluna tipo-de-dado(tamanho)DEFAULT valor padrão;
|---------------------|-----------------------------------------------------
|    PRIMARY KEY      | coluna tipo-de-dado(tamanho) PRIMARY KEY;
|                     |            OU
|                     | CONSTRAINT nome_pk PRIMARY KEY (coluna,colunan);
|---------------------|------------------------------------------------------
|    FOREIGN KEY      | CONSTRAINT nome_fk FOREIGN KEY (nome_coluna) REFERENCES nome_tabela (nome_coluna_chave_primária);
|---------------------|------------------------------------------------------
|       CHECK         | CONSTRAINT nome_ch CHECK (coluna possíveis valores);
|---------------------|--------------------------------------------------------
|      NOT NULL       | coluna tipo-dado NOT NULL;
|---------------------|--------------------------------------------------------
|       UNIQUE        | CONSTRAINT nome_uk UNIQUE(coluna);]


##### Visualizar a estrutura de uma tabela
- A instrução *DESC* ou *DESCRIBE* exibe o nome das colunas, as restrições, tipo de dados, valor padrão, comentários e
 quantidade de caracteres de cada coluna 

 - Sintaxe:
    DESCRIBE nome_tabela;


##### Alterar tabelas (ALTER TABLE)

1. Adicionar colunas
    ALTER TABLE   nome-da-tabela
    ADD   (nome-da-coluna tipo-de-dado   [(tamanho)]);

2. Modificar colunas
    ALTER TABLE   nome-da-tabela
    MODIFY   (nome-da-coluna    tipo-de-dado   [(tamanho)]);

3. Renomear colunas
    ALTER TABLE   nome-da-coluna
    RENAME COLUMN   coluna_antiga   TO   coluna_nova;

4. Excluir colunas
    ALTER TABLE   nome-da-tabela
    DROP COLUMN   (nome-da-coluna);

5. Adicionar restrições
    ALTER TABLE   nome-da-coluna
    ADD CONSTRAINT   nome-constraint   tipo-constraint   (campo-constraint);


##### Truncar tabela (TRUNCATE TABLE)
- O comando TRUNCATE TABLE remove todas as linhas de uma tabela, liberando o espaço de armazenamento usado por ela

    TRUNCATE TABLE   nome-da-tabela;

##### Renomear tabela (RENAME)

    RENAME   nome_tabela_atual   TO   nova_tabela;

##### Excluir tabela (DROP TABLE)

    DROP TABLE   nome-da-tabela;
    DROP TABLE   nome-da-tabela   PURGE;

##### Recuperar tabela (FLASHBACK TABLE)

    FLASHBACK TABLE   esquema.nome_tabela   TO   BEFORE DROP

* A recyclebin é a lixeira onde ficam os objetos com seus registros excluídos. Para consultar a recyclebin:
    
        SELECT original_name, operation, droptime FROM recyclebin

        PURGE RECYCLEBIN

##### Informações dos objetos no banco de dados
- Objetos pertencentes ao usuário logado

    SELECT   *   FROM   USER_OBJECT;

    * Pode ultilizar o prefixo ALL para exibir todos os objetos do banco de dados

    * Nome das tabelas existentes neste usuário: 
        
        SELECT table_name FROM USER_TABLES;

    * Informações detalhadas das colunas de suas tabelas:
        
        SELECT  *  FROM  USER_TAB_COLUMNS;

##### Comentários

    COMMENT ON TABLE   nome_tabela   IS   'texto'

    COMMENT ON COLUMN nome_tabela.nome_coluna  IS ‘texto’;

    SELECT * FROM <nome da view do dicionário de dados>;

### Data Manipulation Language (DML)
- Adicionar novas linhas a uma tabela;
- Modifica linhas existentes em uma tabela;
- Remove linhas existentes de uma tabela;

* São iniciados com as palavras reservadas:
    - INSERT
    - DELETE
    - UPDATE
    - MERGE
    - SELECT

#### Inserir registros (INSERT INTO)
- Permite inserir registros em tabelas

    INSERT INTO   tabela [(coluna), (coluna1), ...]   VALUES (valor, valor1, ...);

#### Atualizar registros (UPDATE)
- Modifica linhas existentes (mais de uma linha por vez)

    UPDATE   tabela
        SET   coluna = valor,   [coluna1 = valor2, ...]
    [WHERE   condição]

#### Excluir registro (DELETE)

    DELETE   FROM   tabela
    [WHERE   condição];

#### Inserção e atualização de registros (MERGE)
- Atualizar ou inserir uma llinha _condicionalmente_ (ON) em uma tabela
- Combina o INSERT e o UPDATE

    MERGE INTO tabela apelido_tabela
        USING (tabela|view|subconsulta) apelido
            ON (condição_junção)
        WHEN MATCHED THEN
        UPDATE SET coluna1 = valor1, coluna2 = valor2,...
        WHEN NOT MATCHED THEN
    INSERT (coluna1, coluna2)     VALUES (valor1, valor2,...);

### Data Transaction Language (DLT)
- Conjunto de operações que caracterizam uma trannsformação no banco de dados
- Deve atender as características conhecidas pela sigla ACID:
    * Atomicidade
    * Consistência
    * Isolamento
    * Durabilidade

* Usam as palavras reservadas:
    - COMMIT
        - Confirmação dos comandos DML
    - ROLLBACK
        - Cancelamentos dos comandos DML
    - SAVEPOINT
        - Marca um ponto de salvamento

### Recuperação de dados (comando SELECT)
- O comando SELECT permite a seleção e a manipulação, para vizualizar as informações no banco de dados

    SELECT   [DISTINCT]  {*, coluna [apelido],..}
        FROM   tabela;

- Com esse comando, é possivel exibir:


    |         *Tipo*         |               *Descrição*
    |------------------------|--------------------------------------------------------
    |           *            | Todas as colunas da tabela.
    |------------------------|--------------------------------------------------------
    |    Colunas (campos)    | Os nomes das colunas devem ser separados por vírgulas.
    |      específicos       |
    |------------------------|----------------------------------------------------------
    |      Colunas com       | O apelido (título) que se deseja dar a uma coluna ou expressão
    |    apelidos (alias)    | deve aparecer logo após, delimitado por aspas duplas ('').
    |------------------------|------------------------------------------------------------
    |  Colunas concatenadas  | Colunas que terão seu resultado concatenado (unido). O operador
    |                        | (||) é o responsável por essa funcionalidade.
    |------------------------|-------------------------------------------------------------
    |                        | Qualquer valor fixo que se deseje apresentar. Pode ou não ser
    |        Constante       | acompanhado por alias. Para valores alfanuméricos e do tipo data,
    |                        | devem ser delimitados por aspas simples (').
    |------------------------|----------------------------------------------------------------
    |       DISTINCT         | Linhas duplicadas apareçam somente uma vez
    |------------------------|------------------------------------------------------------------
    | Expressões aritméticas | Podem ser compostas por colunas das tabelas, constantes, funções,
    |                        | operadores aritméticos (+, -, / e *)


#### Operadores

1. Operadores Aritméticos
    - *, /, +, -

2. Operadores de Comparação:
                  
    |    =     | Igual a                             | <> ou != ou ^= | Diferente de 
    |----------|------------------------             |----------------|---------------------- 
    |    >     | Maior do que                        | BETWEEN...AND  | Entre dois valores
    |----------|------------------------             |----------------|----------------------
    |   >=     | Maior do que ou igual a             |  IN (lista)    | Lista de valores
    |----------|--------------------------           |----------------|----------------------
    |    <     | Menor do que                        |      LIKE      | Padrão de caracteres
    |----------|--------------------------           |----------------|-----------------------
    |   <=     | Menor do que ou igual a             |    IS NULL     | É um valor nulo


3. Operadores lógicos

    |   AND   | Retorna valor TRUE se as condições de componentes forem TRUE
    |---------|---------------------------------------------------------------------
    |   OR    | Retorna TRUE se pelo menos uma das condições de componente for TRUE
    |---------|---------------------------------------------------------------------
    |   NOT   | Retorna TRUE se a condição seguinte for FALSE

4. Operadores de Concatenação
    - O operador de concatenação concatena duas colunas ou strings a outras colunas
    - É representado por duas barras verticais (||)
    - Cria uma coluna resultante

* String literal de caracteres

    SELECT   coluna   || 'literal' ||  coluna   FROM   tabela;

#### Restringindo e classificando dados (seleção)

* O comando SELECT possui, ainda, cláusulas distintas: WHERE, ORDER BY, GROUP BY e HAVING,
  que podem ser utilizados com operadores: lógicos, artiméticos e de comparação.
  
* Where
    - A cláusula Whete restringe as linhas retornadas
    - Sempre segue a condição FROM
    - Quando há mais de uma condição, usa os operadores OR e AND

        SELECT [DISTINCT]  {*| coluna [apelido] ...}
            FROM   tabela
        WHERE   condição};

* Order by
    - ASC - ordem crescente (default), não precisa ser acrecentada;
    - DESC - ordem decrescente;
