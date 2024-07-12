# Documentação do  Projeto Full-Stack de Filmes

# Descrição do Projeto

Este projeto consiste em uma API de back-end desenvolvida para gerenciar um catálogo de filmes. Utiliza Node.js, Express para o roteamento e Prisma como ORM para interagir com o banco de dados. A API permite realizar operações CRUD (Criar, Ler, Atualizar, Deletar) em filmes, que incluem informações como título, URL da imagem, quantidade, descrição e duração em minutos.

## Problema Resolvido

A API oferece uma solução centralizada para gerenciar um catálogo de filmes, facilitando a organização e o acesso a informações detalhadas sobre cada filme. Ideal para aplicações que necessitam de um backend robusto para gerenciar dados de filmes.

## Instruções de Instalação e Configuração

### Pré-requisitos

- Node.js instalado.
- Um banco de dados PostgreSQL.
- npm (Node Package Manager) para gerenciar as dependências.
- Docker (opcional, para facilitar a configuração do PostgreSQL).
- 

# Back-end

### Passos para Instalação

1. Clone o repositório para sua máquina local:
    
    ```bash
    git clone <URL_DO_REPOSITORIO>
    
    ```
    
2. Abra um terminal e navegue até a pasta `back_filme` do projeto clonado:
    
    ```bash
    cd back_filme
    
    ```
    
3. Execute `npm install` para instalar todas as dependências necessárias:
    
    ```bash
    npm install
    
    ```
    
4. Configure o arquivo `.env` na raiz do projeto com as credenciais do seu banco de dados PostgreSQL:
    
    ```bash
    DATABASE_URL="postgresql://usuario:senha@localhost:5432/nome_do_banco"
    
    ```
    
5. Execute `npx prisma migrate dev --name create-table-filmes` para criar a tabela `filmes` no banco de dados:
    
    ```bash
    npx prisma migrate dev --name create-table-filmes
    
    ```
    
6. Execute `npm import cors` para importar e configurar o pacote CORS na sua aplicação:
    
    ```jsx
    npm i cors
    ```
    
7. Inicie a aplicação com `npm run start`. A aplicação estará rodando na porta 3333:
    
    ```bash
    npm run start
    
    ```
    

### Configuração do Docker para PostgreSQL

### Comandos Docker Úteis

- Para iniciar o docker-compose será necessário executar o comando abaixo:
    
    ```jsx
    docker-compose up -d
    ```
    
- Em seguida execute as migrate com a seguinte linha de comando:
    
    ```jsx
    npx prisma migrate dev
    ```
    
    ## Comandos importantes para verificar se a imagem está ativa
    
- **Listar instâncias que estão rodando:**
    
    ```bash
    docker ps 
    ```
    
- **Listar todas as instâncias:**
    
    ```bash
    docker ps -a
    ```
    
- **Listar todas as imagens existentes:**
    
    ```bash
    docker images
    ```
    
- **Baixar a imagem do PostgreSQL:**
    
    ```bash
    docker pull postgres
    ```
    
- **Criar uma instância do PostgreSQL (baixando a imagem automaticamente):**
    
    ```bash
    docker create postgres
    ```
    
- **Apagar uma instância caso exista:**
    
    ```bash
    docker rm postgres
    ```
    
- **Criar e rodar uma instância do PostgreSQL:**
    
    ```bash
    docker run --name postgres-p 5432:5432 -e POSTGRES_PASSWORD=secret -d postgres
    ```
    
- **Iniciar a instância criada:**
    
    ```bash
    docker start postgres
    ```
    
- **Parar a instância rodando:**
    
    ```bash
    docker stop postgres
    ```
    

### Iniciar o Projeto Node.js

1. Iniciar o projeto Node:
    
    ```bash
    npm init -y
    ```
    
2. Instalar o Express:
    
    ```bash
    npm i express
    ```
    
3. Instalar os tipos do Express para TypeScript:
    
    ```bash
    npm i @types/express -D
    ```
    
4. Instalar TypeScript e ts-node:
    
    ```bash
    npm i typescript ts-node @types/node -D
    ```
    
5. Instalar o Prisma:
    
    ```bash
    npm i prisma -D
    ```
    
6. Iniciar o TypeScript e criar o arquivo `tsconfig.json`:
    
    ```bash
    npx tsc --init
    ```
    
7. Iniciar o Prisma e criar os arquivos `.env` e `schema.prisma`:
    
    ```bash
    npx prisma init
    ```
    

## Exemplos de Uso

### Listar Todos os Filmes

**GET** `/filme`

Retorna uma lista de todos os filmes cadastrados.

### Adicionar um Novo Filme

**POST** `/filme`

Corpo da requisição:

```json
{
  "title": "Nome do Filme",
  "imageURL": "URL da Imagem do Filme",
  "amount": 10,
  "describe": "Descrição do Filme",
  "time_minutes": 120
}

```

Adiciona um novo filme ao catálogo.

### Buscar Filme por ID

**GET** `/filme/:id`

Substitua `:id` pelo ID do filme desejado. Retorna os detalhes do filme especificado.

### Atualizar um Filme

**PUT** `/filme/:id`

Substitua `:id` pelo ID do filme que deseja atualizar. Corpo da requisição similar ao da adição de um novo filme.

Atualiza os detalhes do filme especificado.

