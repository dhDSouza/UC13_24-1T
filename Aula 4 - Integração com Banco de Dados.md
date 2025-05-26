# 🚀 **1. Introdução ao TypeORM e reflect-metadata**

### **O que é o TypeORM?**

TypeORM é um ORM (Object Relational Mapper) para Node.js, escrito em TypeScript. Ele permite que você trabalhe com bancos de dados relacionais (como MySQL, PostgreSQL, etc.) usando objetos e classes ao invés de SQL puro.

### **O que é reflect-metadata?**

O `reflect-metadata` é uma biblioteca que permite que o TypeScript adicione informações extras (metadados) nas classes e propriedades, o que é essencial para o funcionamento de decorators como `@Entity`, `@Column`, etc.

**Por que usamos?**

* Permite mapear classes para tabelas.
* Facilita o desenvolvimento, abstraindo SQL complexo.
* Aumenta a produtividade e a legibilidade do código.

---

# 🔧 **2. Configuração do Projeto**

### **Passo 1: Inicializar o projeto**

```bash
mkdir api-typeorm-mysql
cd api-typeorm-mysql
npm init -y
```

### **Passo 2: Instalar as dependências**

```bash
npm install express typeorm reflect-metadata mysql2
```

### **Dependências de desenvolvimento:**

```bash
npm install -D typescript ts-node-dev @types/node @types/express
```

### **Passo 3: Criar o arquivo `tsconfig.json`**

```bash
npx tsc --init
```

Ajuste ele assim:

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

### **Passo 4: Estrutura de pastas sugerida**

```
src/
├── database/
│   └── data-source.ts
├── models/
│   └── User.ts
├── routes/
│   └── user.routes.ts
├── controllers/
│   └── UserController.ts
├── index.ts
```

---

# 🔌 **3. Conectando com o MySQL**

### **Arquivo: `src/database/data-source.ts`**

```ts
import 'reflect-metadata';
import { DataSource } from 'typeorm';

export const AppDataSource = new DataSource({
    type: 'mysql',
    host: 'localhost',
    port: 3306,
    username: 'root', // seu usuário do MySQL
    password: 'root', // sua senha
    database: 'aula_typeorm',
    synchronize: true, // CUIDADO! True no desenvolvimento, False em produção
    logging: true,
    entities: ["src/models/*.ts"],
});
```

---

# 🏗️ **4. Criando uma entidade (Tabela)**

### **Arquivo: `src/models/User.ts`**

```ts
import { Entity, PrimaryGeneratedColumn, Column } from 'typeorm';

@Entity('users') // nome da tabela
export class User {
    @PrimaryGeneratedColumn()
    id: number;

    @Column()
    name: string;

    @Column({ unique: true })
    email: string;

    @Column()
    password: string;
}
```

**Explicação dos decorators:**

* `@Entity()` → Define que essa classe é uma tabela.
* `@PrimaryGeneratedColumn()` → Cria uma coluna do tipo chave primária auto incrementável.
* `@Column()` → Define uma coluna normal no banco.

---

# 🚦 **5. CRUD Básico**

### **Arquivo: `src/controllers/UserController.ts`**

```ts
import { Request, Response } from 'express';
import { AppDataSource } from '../database/data-source';
import { User } from '../models/User';

const userRepository = AppDataSource.getRepository(User);

export class UserController {
    // Listar todos os usuários
    async list(req: Request, res: Response) {
        const users = await userRepository.find();
        return res.json(users);
    }

    // Criar novo usuário
    async create(req: Request, res: Response) {
        const { name, email, password } = req.body;

        const user = userRepository.create({ name, email, password });
        await userRepository.save(user);

        return res.status(201).json(user);
    }

    // Buscar usuário por ID
    async show(req: Request, res: Response) {
        const { id } = req.params;

        const user = await userRepository.findOneBy({ id: Number(id) });

        if (!user) {
            return res.status(404).json({ message: 'Usuário não encontrado' });
        }

        return res.json(user);
    }

    // Atualizar usuário
    async update(req: Request, res: Response) {
        const { id } = req.params;
        const { name, email, password } = req.body;

        const user = await userRepository.findOneBy({ id: Number(id) });

        if (!user) {
            return res.status(404).json({ message: 'Usuário não encontrado' });
        }

        user.name = name;
        user.email = email;
        user.password = password;

        await userRepository.save(user);

        return res.json(user);
    }

    // Deletar usuário
    async delete(req: Request, res: Response) {
        const { id } = req.params;

        const user = await userRepository.findOneBy({ id: Number(id) });

        if (!user) {
            return res.status(404).json({ message: 'Usuário não encontrado' });
        }

        await userRepository.remove(user);

        return res.status(204).send();
    }
}
```

---

### **Rotas: `src/routes/user.routes.ts`**

```ts
import { Router } from 'express';
import { UserController } from '../controllers/UserController';

const routes = Router();
const userController = new UserController();

routes.get('/users', userController.list);
routes.post('/users', userController.create);
routes.get('/users/:id', userController.show);
routes.put('/users/:id', userController.update);
routes.delete('/users/:id', userController.delete);

export default routes;
```

---

### **Arquivo principal: `src/index.ts`**

```ts
import express, { Application } from 'express';
import { AppDataSource } from './database/data-source';
import routes from './routes/user.routes';

AppDataSource.initialize()
    .then(() => {
        const app: Application = express();
        app.use(express.json());

        app.use('/api', routes);

        app.listen(3000, () => console.log('Server rodando na porta 3000'));
    })
    .catch((error) => console.log(error));
```

# 📝 **6. Exercícios Práticos**

1. **Crie uma entidade `Product` com os campos:**

   * `id` (PK)
   * `name` (string)
   * `price` (number)
   * `description` (string)

2. **Implemente o CRUD completo para a entidade `Product`.**

3. **Adicione uma rota para buscar um produto pelo nome (dica: use `findBy` ou `findOneBy`).**

4. **Adapte a API para não retornar o campo `password` na listagem dos usuários.**

5. **Implemente uma verificação que impeça a criação de usuários com e-mails duplicados, retornando um erro adequado.**
