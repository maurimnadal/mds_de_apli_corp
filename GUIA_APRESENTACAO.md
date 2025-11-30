# 🎤 GUIA DE APRESENTAÇÃO - PROVA P2

## 📋 CHECKLIST PRÉ-APRESENTAÇÃO

Antes de começar, certifique-se de ter:
- ✅ MySQL rodando
- ✅ Node.js instalado
- ✅ Chrome instalado (para teste E2E)
- ✅ VS Code com extensão REST Client (opcional)

---

## 🚀 PASSO A PASSO DA APRESENTAÇÃO

### **PARTE 1: SETUP INICIAL (5 min)**

#### 1.1 - Clonar/Abrir o Projeto
```bash
cd prova_p1_apli_corp
```

#### 1.2 - Configurar Backend
```bash
cd backend
npm install
```

**Aguarde a instalação terminar** (pode demorar 1-2 minutos)

#### 1.3 - Configurar Banco de Dados

**Opção A - Criar banco manualmente:**
```sql
CREATE DATABASE IF NOT EXISTS ifrs_voluntariado;
```

**Opção B - Usar script SQL:**
```bash
# Execute o arquivo backend/src/db/script.sql no MySQL
```

#### 1.4 - Configurar Prisma
```bash
npx prisma generate
npx prisma migrate dev --name init
npm run prisma:seed
```

**Resultado esperado:**
```
✅ Prisma Client gerado
✅ Migrations aplicadas
✅ Dados fictícios inseridos (2 usuários + 2 eventos)
```

#### 1.5 - Configurar Frontend
```bash
cd ../frontend
npm install
```

---

### **PARTE 2: EXECUTAR APLICAÇÃO (2 min)**

#### 2.1 - Iniciar Backend
```bash
cd backend
npm run dev
```

**Resultado esperado:**
```
Conectado ao MySQL via Prisma ✅
📘 Swagger UI disponível em:
👉 http://localhost:3000/api-docs
Servidor rodando na porta 3000
```

**⚠️ DEIXE ESTE TERMINAL ABERTO**

#### 2.2 - Iniciar Frontend (NOVO TERMINAL)
```bash
cd frontend
npm run dev
```

**Resultado esperado:**
```
VITE ready in XXX ms
➜ Local: http://localhost:5173/
```

**⚠️ DEIXE ESTE TERMINAL ABERTO**

---

### **PARTE 3: DEMONSTRAÇÃO DA APLICAÇÃO (5 min)**

#### 3.1 - Acessar Frontend
Abra o navegador em: `http://localhost:5173`

#### 3.2 - Fazer Login
- Email: `admin@ifrs.edu.br`
- Senha: `123456`

**Mostre:**
- ✅ Login funciona
- ✅ Redirecionamento para dashboard
- ✅ Token JWT armazenado

#### 3.3 - Navegar pela Aplicação
- ✅ Dashboard (informações do usuário)
- ✅ Eventos (listar eventos)
- ✅ Criar novo evento (se admin)
- ✅ Voluntários (listar)

---

### **PARTE 4: DEMONSTRAÇÃO DA API (5 min)**

#### 4.1 - Acessar Swagger
Abra: `http://localhost:3000/api-docs`

**Mostre:**
- ✅ Documentação completa
- ✅ GET /events documentado
- ✅ POST /events documentado
- ✅ POST /auth/login documentado
- ✅ Schemas definidos
- ✅ Security JWT configurado

#### 4.2 - Testar Endpoints no Swagger

**1. Login:**
```json
POST /auth/login
{
  "email": "admin@ifrs.edu.br",
  "password": "123456"
}
```
**Copie o token retornado**

**2. Autorizar no Swagger:**
- Clique em "Authorize" (cadeado)
- Cole: `Bearer SEU_TOKEN_AQUI`
- Clique em "Authorize"

**3. Listar Eventos:**
```
GET /events
```
**Mostre a lista de eventos retornada**

**4. Criar Evento:**
```json
POST /events
{
  "title": "Evento Teste Apresentação",
  "description": "Criado durante apresentação",
  "date": "2025-12-31",
  "location": "IFRS",
  "max_volunteers": 30
}
```

---

### **PARTE 5: TESTES AUTOMATIZADOS (5 min)**

#### 5.1 - Testes Unitários
```bash
cd backend
npm run test:unit
```

**Mostre:**
- ✅ Testes de AuthService (6 cenários)
- ✅ Testes de EventService (7 cenários)
- ✅ Todos passando

#### 5.2 - Testes de Integração
```bash
npm run test:integration
```

**Mostre:**
- ✅ Testes de rotas /auth
- ✅ Testes de rotas /events
- ✅ Validação de autenticação
- ✅ Todos passando

#### 5.3 - Teste E2E (Selenium)
```bash
npm run test:e2e
```

**Resultado esperado:**
```
🚀 Iniciando teste E2E de Login...
✅ Navegador iniciado
✅ Página de login carregada
✅ Elementos do formulário encontrados
✅ Credenciais preenchidas
✅ Botão de login clicado
✅ Redirecionado para: http://localhost:5173/dashboard
✅ TESTE E2E PASSOU: Login realizado com sucesso!
✅ Navegador fechado
```

#### 5.4 - Cobertura de Testes
```bash
npm test
```

**Mostre o relatório de cobertura no terminal**

---

### **PARTE 6: LOGS (2 min)**

#### 6.1 - Verificar Logs em Arquivo
```bash
cd backend
cat logs/combined.log
```

**Mostre:**
- ✅ Logs estruturados (JSON)
- ✅ Requisições HTTP logadas
- ✅ Operações de autenticação
- ✅ CRUD de eventos