### Deletar um Filme

**DELETE** `/filme/:id`

Substitua `:id` pelo ID do filme que deseja deletar. Remove o filme do catálogo.

**Nota:** É extremamente importante instanciar o `{id}` corretamente nas requisições GET, PUT e DELETE para garantir que as operações sejam realizadas no filme específico desejado.

## Como Contribuir

1. Faça um fork do projeto.
2. Crie uma branch para sua feature ou correção:
    
    ```bash
    git checkout -b minha-nova-feature
    ```
    
3. Faça o commit das suas alterações:
    
    ```bash
    git commit -m 'Adiciona nova feature'
    ```
    
4. Envie para o branch original:
    
    ```bash
    git push origin minha-nova-feature
    ```
    
5. Crie um pull request.

## Desenho da Arquitetura

O projeto segue uma arquitetura de camadas, onde temos:

1. **Camada de Roteamento:** Gerencia as rotas da aplicação.
2. **Camada de Controle:** Contém a lógica de controle das requisições.
3. **Camada de Serviço:** Contém a lógica de negócios.
4. **Camada de Dados:** Gerencia a interação com o banco de dados.

### Principais Features

- CRUD de filmes.
- Validação de dados de entrada.
- Uso de ORM para interação com o banco de dados.
- Estrutura modular e escalável.

### Padrões de Projetos

- **MVC (Model-View-Controller):** Organiza a aplicação em três componentes principais para separação de responsabilidades.
- **DAO (Data Access Object):** Abstrai e encapsula o acesso ao banco de dados.

### Style Guide

Seguir o guia de estilo padrão do ESLint com algumas customizações específicas para o projeto, como uso do Prettier para formatação de código.

### Exemplos de Consumo da API com Insomnia

### Listar Todos os Filmes

**Método:** GET

**URL:** `http://localhost:3333/filme`

1. Abra o Insomnia.
2. Clique em "New Request".
3. Nomeie a requisição como "Listar Todos os Filmes".
4. Selecione o método **GET**.
5. Insira a URL `http://localhost:3333/filme`.
6. Clique em "Send".

### Adicionar um Novo Filme

**Método:** POST

**URL:** `http://localhost:3333/filme`

1. Abra o Insomnia.
2. Clique em "New Request".
3. Nomeie a requisição como "Adicionar Novo Filme".
4. Selecione o método **POST**.
5. Insira a URL `http://localhost:3333/filme`.
6. Vá para a aba "Body" e selecione "JSON".
7. Adicione o seguinte JSON no corpo da requisição:
    
    ```json
    {
      "title": "Nome do Filme",
      "imageURL": "URL da Imagem do Filme",
      "amount": 10,
      "describe": "Descrição do Filme",
      "time_minutes": 120
    }
    
    ```
    
8. Clique em "Send".

### Buscar Filme por ID

**Método:** GET

**URL:** `http://localhost:3333/filme/:id`

1. Abra o Insomnia.
2. Clique em "New Request".
3. Nomeie a requisição como "Buscar Filme por ID".
4. Selecione o método **GET**.
5. Insira a URL `http://localhost:3333/filme/1` (substitua `1` pelo ID do filme desejado).
6. Clique em "Send".

### Atualizar um Filme

**Método:** PUT

**URL:** `http://localhost:3333/filme/:id`

1. Abra o Insomnia.
2. Clique em "New Request".
3. Nomeie a requisição como "Atualizar Filme".
4. Selecione o método **PUT**.
5. Insira a URL `http://localhost:3333/filme/1` (substitua `1` pelo ID do filme que deseja atualizar).
6. Vá para a aba "Body" e selecione "JSON".
7. Adicione o seguinte JSON no corpo da requisição:
8. Clique em "Send".
    
    ```json
    {
      "title": "Nome do Filme Atualizado",
      "imageURL": "URL da Imagem do Filme Atualizado",
      "amount": 20,
      "describe": "Descrição do Filme Atualizado",
      "time_minutes": 150
    }
    
    ```
    

### Deletar um Filme

**Método:** DELETE

**URL:** `http://localhost:3333/filme/:id`

1. Abra o Insomnia.
2. Clique em "New Request".
3. Nomeie a requisição como "Deletar Filme".
4. Selecione o método **DELETE**.
5. Insira a URL `http://localhost:3333/filme/1` (substitua `1` pelo ID do filme que deseja deletar).
6. Clique em "Send".

## Aprendizados

Durante o desenvolvimento deste projeto, aprendi sobre a integração do Prisma com o Node.js e como utilizar o Docker para gerenciar instâncias de banco de dados de forma eficiente. Também aprofundei meus conhecimentos em arquitetura de software e boas práticas de desenvolvimento backend.

# Front-End

1. Abra o CMD do seu computador escolha a pasta desejada e faça o git clone

```powershell
git clone https://github.com/SinvalFilho/Full-Movie
```

2. Quando fazer o download do repositorio tera duas pastas uma com o back-end chamada “Black-Filmes” e outra com o front-end  “Front-Filme”
3. faça um cd ./front-filme/ e depois abra com o vs code .

```powershell
cd full-Movie
cd front-filme
code .
```

4. faça o download das dependencias 

```powershell
npm install
npm install react react-dom
npm install react-icons

```

5. Depois inicie o seu React.

```powershell
npm run dev

```
