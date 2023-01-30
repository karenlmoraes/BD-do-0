# Criação de um Banco de Dados do 0
Colocando em prática o que foi aprendido em sala de aula sobre MySQL. Passo a passo completo de como criar e alimentar um banco de dados :)

1. Inicialize o aplicativo [Xampp](https://www.apachefriends.org/pt_br/index.html).
2. Clique em start nos campos Apache e MySQL.
3. Clique em Config no campo MySQL para iniciar.

![image](https://user-images.githubusercontent.com/112867913/215505035-c91b6d95-bf5e-47b6-b381-ecbd490910d8.png)

4. Clique em **SQL** e digite: ```CREATE DATABASE NOME_DO_BD```. O nome do nosso banco será **COLEGIO** 

>[*CREATE DATABASE COLEGIO*]

5. Clicando em continuar, você cria o banco.

![image](https://user-images.githubusercontent.com/112867913/215507299-397c38f5-6113-425c-ae0e-dc12a8c13b52.png)

> Todos os comandos a seguir, serão sempre inseridos nesse campo SQL (conforme imagem acima). Antes de inserir algum dado, se atente se está com o BD correto selecionado.

![image](https://user-images.githubusercontent.com/112867913/215508240-e4e7b167-92f0-46c8-afa8-3f42b4ac3e4d.png)

## Banco de dados Colégio

Antes de tudo, precisamos de dados para inserir no banco 🌛 Foi desenvolvido um modelo conceitual e lógico que você pode [conferir aqui](https://github.com/karenlmoraes/Banco-de-Dados). *A lista a seguir foi criada em sala de aula.* **PK:** Primary Key / Chave Primária | **FK:** Foreign Key / Chave Estrangeira. [Mais informações.](https://www.diegomacedo.com.br/entendendo-as-chaves-dos-bancos-de-dados/)

Nosso banco terá a seguinte estrutura: **Entidade - Atributos**

- **Curso** - cod_curso(PK), nome, tipo
- **Aluno** - cod_aluno(PK), cod_curso(FK), matrícula, nome, endereço, telefone
- **Turma** - cod_turma(PK), cod_disc(FK), cod_curso(FK), data_inicio
- **Disciplina** - cod_disc(PK), ementa, cont_prog, cod_prof(FK)
- **Professor** - cod_prof(PK), nome, sexo, especialidade


## Criação de tabelas

1. Para criação de tabelas, utilizaremos o comando: 

```
CREATE TABLE NOME_DA_TABELA(
  NOME_DO_ATRIBUTO INFORMAÇÕES,
  NOME_DO_ATRIBUTO INFORMAÇÕES,
  NOME_DO_ATRIBUTO INFORMAÇÕES
  )
```

2. Criaremos as tabelas curso, aluno, turma, disciplina e professor:

> **Atenção**, o último atributo não precisa de vírgula. Maiúsculas e minúsculas importam! Deixe tudo no mesmo padrão, Ex: Se começar as palavras com maiúscula, todos os nomes das entidades precisam começar assim também.

As tabelas precisam ser inseridas uma de cada vez. Todas as chaves primárias estão devidamente indicadas.

```
CREATE TABLE CURSO(
    Cod_Curso int not null PRIMARY KEY AUTO_INCREMENT,
    Nome varchar(100),
    Tipo varchar(100)
)

CREATE TABLE ALUNO(
    Cod_Aluno int not null PRIMARY KEY AUTO_INCREMENT,
    Cod_Curso int,
    Matrícula int,
    Nome varchar(100),
    Endereço varchar(150),
    Telefone int
)

CREATE TABLE TURMA(
    Cod_Turma int not null PRIMARY KEY AUTO_INCREMENT,
    Cod_Disc int,
    Cod_Curso int,
    Data_Inicio date
)

CREATE TABLE DISCIPLINA(
    Cod_Disc int not null PRIMARY KEY AUTO_INCREMENT,
    Ementa varchar(300),
    Cont_Prog varchar(200),
    Cod_Prof int
)

CREATE TABLE PROFESSOR(
    Cod_Prof int not null PRIMARY KEY AUTO_INCREMENT,
    Nome varchar(100),
    Sexo varchar(1),
    Especialidade varchar(150)
)
```

**Varchar:** Campo de palavras (número máximo de caracteres)

**Int:** Campo de números inteiros

**Date:** Refere-se a campo de data

**Not Null:** Significa que o campo precisa de algum valor, não pode ser vazio. Oposte de **null**

**Auto_Increment:** Significa que será incrementado automáticamente o valor 1 a cada novo elemento adicionado

![image](https://user-images.githubusercontent.com/112867913/215527120-c598ff1b-5d7f-44e4-bc93-a18ea73a48a2.png)

## Alterando tabelas e relacionando-as

As tabelas são relacionadas por chaves estrangeiras. Para adicionar essa relação, utilizaremos o comando ```ALTER TABLE nome_da_tabela add foreign key (nome_do_atributo) REFERENCES nome_da_tabela_a_ser_relacionada (nome_do_atributo)```

Exemplo:
**Turma** - cod_turma(PK), cod_disc(FK), cod_curso(FK), data_inicio

> Turma tem duas chaves estrangeiras: **cod_disc** da tabela *Disciplina* e **cod_curso** da tabela *Curso*.

- Vamos relacionar a tabela Turma com a tabela Disciplina

```
ALTER TABLE Turma 
add foreign key (cod_disc) REFERENCES Disciplina (cod_disc)
```

- Agora faremos o mesmo entre Turma e Curso

```
ALTER TABLE Turma 
add foreign key (cod_curso) REFERENCES Curso (cod_curso)
```

- Agora é só relacionar o restante:

```
ALTER TABLE Disciplina 
add foreign key (cod_prof) REFERENCES Professor (cod_prof)

ALTER TABLE Aluno 
add foreign key (cod_curso) REFERENCES Curso (cod_curso)
```

Agora é possível ver o modelo lógico no campo **Desenhador**
![image](https://user-images.githubusercontent.com/112867913/215531858-9c5b5871-511d-4926-a82d-aac23130be94.png)