#### 6.2 - Logs de Erro
```bash
cat logs/error.log
```

**Mostre que erros são logados separadamente**

---

### **PARTE 7: PRISMA (3 min)**

#### 7.1 - Abrir Prisma Studio
```bash
npx prisma studio
```

**Abre em:** `http://localhost:5555`

**Mostre:**
- ✅ Interface visual do banco
- ✅ Tabela User com dados
- ✅ Tabela Event com dados
- ✅ Relacionamentos

#### 7.2 - Mostrar Schema
```bash
cat prisma/schema.prisma
```

**Explique:**
- ✅ Models definidos
- ✅ Relacionamentos
- ✅ Enums (Role)

#### 7.3 - Mostrar Seeds
```bash
cat prisma/seed.js
```

**Explique:**
- ✅ Dados fictícios
- ✅ Senhas hasheadas
- ✅ Relacionamentos criados

---

### **PARTE 8: CÓDIGO E ARQUITETURA (5 min)**

#### 8.1 - Mostrar Estrutura de Pastas
```bash
tree -L 3 -I node_modules
```

**Explique:**
- ✅ Separação de camadas
- ✅ Models, Services, Controllers
- ✅ Middlewares
- ✅ Testes organizados

#### 8.2 - Mostrar JSDoc
Abra no VS Code:
- `src/models/user.model.js`
- `src/services/auth.service.js`
- `src/controllers/auth.controller.js`

**Mostre:**
- ✅ Documentação completa
- ✅ Parâmetros explicados
- ✅ Retornos documentados

#### 8.3 - Mostrar Clean Code
Abra qualquer arquivo e mostre:
- ✅ Nomes claros
- ✅ Funções pequenas
- ✅ Sem duplicação
- ✅ Código legível

---

### **PARTE 9: TESTES MANUAIS (REST Client) (3 min)**

#### 9.1 - Abrir tests.rest
```bash
code tests/tests.rest
```

#### 9.2 - Executar Requests
Clique em "Send Request" em cada bloco:

1. **Registro:**
```http
POST http://localhost:3000/auth/register
```

2. **Login:**
```http
POST http://localhost:3000/auth/login
```

3. **Listar Eventos:**
```http
GET http://localhost:3000/events
```

**Mostre os resultados no painel lateral**

---

### **PARTE 10: ENCERRAMENTO (2 min)**

#### 10.1 - Mostrar Documentação
Abra no VS Code:
- `README.md`
- `CHECKLIST_REQUISITOS.md`
- `RESUMO_IMPLEMENTACAO.md`

#### 10.2 - Destacar Pontos Fortes
- ✅ Todos os requisitos atendidos
- ✅ Testes completos (unitários, integração, E2E)
- ✅ Documentação rica (Swagger + JSDoc)
- ✅ Logs estruturados
- ✅ Prisma ORM com migrations e seeds
- ✅ Clean Code e SOLID
- ✅ Segurança JWT

---

## 🎯 ROTEIRO RESUMIDO (30 min)

| Tempo | Atividade |
|-------|-----------|
| 0-5 min | Setup (npm install, prisma, seeds) |
| 5-7 min | Executar backend + frontend |
| 7-12 min | Demo aplicação (login, CRUD) |
| 12-17 min | Demo API (Swagger, endpoints) |
| 17-22 min | Testes (unitários, integração, E2E) |
| 22-24 min | Logs (arquivos, estrutura) |
| 24-27 min | Prisma (Studio, schema, seeds) |
| 27-32 min | Código (arquitetura, JSDoc, Clean Code) |
| 32-35 min | Testes manuais (REST Client) |
| 35-37 min | Documentação e encerramento |

---

## 🆘 TROUBLESHOOTING

### Erro: "Cannot connect to MySQL"
```bash
# Verifique se MySQL está rodando
# Windows: services.msc → MySQL
# Verifique credenciais no .env
```

### Erro: "Port 3000 already in use"
```bash
# Mate o processo na porta 3000
# Windows: netstat -ano | findstr :3000
# taskkill /PID <PID> /F
```

### Erro: "Prisma Client not generated"
```bash
npx prisma generate
```

### Erro no teste E2E: "ChromeDriver not found"
```bash
npm install --save-dev chromedriver
```

### Frontend não carrega
```bash
# Verifique se backend está rodando
# Verifique CORS no backend (deve permitir localhost:5173)
```

---

## 📝 DICAS PARA APRESENTAÇÃO

1. **Prepare o ambiente antes** - Faça o setup completo antes de apresentar
2. **Tenha 2 terminais abertos** - Um para backend, outro para frontend
3. **Teste tudo antes** - Execute todos os comandos antes da apresentação
4. **Tenha o Swagger aberto** - Facilita demonstração da API
5. **Mostre os logs em tempo real** - Abra `logs/combined.log` em outro terminal
6. **Prepare dados de teste** - Tenha emails/senhas anotados
7. **Explique enquanto executa** - Não apenas mostre, explique o que está fazendo
8. **Destaque os diferenciais** - Testes, logs, Prisma, documentação

---

## ✅ CHECKLIST FINAL

Antes de apresentar, verifique:
- [ ] MySQL rodando
- [ ] Dependências instaladas (backend + frontend)
- [ ] Prisma configurado (generate + migrate + seed)
- [ ] Backend rodando (porta 3000)
- [ ] Frontend rodando (porta 5173)
- [ ] Swagger acessível
- [ ] Testes passando
- [ ] Logs sendo gerados
- [ ] Prisma Studio funciona
- [ ] REST Client configurado

---

## 🎉 BOA APRESENTAÇÃO!

Siga este guia e sua apresentação será completa e profissional!
