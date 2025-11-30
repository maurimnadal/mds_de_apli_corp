# 🎬 ROTEIRO DE APRESENTAÇÃO - 30 MINUTOS

## 📌 ESTRUTURA DA APRESENTAÇÃO

### INTRODUÇÃO (2 min)
**O que dizer:**
> "Bom dia/tarde! Vou apresentar o Sistema de Voluntariado IFRS, desenvolvido para a Prova P2 de Aplicações Corporativas. O sistema é um monólito completo com backend Node.js + Express, banco MySQL com Prisma ORM, e frontend React. Implementei autenticação JWT, testes automatizados, logs estruturados e documentação completa."

---

## PARTE 1: ARQUITETURA E TECNOLOGIAS (3 min)

### Mostrar no VS Code
Abra: `README.md`

**O que dizer:**
> "A arquitetura segue o padrão Model-Service-Controller com separação clara de responsabilidades."

**Tecnologias principais:**
- Backend: Node.js + Express + Prisma ORM
- Banco: MySQL 8.0
- Frontend: React + Vite
- Autenticação: JWT
- Logs: Winston
- Testes: Jest + Supertest + Selenium
- Documentação: Swagger + JSDoc

**Mostrar estrutura de pastas:**
```
backend/
├── prisma/          → ORM (schema, seeds, migrations)
├── src/
│   ├── config/      → Configurações (Prisma, Logger)
│   ├── models/      → Acesso ao banco
│   ├── services/    → Lógica de negócio
│   ├── controllers/ → Requisições HTTP
│   ├── routes/      → Endpoints
│   └── middlewares/ → Autenticação, Logs
└── tests/           → Testes (unit, integration, e2e)
```

---

## PARTE 2: DEMONSTRAÇÃO DA APLICAÇÃO (5 min)

### 2.1 - Frontend
**Abrir:** http://localhost:5173

**O que dizer:**
> "Vou fazer login como administrador para demonstrar as funcionalidades."

**Login:**
- Email: `admin@ifrs.edu.br`
- Senha: `123456`

**Demonstrar:**
1. ✅ **Dashboard** - "Aqui vemos as informações do usuário autenticado"
2. ✅ **Eventos** - "Lista de eventos com dados do banco"
3. ✅ **Criar Evento** - "Apenas admins podem criar eventos"
4. ✅ **Voluntários** - "Gerenciamento de voluntários"

**O que dizer:**
> "O frontend consome a API REST do backend, com autenticação JWT. O token é armazenado e enviado em todas as requisições."

---

## PARTE 3: DOCUMENTAÇÃO DA API (5 min)

### 3.1 - Swagger
**Abrir:** http://localhost:3000/api-docs

**O que dizer:**
> "Toda a API está documentada com Swagger/OpenAPI, conforme requisito da prova."

**Mostrar:**
1. ✅ **GET /events** - "Documentado com schema de resposta"
2. ✅ **POST /events** - "Documentado com schema de request"
3. ✅ **POST /auth/login** - "Documentado com autenticação"

### 3.2 - Testar no Swagger
**Executar:**
1. **POST /auth/login**
   ```json
   {
     "email": "admin@ifrs.edu.br",
     "password": "123456"
   }
   ```
   **Copiar token**

2. **Authorize** - Colar token: `Bearer SEU_TOKEN`

3. **GET /events** - "Agora autenticado, consigo listar eventos"

4. **POST /events** - Criar evento de demonstração
   ```json
   {
     "title": "Evento Apresentação",
     "description": "Criado durante a apresentação",
     "date": "2025-12-31",
     "location": "IFRS Campus",
     "max_volunteers": 50
   }
   ```

**O que dizer:**
> "A API segue padrões RESTful, com autenticação JWT e controle de acesso por roles."

---

## PARTE 4: TESTES AUTOMATIZADOS (7 min)

### 4.1 - Testes Unitários
**Executar:**
```bash
npm run test:unit
```

**O que dizer:**
> "Implementei testes unitários com Jest, cobrindo cenários de sucesso e erro."

