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

Antes de tudo, precisamos de dados para inserir no banco 🌛 *A lista a seguir foi criada em sala de aula.* **PK:** Primary Key / Chave Primária | **FK:** Foreign Key / Chave Estrangeira. [Mais informações.](https://www.diegomacedo.com.br/entendendo-as-chaves-dos-bancos-de-dados/)

Nosso banco terá a seguinte estrutura: **Entidade - Atributos**

- **Curso** - cod_curso(PK), nome, tipo
- **Aluno** - cod_aluno(PK), matrícula, nome, endereço, telefone
- **Turma** - cod_turma(PK), cod_aluno(FK), cod_disc(FK), cod_curso(FK), data_inicio
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
