# API Genérica com MongoDB e Mongo Express

Este projeto é uma API RESTful dinâmica e genérica construída com Express.js e MongoDB. A aplicação suporta operações CRUD em qualquer entidade especificada, proporcionando flexibilidade e facilidade de uso para prototipagem ou desenvolvimento de aplicações dinâmicas. O Mongo Express está incluído para gerenciamento do banco de dados por meio de uma interface web simples.

## Índice

1. [Pré-requisitos](#pré-requisitos)
2. [Primeiros Passos](#primeiros-passos)
   - [Configuração e Execução](#configuração-e-execução)
   - [Parando a Aplicação](#parando-a-aplicação)
3. [Estrutura do Projeto](#estrutura-do-projeto)
4. [Endpoints da API](#endpoints-da-api)
   - [Criar Entidade](#criar-entidade)
   - [Recuperar Entidade por ID](#recuperar-entidade-por-id)
   - [Atualizar Entidade por ID](#atualizar-entidade-por-id)
   - [Excluir Entidade por ID](#excluir-entidade-por-id)
   - [Listar Entidades](#listar-entidades)
5. [Configuração do Ambiente](#configuração-do-ambiente)
6. [Comandos Docker](#comandos-docker)
7. [Mongo Express](#mongo-express)
8. [Tecnologias Utilizadas](#tecnologias-utilizadas)

---

## Pré-requisitos

- Docker e Docker Compose instalados no seu sistema.
- Conhecimento básico sobre APIs REST e MongoDB.

---

## Primeiros Passos

### Configuração e Execução

1. Clone este repositório.
2. Crie um arquivo chamado `mongo-compose.yml` e cole a configuração do Docker Compose fornecida no projeto.
3. Execute o seguinte comando para iniciar os serviços MongoDB e Mongo Express:

   ```bash
   docker-compose -f mongo-compose.yml up -d
   ```

4. Instale as dependências necessárias para a aplicação Express.js:

   ```bash
   npm install
   ```

5. Inicie o servidor da API:

   ```bash
   node server.js
   ```

6. O servidor da API estará disponível em `http://localhost:3000` e o Mongo Express estará acessível em `http://localhost:8081`.

### Parando a Aplicação

Para parar os serviços e limpar os recursos:

```bash
docker-compose -f mongo-compose.yml down -v
```

---

## Estrutura do Projeto

```plaintext
├── mongo-compose.yml   # Arquivo Docker Compose para MongoDB e Mongo Express
├── server.js           # Arquivo principal do servidor da API
└── package.json        # Dependências e scripts do Node.js
```

---

## Endpoints da API

### Criar Entidade
- **POST** `/:entity`
- Cria uma nova entidade na coleção especificada.
- **Corpo da Requisição**: Objeto JSON representando a nova entidade.
- **Resposta**: ID da entidade criada.

### Recuperar Entidade por ID
- **GET** `/:entity/:id`
- Recupera uma entidade específica pelo seu ID.
- **Resposta**: Objeto JSON representando a entidade.

### Atualizar Entidade por ID
- **PUT** `/:entity/:id`
- Atualiza uma entidade existente pelo seu ID.
- **Corpo da Requisição**: Objeto JSON com os campos atualizados.
- **Resposta**: Mensagem de status confirmando a atualização.

### Excluir Entidade por ID
- **DELETE** `/:entity/:id`
- Exclui uma entidade pelo seu ID.
- **Resposta**: Mensagem de status confirmando a exclusão.

### Listar Entidades
- **GET** `/:entity`
- Recupera uma lista paginada de entidades na coleção.
- **Parâmetros de Consulta**:
  - `query`: Objeto JSON para filtrar os resultados.
  - `fields`: Lista separada por vírgulas dos campos a incluir/excluir.
  - `page`: Número da página (padrão é 1).
  - `limit`: Número de resultados por página (padrão é 10).

---

## Configuração do Ambiente

O arquivo `mongo-compose.yml` configura o MongoDB e o Mongo Express:

- **MongoDB**
  - Nome de Usuário Admin: `admin`
  - Senha Admin: `admin123`

- **Mongo Express**
  - Nome de Usuário Admin: `admin`
  - Senha Admin: `admin123`

---

## Comandos Docker

- Iniciar os contêineres:
  ```bash
  docker-compose -f mongo-compose.yml up -d
  ```

- Parar os contêineres e remover volumes:
  ```bash
  docker-compose -f mongo-compose.yml down -v
  ```

- Acessar o shell do MongoDB:
  ```bash
  docker exec -it mongodb-container mongosh -u admin -p admin123
  ```

- Visualizar logs:
  ```bash
  docker-compose -f mongo-compose.yml logs mongo
  docker-compose -f mongo-compose.yml logs mongo-express
  ```

---

## Mongo Express

O Mongo Express fornece uma interface web para gerenciar a instância do MongoDB. Após iniciar os contêineres, acesse o Mongo Express em:

```
http://localhost:8081
```

As credenciais de login estão definidas no arquivo `mongo-compose.yml`.

---

## Tecnologias Utilizadas

- **Express.js**: Framework para aplicações web com Node.js.
- **MongoDB**: Banco de dados NoSQL.
- **Mongo Express**: Interface administrativa baseada na web para o MongoDB.
- **Docker**: Plataforma de containerização para gerenciar dependências e implantação.