**Mostrar no código:** `tests/unit/auth.service.test.js`

**Explicar:**
- ✅ Teste de registro (sucesso)
- ✅ Teste de registro (usuário já existe)
- ✅ Teste de login (sucesso)
- ✅ Teste de login (senha incorreta)

### 4.2 - Testes de Integração
**Executar:**
```bash
npm run test:integration
```

**O que dizer:**
> "Os testes de integração usam Supertest para testar a API completa, incluindo autenticação."

**Mostrar no código:** `tests/integration/events.test.js`

**Explicar:**
- ✅ Testa endpoints reais
- ✅ Valida autenticação JWT
- ✅ Testa cenários de erro (401, 400)

### 4.3 - Teste E2E (Selenium)
**Executar:**
```bash
npm run test:e2e
```

**O que dizer:**
> "O teste E2E usa Selenium para simular um usuário real fazendo login no sistema."

**Mostrar resultado:**
```
✅ Navegador iniciado
✅ Página de login carregada
✅ Credenciais preenchidas
✅ Botão de login clicado
✅ Redirecionado para dashboard
✅ TESTE E2E PASSOU
```

**Mostrar no código:** `tests/e2e/login.test.js`

### 4.4 - Cobertura
**Executar:**
```bash
npm test
```

**O que dizer:**
> "A cobertura de testes mostra quais partes do código foram testadas."

---

## PARTE 5: LOGS ESTRUTURADOS (3 min)

### 5.1 - Winston
**O que dizer:**
> "Implementei logs estruturados com Winston, salvos em arquivos e exibidos no console."

**Mostrar arquivo:** `src/config/logger.js`

**Explicar:**
- ✅ Logs em JSON estruturado
- ✅ Níveis: error, warn, info
- ✅ Arquivos separados (error.log, combined.log)

### 5.2 - Ver Logs
**Executar:**
```bash
cat logs/combined.log
```

**Mostrar:**
- ✅ Requisições HTTP logadas
- ✅ Login de usuários
- ✅ Operações CRUD
- ✅ Erros capturados

**O que dizer:**
> "Cada requisição é logada com método, URL, status e duração. Operações importantes como login e CRUD também são registradas."

---

## PARTE 6: PRISMA ORM (4 min)

### 6.1 - Prisma Studio
**Executar:**
```bash
npx prisma studio
```

**Abrir:** http://localhost:5555

**O que dizer:**
> "O Prisma Studio é uma interface visual para o banco de dados."

**Mostrar:**
- ✅ Tabela User (2 usuários)
- ✅ Tabela Event (eventos criados)
- ✅ Relacionamentos

### 6.2 - Schema
**Mostrar arquivo:** `prisma/schema.prisma`

**Explicar:**
```prisma
model User {
  id        Int      @id @default(autoincrement())
  name      String
  email     String   @unique
  password  String
  role      Role     @default(volunteer)
  events    Event[]  // Relacionamento
}

model Event {
  id            Int      @id @default(autoincrement())
  title         String
  date          DateTime
  creator       User?    @relation(...)
}
```

**O que dizer:**
> "O schema define os modelos, relacionamentos e validações. O Prisma gera o cliente automaticamente."

### 6.3 - Seeds
**Mostrar arquivo:** `prisma/seed.js`

**O que dizer:**
> "Os seeds populam o banco com dados fictícios para testes: 2 usuários (admin e voluntário) e 2 eventos."

---

## PARTE 7: CÓDIGO E BOAS PRÁTICAS (5 min)

### 7.1 - JSDoc
**Mostrar arquivos:**
1. `src/models/user.model.js`
2. `src/services/auth.service.js`
3. `src/controllers/auth.controller.js`

**O que dizer:**
> "Todo o código está documentado com JSDoc, explicando funções, parâmetros e retornos."

**Exemplo:**
```javascript
/**
 * Cria um novo usuário no banco de dados
 * @param {Object} data - Dados do usuário
 * @param {string} data.name - Nome do usuário
 * @param {string} data.email - Email do usuário
 * @returns {Promise<Object>} Usuário criado
 */
static async criar({ name, email, password }) {
  // ...
}
```

