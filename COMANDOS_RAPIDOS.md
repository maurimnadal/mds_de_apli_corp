# ⚡ COMANDOS RÁPIDOS - APRESENTAÇÃO

## 🚀 SETUP COMPLETO (Execute na ordem)

### 1. Backend
```bash
cd backend
npm install
npx prisma generate
npx prisma migrate dev --name init
npm run prisma:seed
```

### 2. Frontend
```bash
cd frontend
npm install
```

---

## 🎯 EXECUTAR APLICAÇÃO

### Terminal 1 - Backend
```bash
cd backend
npm run dev
```
**Deixe rodando!**

### Terminal 2 - Frontend
```bash
cd frontend
npm run dev
```
**Deixe rodando!**

---

## 🧪 TESTES

### Todos os testes
```bash
cd backend
npm test
```

### Testes unitários
```bash
npm run test:unit
```

### Testes de integração
```bash
npm run test:integration
```

### Teste E2E
```bash
npm run test:e2e
```

---

## 📊 PRISMA

### Abrir Prisma Studio
```bash
cd backend
npx prisma studio
```
**Abre em:** http://localhost:5555

### Ver schema
```bash
cat prisma/schema.prisma
```

### Recriar banco (se necessário)
```bash
npx prisma migrate reset
npm run prisma:seed
```

---

## 📝 LOGS

### Ver logs combinados
```bash
cd backend
cat logs/combined.log
```

### Ver apenas erros
```bash
cat logs/error.log
```

### Acompanhar logs em tempo real (Windows)
```bash
Get-Content logs/combined.log -Wait -Tail 10
```

---

## 🌐 URLs IMPORTANTES

- **Frontend:** http://localhost:5173
- **Backend:** http://localhost:3000
- **Swagger:** http://localhost:3000/api-docs
- **Prisma Studio:** http://localhost:5555

---

## 🔑 CREDENCIAIS DE TESTE

### Admin
- Email: `admin@ifrs.edu.br`
- Senha: `123456`

### Voluntário
- Email: `joao@ifrs.edu.br`
- Senha: `123456`

---

## 🆘 COMANDOS DE EMERGÊNCIA

### Matar processo na porta 3000 (Windows)
```bash
netstat -ano | findstr :3000
taskkill /PID <PID> /F
```

### Matar processo na porta 5173 (Windows)
```bash
netstat -ano | findstr :5173
taskkill /PID <PID> /F
```

### Limpar node_modules e reinstalar
```bash
rm -rf node_modules package-lock.json
npm install
```

### Resetar banco de dados
```bash
cd backend
npx prisma migrate reset --force
npm run prisma:seed
```

---

## 📋 ORDEM DE APRESENTAÇÃO

1. **Setup** (5 min)
   ```bash
   cd backend && npm install
   npx prisma generate && npx prisma migrate dev && npm run prisma:seed
   cd ../frontend && npm install
   ```

2. **Executar** (2 min)
   ```bash
   # Terminal 1
   cd backend && npm run dev
   
   # Terminal 2
   cd frontend && npm run dev
   ```

3. **Demonstrar** (15 min)
   - Frontend: http://localhost:5173
   - Swagger: http://localhost:3000/api-docs
   - Prisma Studio: `npx prisma studio`

4. **Testes** (5 min)
   ```bash
   npm run test:unit
   npm run test:integration
   npm run test:e2e
   ```

5. **Logs** (2 min)
   ```bash
   cat logs/combined.log
   ```

6. **Código** (5 min)
   - Mostrar arquitetura
   - Mostrar JSDoc
   - Mostrar testes

---

## ✅ CHECKLIST PRÉ-APRESENTAÇÃO

```bash
# Execute tudo de uma vez para verificar
cd backend
npm install && \
npx prisma generate && \
npx prisma migrate dev --name init && \
npm run prisma:seed && \
npm test && \
cd ../frontend && \
npm install
```

Se tudo passar, está pronto! ✅
