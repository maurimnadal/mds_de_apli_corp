# 🧪 Guia de Setup dos Testes

## Comandos para executar:

### 1. Instalar dependências de teste
```bash
cd backend
npm install --save-dev jest supertest @types/jest selenium-webdriver chromedriver
```

---

## 🎯 Executar Testes

### Todos os testes com coverage
```bash
npm test
```

### Apenas testes unitários
```bash
npm run test:unit
```

### Apenas testes de integração
```bash
npm run test:integration
```

### Teste E2E (Selenium)
```bash
npm run test:e2e
```

**⚠️ Importante para E2E:**
- Backend deve estar rodando em `http://localhost:3000`
- Frontend deve estar rodando em `http://localhost:5173`

---

## ✅ O que foi implementado:

### 1. Testes Unitários (Jest)
- ✅ `tests/unit/auth.service.test.js`
  - Registro de usuário (sucesso e erro)
  - Login (sucesso e erro)
  - Validações de campos

- ✅ `tests/unit/event.service.test.js`
  - Listar eventos
  - Criar evento (sucesso e erro)
  - Atualizar evento (sucesso e erro)
  - Remover evento (sucesso e erro)

### 2. Testes de Integração (Jest + Supertest)
- ✅ `tests/integration/auth.test.js`
  - POST /auth/register
  - POST /auth/login
  - Validações de autenticação

- ✅ `tests/integration/events.test.js`
  - GET /events (com e sem autenticação)
  - POST /events (com e sem autenticação)
  - Validações de autorização

### 3. Teste E2E (Selenium)
- ✅ `tests/e2e/login.test.js`
  - Fluxo completo de login no frontend
  - Preenchimento de formulário
  - Redirecionamento para dashboard

---

## 📊 Cobertura de Testes

Após executar `npm test`, verifique o relatório em:
- Console: Resumo da cobertura
- `coverage/lcov-report/index.html`: Relatório visual

---

## 🔍 Estrutura de Testes

```
tests/
├── unit/                    # Testes unitários (Services)
│   ├── auth.service.test.js
│   └── event.service.test.js
├── integration/             # Testes de integração (API)
│   ├── auth.test.js
│   └── events.test.js
└── e2e/                     # Testes ponta a ponta
    └── login.test.js
```

---

## 🧪 Cenários Testados

### Sucesso ✅
- Registro de usuário válido
- Login com credenciais corretas
- Criação de evento autenticado
- Listagem de eventos
- Atualização e remoção

### Erro ❌
- Campos obrigatórios faltando
- Credenciais inválidas
- Usuário já existente
- Acesso sem autenticação
- Recursos não encontrados

---

## 🛠️ Troubleshooting

### Erro: "Cannot find module"
```bash
npm install
```

### Erro no E2E: "ChromeDriver not found"
```bash
npm install --save-dev chromedriver
```

### Erro: "ECONNREFUSED"
- Certifique-se de que o backend está rodando
- Verifique se o banco de dados está acessível

---

## 📈 Próximos Passos

1. Execute os testes: `npm test`
2. Verifique a cobertura
3. Execute o teste E2E com frontend rodando
