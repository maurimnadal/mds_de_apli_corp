# ✅ VERIFICAÇÃO PRÉ-EXECUÇÃO

## 🔍 CHECKLIST COMPLETO

Execute este checklist ANTES de apresentar ou testar o projeto.

---

## 1️⃣ AMBIENTE

### MySQL
```bash
# Windows: Verificar se MySQL está rodando
services.msc
# Procurar por "MySQL" e verificar se está "Em execução"
```

**Status:** [ ] MySQL rodando

### Node.js
```bash
node --version
# Deve ser 18+
```

**Status:** [ ] Node.js instalado

---

## 2️⃣ BACKEND

### Dependências
```bash
cd backend
npm install
```

**Verificar:**
- [ ] `node_modules/` criado
- [ ] Sem erros de instalação

### Prisma
```bash
# Gerar Prisma Client
npx prisma generate

# Verificar se gerou
ls node_modules/.prisma/client
# ou
dir node_modules\.prisma\client
```

**Status:** [ ] Prisma Client gerado

### Banco de Dados
```bash
# Criar banco (se não existir)
mysql -u root -p
CREATE DATABASE IF NOT EXISTS ifrs_voluntariado;
exit;

# Aplicar migrations
npx prisma migrate dev --name init

# Popular com seeds
npm run prisma:seed
```

**Verificar:**
- [ ] Banco `ifrs_voluntariado` existe
- [ ] Tabelas `users` e `events` criadas
- [ ] 2 usuários inseridos (admin e voluntário)
- [ ] 2 eventos inseridos

### Logs
```bash
# Verificar se diretório existe
ls logs/
# ou
dir logs\
```

**Status:** [ ] Diretório `logs/` existe

### Variáveis de Ambiente
```bash
cat .env
# ou
type .env
```

**Verificar:**
```env
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
DB_NAME=ifrs_voluntariado
JWT_SECRET=troque_esta_chave_por_uma_segura
DATABASE_URL="mysql://root:@localhost:3306/ifrs_voluntariado"
```

**Status:** [ ] `.env` configurado corretamente

---

## 3️⃣ FRONTEND

### Dependências
```bash
cd frontend
npm install
```

**Verificar:**
- [ ] `node_modules/` criado
- [ ] Sem erros de instalação

### Configuração API
```bash
cat src/api/api.js
# ou
type src\api\api.js
```

**Verificar:**
```javascript
const API_URL = "http://localhost:3000";
```

**Status:** [ ] URL da API correta

---

## 4️⃣ TESTES

### Dependências de Teste
```bash
cd backend
npm list jest supertest selenium-webdriver chromedriver
```

**Verificar:**
- [ ] jest instalado
- [ ] supertest instalado
- [ ] selenium-webdriver instalado
- [ ] chromedriver instalado

### Executar Testes
```bash
# Testes unitários
npm run test:unit

# Testes de integração (backend deve estar rodando)
npm run test:integration
```

**Status:** 
- [ ] Testes unitários passam
- [ ] Testes de integração passam

---

## 5️⃣ EXECUÇÃO

### Iniciar Backend
```bash
cd backend
npm run dev
```

**Verificar no console:**
```
Conectado ao MySQL via Prisma ✅
📘 Swagger UI disponível em:
👉 http://localhost:3000/api-docs
Servidor rodando em http://localhost:3000
```

**Status:** [ ] Backend rodando sem erros

### Testar Backend
Abrir navegador: `http://localhost:3000`

**Deve mostrar:** "API funcionando 🚀"

**Status:** [ ] Backend acessível

### Testar Swagger
Abrir navegador: `http://localhost:3000/api-docs`

**Deve mostrar:** Interface do Swagger

**Status:** [ ] Swagger acessível

### Iniciar Frontend (NOVO TERMINAL)
```bash
cd frontend
npm run dev
```

**Verificar no console:**
```
VITE ready in XXX ms
➜ Local: http://localhost:5173/
```

**Status:** [ ] Frontend rodando sem erros

### Testar Frontend
Abrir navegador: `http://localhost:5173`

**Deve mostrar:** Página de login

**Status:** [ ] Frontend acessível

---

## 6️⃣ TESTE FUNCIONAL COMPLETO

### Login
1. Acessar: `http://localhost:5173/login`
2. Email: `admin@ifrs.edu.br`
3. Senha: `123456`
4. Clicar em "Entrar"

**Resultado esperado:** Redirecionar para `/dashboard`

**Status:** [ ] Login funciona

### Dashboard
**Deve mostrar:**
- Mensagem: "Bem-vindo ao dashboard, Admin IFRS!"
- Dados do usuário (id, name, email, role)

**Status:** [ ] Dashboard funciona

### Listar Eventos
1. Clicar em "Eventos" no menu
2. Deve mostrar lista de eventos

