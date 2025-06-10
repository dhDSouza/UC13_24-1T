# 💡 Atividade em Grupo: Sistema de Cadastro e Login de Usuários

## 🎯 Objetivo

Desenvolver, em grupos, um sistema simples de **cadastro e login de usuários**, com autenticação e armazenamento de dados, utilizando divisão de responsabilidades entre **Frontend** e **Backend**.

---

## 👥 Organização dos Grupos

Em grupos de 4 a 6 alunos. Cada grupo deverá se dividir internamente em dois times:

* **Time Frontend (2 a 3 alunos):**
  Responsável pelas telas, interações e consumo da API.

* **Time Backend (2 a 3 alunos):**
  Responsável pela criação da API, regras de negócio e persistência de dados.

---

## 🧱 Funcionalidades do Sistema

1. **Cadastro de Usuário**

   * Campos obrigatórios: nome, email e senha.
   * Senha deve ser criptografada no backend.

2. **Login de Usuário**

   * Verificar e-mail e senha.
   * Retornar uma mensagem de sucesso ou erro.

---

## 🛠️ Tecnologias

### Backend 🖥️

* TypeScript + Express
* Banco de dados MySQL
* Bcrypt para criptografar senhas

### Frontend 💻

* HTML, CSS e JavaScript
* Fetch para chamadas HTTP

---

## 📋 Etapas do Projeto

### 1. Planejamento 📌

* Definir os papéis de cada integrante.
* Criar um fluxograma básico do processo de cadastro/login.
* Montar o protótipo das telas (pode ser no papel, Figma ou Canva).

### 2. Desenvolvimento Backend 🔧

* Criar as rotas da API:

  * `POST /register`
  * `POST /login`
  * `GET /profile`

* Implementar validações e criptografia de senhas.

### 3. Desenvolvimento Frontend 🎨

* Criar as telas:

  * Cadastro
  * Login

* Fazer as requisições HTTP para a API.

---

## 🧪 Entregáveis

* Código-fonte completo no GitHub (frontend e backend em pastas separadas).
* Apresentação de 5 a 10 minutos explicando:

  * O que cada integrante fez.
  * Dificuldades encontradas e como resolveram.

---

## 🧠 Dicas

* Testem a API antes de integrar com o frontend.
* Usem variáveis de ambiente para dados sensíveis (como senhas ou conexões).

> [!TIP]
> **OBS: Não hesitem em me chamar em caso de dúvidas**   
> _Eu posso indicar a vocês como fazer a comunicação entre o frontend e o backend_
