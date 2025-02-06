# Modelagem de Dados 🏗️

## Introdução

A **modelagem de dados** é essencial para estruturar informações de forma organizada e eficiente dentro de um banco de dados. Ela garante **redução de redundância**, **melhor organização** e **facilidade de manutenção**.

Os modelos são divididos em três níveis principais:

- **Conceitual**: Representação abstrata dos dados.
- **Lógico**: Estrutura técnica com definições de atributos e relacionamentos.
- **Físico**: Implementação real no banco de dados.

Além disso, a modelagem envolve **entidades, atributos, relacionamentos e restrições** para garantir integridade e consistência.

## Implementação Prática no MySQL 💻

Abaixo, seguem exemplos práticos de criação e manipulação de um banco de dados baseado em modelagem de dados:

### Criando um Banco de Dados

Criamos um banco de dados chamado `RegistroDePublicacoes` e o selecionamos para uso.

```
CREATE DATABASE RegistroDePublicacoes;
SHOW DATABASES;
USE RegistroDePublicacoes;
```

### Criando Tabelas

Criamos uma tabela `editora` para armazenar informações sobre editoras, com `id` como chave primária e `nome_editora` como um campo único.

```
CREATE TABLE editora (
    id INTEGER AUTO_INCREMENT PRIMARY KEY,
    nome_editora VARCHAR(120) UNIQUE,
    pais VARCHAR(5)
);
```

Criamos a tabela `periodicos`, relacionando-a com a `editora` através de uma chave estrangeira `id_editora`, garantindo integridade referencial.

```
CREATE TABLE periodicos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome_periodico VARCHAR(20),
    issn INT,
    id_editora INT,
    CONSTRAINT fk_editora_periodico FOREIGN KEY (id_editora) REFERENCES editora(id)
);
```

### Inserindo Dados

Adicionamos registros às tabelas `editora` e `periodicos`.

```
INSERT INTO editora (nome_editora, pais) VALUES ('IEEE', 'EUA'), ('DataScienceMagazine', 'EUA');
```

```
INSERT INTO periodicos (nome_periodico, issn, id_editora) VALUES ('Special Issue', 123456789, 1);
```

### Consultando Dados

Consultamos os registros armazenados nas tabelas.

```
SELECT * FROM editora;
SELECT * FROM periodicos;
```

### Atualizando e Excluindo Registros

Atualizamos dados da tabela `editora` e removemos um registro da tabela `periodicos`.

```
UPDATE editora SET pais = 'USA' WHERE nome_editora = 'IEEE';
DELETE FROM periodicos WHERE nome_periodico = 'Special Issue';
```

### Excluindo um Banco de Dados

Caso necessário, podemos excluir o banco de dados criado.

```
DROP DATABASE RegistroDePublicacoes;
```

---

## Conclusão ✅

A modelagem de dados permite estruturar informações de forma eficiente e segura. Com comandos SQL, transformamos essa modelagem em um banco funcional, garantindo **integridade e escalabilidade**. 🚀