**Resultado esperado:** 2 eventos listados

**Status:** [ ] Listagem funciona

### Criar Evento (Admin)
1. Preencher formulário:
   - Título: "Evento Teste"
   - Descrição: "Teste de criação"
   - Data: "2025-12-31"
   - Local: "IFRS"
   - Max voluntários: 30
2. Clicar em "Criar Evento"

**Resultado esperado:** Mensagem de sucesso

**Status:** [ ] Criação funciona

---

## 7️⃣ TESTE DA API (Swagger)

### Login via Swagger
1. Abrir: `http://localhost:3000/api-docs`
2. Expandir `POST /auth/login`
3. Clicar em "Try it out"
4. Body:
```json
{
  "email": "admin@ifrs.edu.br",
  "password": "123456"
}
```
5. Clicar em "Execute"

**Resultado esperado:** Status 200, token retornado

**Status:** [ ] Login via API funciona

### Autorizar no Swagger
1. Clicar no botão "Authorize" (cadeado)
2. Colar: `Bearer SEU_TOKEN_AQUI`
3. Clicar em "Authorize"

**Status:** [ ] Autorização configurada

### Listar Eventos via Swagger
1. Expandir `GET /events`
2. Clicar em "Try it out"
3. Clicar em "Execute"

**Resultado esperado:** Status 200, lista de eventos

**Status:** [ ] GET /events funciona

### Criar Evento via Swagger
1. Expandir `POST /events`
2. Clicar em "Try it out"
3. Body:
```json
{
  "title": "Evento Swagger",
  "description": "Criado via Swagger",
  "date": "2025-12-31",
  "location": "IFRS",
  "max_volunteers": 40
}
```
4. Clicar em "Execute"

**Resultado esperado:** Status 201, evento criado

**Status:** [ ] POST /events funciona

---

## 8️⃣ VERIFICAR LOGS

### Logs em Arquivo
```bash
cd backend
cat logs/combined.log
# ou
type logs\combined.log
```

**Deve conter:**
- Logs de requisições HTTP
- Logs de login
- Logs de operações CRUD

**Status:** [ ] Logs sendo gerados

### Logs no Console
Verificar terminal do backend

**Deve mostrar:**
- Requisições coloridas
- Informações de operações

**Status:** [ ] Logs no console funcionando

---

## 9️⃣ VERIFICAR PRISMA STUDIO

```bash
cd backend
npx prisma studio
```

**Abrir:** `http://localhost:5555`

**Verificar:**
- [ ] Tabela User com 2 registros
- [ ] Tabela Event com registros
- [ ] Relacionamentos visíveis

**Status:** [ ] Prisma Studio funciona

---

## 🔟 TESTE E2E

**IMPORTANTE:** Backend E frontend devem estar rodando!

```bash
cd backend
npm run test:e2e
```

**Resultado esperado:**
```
✅ Navegador iniciado
✅ Página de login carregada
✅ Elementos do formulário encontrados
✅ Credenciais preenchidas
✅ Botão de login clicado
✅ Redirecionado para: http://localhost:5173/dashboard
✅ TESTE E2E PASSOU
✅ Navegador fechado
```

**Status:** [ ] Teste E2E passa

---

## ✅ RESUMO FINAL

### Todos os itens devem estar marcados:

**Ambiente:**
- [ ] MySQL rodando
- [ ] Node.js instalado

**Backend:**
- [ ] Dependências instaladas
- [ ] Prisma configurado
- [ ] Banco populado
- [ ] Logs funcionando
- [ ] Backend rodando

**Frontend:**
- [ ] Dependências instaladas
- [ ] Frontend rodando

**Funcionalidades:**
- [ ] Login funciona
- [ ] Dashboard funciona
- [ ] Listar eventos funciona
- [ ] Criar evento funciona
- [ ] API via Swagger funciona

**Testes:**
- [ ] Testes unitários passam
- [ ] Testes de integração passam
- [ ] Teste E2E passa

**Extras:**
- [ ] Logs sendo gerados
- [ ] Prisma Studio funciona

---

## 🚨 SE ALGO FALHAR

### Backend não inicia
1. Verificar se MySQL está rodando
2. Verificar credenciais no `.env`
3. Verificar se porta 3000 está livre

### Frontend não conecta
1. Verificar se backend está rodando
2. Verificar CORS no backend
3. Verificar URL da API no frontend

### Testes falham
1. Verificar se banco está populado (seeds)
2. Verificar se backend está rodando (integração)
3. Verificar se frontend está rodando (E2E)

### Prisma não funciona
1. Executar `npx prisma generate`
2. Executar `npx prisma migrate dev`
3. Verificar DATABASE_URL no `.env`

---

## 🎉 TUDO PRONTO!

Se todos os itens estão marcados, o projeto está 100% funcional e pronto para apresentação!
