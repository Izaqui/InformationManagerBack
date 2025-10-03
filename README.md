

# 🚀 Backend - User Management API

O **Backend** é desenvolvido em **NestJS + TypeORM + SQLite**.  
O sistema implementa autenticação via **JWT**, CRUD de usuários com permissões (admin x user), listagem com filtros e ordenação, além de endpoint para usuários inativos.

----------

## 📦 Tecnologias utilizadas

-   **NestJS** (framework backend)
    
-   **TypeORM** (ORM)
    
-   **SQLite** (banco de dados simples e portátil)
    
-   **JWT + Passport** (autenticação)
    
-   **bcrypt** (hash de senhas)
    
-   **Swagger** (documentação automática da API)
    
-   **class-validator** (validação de DTOs)
    

----------

## ⚙️ Instalação e execução

### Pré-requisitos

-   Node.js >= 16
    
-   npm ou yarn
    

### Passos

1.  Clone este repositório:
    
    ```bash
    git clone https://github.com/Izaqui/InformationManagerBack.git
    cd InformationManagerBack
    
    ```
    
2.  Instale as dependências:
    
    ```bash
    npm install
    
    ```
    
3.  Crie o arquivo `.env` na raiz do projeto:
    
    ```env
    PORT=3000
    SQLITE_DB=database.sqlite
    TYPEORM_SYNC=true
    
    JWT_SECRET=uma_chave_secreta_segura
    JWT_EXPIRES_IN=3600s
    
    ```
    
4.  Rode o servidor em modo desenvolvimento:
    
    ```bash
    npm run start:dev
    
    ```
    
5.  Acesse:
    
    -   API: `http://localhost:3000`
        
    -   Documentação Swagger: `http://localhost:3000/docs`
        

----------

## 🔑 Autenticação

-   **Login** via `POST /auth/login` com `email` e `password`.
    
-   Resposta retorna `{ access_token }`.
    
-   Nas requisições seguintes, envie no **header**:
    
    ```
    Authorization: Bearer <token>
    
    ```
    

----------

## 📚 Endpoints principais

### Auth

-   `POST /auth/register` → Cria novo usuário
    
-   `POST /auth/login` → Autentica e retorna token
    

### Users

-   `GET /users` → Lista todos os usuários (apenas **admin**)
    
    -   Suporta filtros (`name`, `role`, `email`) e ordenação (`sortBy`, `order`)
        
-   `GET /users/me` → Retorna dados do usuário autenticado
    
-   `GET /users/:id` → Retorna usuário específico
    
-   `POST /users` → Cria usuário
    
-   `PUT /users/:id` → Atualiza usuário (admin pode todos, user apenas o próprio)
    
-   `DELETE /users/:id` → Remove usuário (apenas **admin**)
    
-   `GET /users/inactive/list?days=30` → Lista usuários inativos nos últimos X dias (apenas **admin**)
    

----------

## 🧪 Testes

Rodar testes unitários com Jest:

```bash
npm run test

```

----------

## 📌 Próximos passos (opcionais / diferenciais)

-   Adicionar **OAuth (Google/Microsoft)**.
    
-   Criar **seed inicial** para gerar usuário `admin`.
    
-   Deploy em ambiente público (Heroku, Railway, etc).
    
-   Melhorar cobertura de **testes automatizados**.
    