### 7.2 - Clean Code
**Mostrar exemplos:**

**Nomes claros:**
```javascript
// ✅ BOM
async buscarPorEmail(email)

// ❌ RUIM
async get(e)
```

**Funções pequenas:**
```javascript
// ✅ Cada função faz uma coisa
static async listar() {
  return await EventModel.listar();
}
```

**Sem duplicação:**
```javascript
// ✅ Reutilização via Services
EventService.listar()
EventService.criar()
```

### 7.3 - SOLID
**Explicar:**

**Single Responsibility:**
- Model → Acesso ao banco
- Service → Lógica de negócio
- Controller → HTTP

**Dependency Injection:**
```javascript
const prisma = require('../config/prisma');
const logger = require('../config/logger');
```

---

## PARTE 8: SEGURANÇA (2 min)

### 8.1 - JWT
**Mostrar:** `src/middlewares/auth.middleware.js`

**O que dizer:**
> "Implementei autenticação JWT com middleware que valida o token em rotas protegidas."

**Explicar:**
- ✅ Token gerado no login
- ✅ Middleware valida token
- ✅ Extrai dados do usuário (id, role)
- ✅ Protege rotas por role

### 8.2 - Senhas
**Mostrar:** `src/models/user.model.js`

**O que dizer:**
> "Senhas são hasheadas com bcrypt antes de salvar no banco."

```javascript
const hashedPassword = await bcrypt.hash(password, 10);
```

---

## CONCLUSÃO (2 min)

### Resumo
**O que dizer:**
> "Implementei todos os requisitos da Prova P2:"

✅ **Funcionalidade** - Sistema completo funcionando  
✅ **Arquitetura** - Model-Service-Controller  
✅ **Segurança** - JWT com roles  
✅ **Boas Práticas** - Clean Code, SOLID, ESLint, Prettier  
✅ **Documentação** - Swagger + JSDoc completo  
✅ **Testes** - Unitários, Integração, E2E  
✅ **Logs** - Winston estruturado  
✅ **ORM** - Prisma com migrations e seeds  

### Diferenciais
> "Além dos requisitos, o projeto tem:"
- ✅ Cobertura de testes completa
- ✅ Documentação rica (4 guias + README)
- ✅ Código limpo e bem organizado
- ✅ Pronto para produção

### Encerramento
> "Obrigado! Estou à disposição para perguntas."

---

## 📋 CHECKLIST DURANTE APRESENTAÇÃO

- [ ] Backend rodando (porta 3000)
- [ ] Frontend rodando (porta 5173)
- [ ] Swagger aberto em aba
- [ ] Prisma Studio pronto para abrir
- [ ] VS Code com arquivos importantes abertos
- [ ] Terminal pronto para executar testes
- [ ] Logs visíveis

---

## 💡 DICAS

1. **Fale devagar e com clareza**
2. **Mostre, não apenas fale** - Execute os comandos
3. **Explique o "porquê"** - Não apenas o "o quê"
4. **Destaque os diferenciais** - Testes, logs, documentação
5. **Esteja preparado para perguntas** - Conheça bem o código
6. **Mantenha a calma** - Se algo der errado, explique e continue

---

## ❓ POSSÍVEIS PERGUNTAS

**"Por que escolheu Prisma?"**
> "Prisma oferece type-safety, migrations automáticas, e uma API intuitiva. É mais moderno que ORMs tradicionais."

**"Como funciona a autenticação?"**
> "Uso JWT. No login, gero um token com dados do usuário. O middleware valida esse token em rotas protegidas."

**"Por que separou em camadas?"**
> "Separação de responsabilidades. Model cuida do banco, Service da lógica, Controller do HTTP. Facilita manutenção e testes."

**"Como garantiu a qualidade do código?"**
> "Testes automatizados (unitários, integração, E2E), ESLint, Prettier, e code review seguindo Clean Code e SOLID."

---

## 🎉 BOA SORTE!
