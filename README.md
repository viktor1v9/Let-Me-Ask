# Let-Me-Ask

Um projeto de plataforma de perguntas e respostas, desenvolvido para permitir que os usuários criem, visualizem e interajam com perguntas e respostas.

## Desenvolvido por

- **Victo Reis**

---

## 🚀 Tecnologias Utilizadas

O projeto é uma aplicação Full-Stack dividida em `server` (backend) e `web` (frontend), desenvolvida como um monorepo.

### **Backend (server)**

- **Framework:** [Fastify](https://www.fastify.io/) - Um framework web focado em performance e baixo overhead.
- **ORM:** [Drizzle ORM](https://orm.drizzle.team/) - Um ORM TypeScript "headless" para interagir com o banco de dados de forma segura e tipada.
- **Banco de Dados:** [PostgreSQL](https://www.postgresql.org/) - Sistema de gerenciamento de banco de dados relacional.
- **Validação:** [Zod](https://zod.dev/) - Biblioteca de declaração e validação de tipos para TypeScript.
- **Ambiente de Execução:** [Node.js](https://nodejs.org/)

### **Frontend (web)**

- **Framework:** [React](https://react.dev/) - Biblioteca para construir interfaces de usuário.
- **Build Tool:** [Vite](https://vitejs.dev/) - Ferramenta de build moderna e ultrarrápida.
- **Roteamento:** [React Router DOM](https://reactrouter.com/) - Para gerenciamento de rotas na aplicação.
- **Gerenciamento de Estado do Servidor:** [TanStack Query](https://tanstack.com/query/latest) - Para fetching, caching e atualização de dados assíncronos.
- **Estilização:** [Tailwind CSS](https://tailwindcss.com/) - Framework CSS utility-first para estilização rápida e customizável.
- **Formulários:** [React Hook Form](https://react-hook-form.com/) - Para gerenciamento de formulários de forma performática.

---

## 🏗️ Padrões de Projeto

- **Arquitetura Cliente-Servidor:** A aplicação é claramente dividida entre o backend (API) e o frontend (consumidor da API).
- **API RESTful:** O backend expõe endpoints seguindo os princípios REST para manipulação dos recursos (perguntas, respostas, etc.).
- **Repository Pattern (inferido):** O uso do Drizzle ORM sugere uma camada de abstração para o acesso a dados, separando a lógica de negócio das consultas ao banco de dados.
- **Single Page Application (SPA):** O frontend é uma SPA, onde o React gerencia a renderização da UI dinamicamente no cliente.

---

## ⚙️ Setup e Configuração

Siga os passos abaixo para configurar e executar o projeto em seu ambiente local.

### **Pré-requisitos**

- [Node.js](https://nodejs.org/) (versão 20 ou superior)
- [Docker](https://www.docker.com/) e [Docker Compose](https://docs.docker.com/compose/)

### **1. Clonar o Repositório**

```bash
git clone <URL_DO_SEU_REPOSITORIO>
cd Let-Me-Ask
```

### **2. Configurar o Backend**

1.  **Navegue até a pasta do servidor:**
    ```bash
    cd server
    ```

2.  **Instale as dependências:**
    ```bash
    npm install
    ```

3.  **Configure as variáveis de ambiente:**
    Crie um arquivo `.env` na raiz da pasta `server` e adicione as variáveis necessárias. Você pode usar o arquivo `docker-compose.yml` como referência para as credenciais do banco de dados.
    ```env
    DATABASE_URL="postgresql://docker:docker@localhost:5432/letmeask"
    ```

4.  **Inicie o container do banco de dados:**
    Na raiz da pasta `server`, execute o Docker Compose.
    ```bash
    docker-compose up -d
    ```

5.  **Execute as migrações do banco de dados:**
    Este comando criará as tabelas no banco de dados com base nos schemas do Drizzle.
    ```bash
    npm run db:migrate
    ```

### **3. Configurar o Frontend**

1.  **Navegue até a pasta web:**
    ```bash
    cd ../web
    ```

2.  **Instale as dependências:**
    ```bash
    npm install
    ```

### **4. Executando a Aplicação**

-   **Para iniciar o servidor de desenvolvimento do backend:**
    Na pasta `server`, execute:
    ```bash
    npm run dev
    ```
    O servidor estará rodando em `http://localhost:3333`.

-   **Para iniciar o cliente de desenvolvimento do frontend:**
    Na pasta `web`, execute:
    ```bash
    npm run dev
    ```
    A aplicação estará acessível em `http://localhost:5173`.

---

## 📜 Scripts Principais

### **Server**

-   `npm run dev`: Inicia o servidor em modo de desenvolvimento com watch.
-   `npm run db:migrate`: Aplica as migrações do Drizzle no banco de dados.
-   `npm run db:generate`: Gera novos arquivos de migração com base nas alterações do schema.

### **Web**

-   `npm run dev`: Inicia o servidor de desenvolvimento do Vite.
-   `npm run build`: Compila a aplicação para produção.
