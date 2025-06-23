# 📘 Atividade Avaliativa – Sistema Completo com Autenticação e CRUD

**Tecnologias obrigatórias**: TypeScript + TypeORM + HTML/CSS/JS (puro ou com algum framework leve se desejado)

## 🎯 Objetivo

Desenvolver um sistema web completo com **tema livre**, que contenha:

* Backend em **Node.js com TypeScript e TypeORM**
* Frontend em **HTML, CSS e JavaScript**
* Autenticação (login e cadastro)
* CRUD completo de alguma entidade à sua escolha (ex: Tarefas, Produtos, Eventos, Jogos, Filmes, etc.)

---

## 🧱 Requisitos Técnicos

### 📦 Back-end

* ✅ Node.js com TypeScript
* ✅ ORM: TypeORM
* ✅ Banco de dados: MySQL
* ✅ Cadastro e login de usuários (com hash de senha)
* ✅ CRUD completo de uma entidade:

  * Criar
  * Listar tudo
  * Buscar por ID
  * Editar
  * Deletar
  
* ✅ Validações básicas (campos obrigatórios, formato de dados, etc.)

### 🌐 Front-end (dentro da pasta `public/`)

* ✅ Tela de login
* ✅ Tela de cadastro
* ✅ Tela inicial (após login) com:

  * Boas-vindas
  * Acesso às operações do CRUD
  
* ✅ Interface para:

  * Cadastrar nova entidade
  * Listar todas
  * Buscar por ID
  * Editar
  * Deletar
  
* ✅ Comunicação com o back via `fetch` e consumo de JSON
* ✅ Feedback visual para ações (ex: alertas de sucesso/erro)

---

## 📁 Organização do Projeto

```
📦 nome-do-projeto/
├── src/
│   ├── config/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   └── server.ts
├── public/
│   ├── index.html         <- login
│   ├── cadastro.html
│   ├── home.html          <- tela pós-login
│   ├── css/
│   └── js/
```

---

## 🧠 Critérios de Avaliação

| Critério                                          | Pontuação   |
|:-------------------------------------------------:|:-----------:|
| Cadastro e Login funcionais com hash de senha     | 10 pts      |
| CRUD funcional (API + Front integrado)            | 20 pts      |
| Estrutura de código organizada                    | 10 pts      |
| Responsividade e usabilidade do front             | 10 pts      |
| Validações no back-end                            | 20 pts      |
| Comunicação via `fetch` com tratamento de erros   | 10 pts      |
| Criatividade e completude da ideia                | 10 pts      |
| Documentação no `README.md` com instruções de uso | 10 pts      |
| **Total**                                         | **100 pts** |

---

## 📅 Entrega

* Subir projeto em um repositório do GitHub
* README com instruções de como rodar o back e testar o sistema

---

## 💡 Dicas de Temas

* To-do list com categorias
* Catálogo de produtos com gerenciamento de estoque
* Gerenciador de filmes/séries assistidas
* Sistema de posts e comentários
* Diário pessoal com tags
