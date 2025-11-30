# 🔍 PROBLEMAS ENCONTRADOS E CORREÇÕES

## ⚠️ PROBLEMAS CRÍTICOS

### 1. EventForm - maxVolunteers não tem valor padrão
**Arquivo:** `frontend/src/components/EventForm.jsx`

**Problema:**
```javascript
const [maxVolunteers, setMaxVolunteers] = useState(); // undefined
```

**Impacto:** Campo vazio pode causar erro ao criar evento

**Correção necessária:** Definir valor padrão
```javascript
const [maxVolunteers, setMaxVolunteers] = useState(50);
```

---

### 2. EventList - Formato de data pode estar incorreto
**Arquivo:** `frontend/src/components/EventList.jsx`

**Problema:** 
- Data vem do banco como DateTime
- Pode exibir formato completo (2025-12-31T00:00:00.000Z)

**Impacto:** Data exibida de forma feia no frontend

**Correção necessária:** Formatar data antes de exibir

---

### 3. EventList - maxVolunteers vs max_volunteers
**Arquivo:** `frontend/src/components/EventList.jsx`

**Problema:**
```javascript
<span>Máx. voluntários: {event.max_volunteers}</span>
```

**Verificar:** Prisma retorna `maxVolunteers` (camelCase) ou `max_volunteers` (snake_case)?

**Impacto:** Campo pode não aparecer

---

## ⚠️ PROBLEMAS MÉDIOS

### 4. EventForm - Conversão de maxVolunteers
**Arquivo:** `frontend/src/components/EventForm.jsx`

**Problema:**
```javascript
max_volunteers: maxVolunteers  // pode ser string
```

**Impacto:** Backend pode receber string ao invés de número

**Correção necessária:**
```javascript
max_volunteers: parseInt(maxVolunteers) || 50
```

---

### 5. Logs - Diretório pode não existir
**Arquivo:** `backend/src/config/logger.js`

**Problema:** Winston tenta escrever em `logs/` mas diretório pode não existir

**Impacto:** Erro ao iniciar aplicação se pasta não existir

**Solução:** Já criamos `logs/.gitkeep`, mas verificar se existe

---

### 6. Prisma - Migrations podem não estar aplicadas
**Problema:** Se usuário não rodar `npx prisma migrate dev`

**Impacto:** Tabelas não existem, aplicação quebra

**Solução:** Documentar bem no README

---

## ⚠️ PROBLEMAS MENORES

### 7. EventList - handleEdit usa prompt()
**Arquivo:** `frontend/src/components/EventList.jsx`

**Problema:** Usar `prompt()` não é ideal para UX

**Impacto:** Experiência ruim, mas funciona

**Sugestão:** Aceitar como está ou criar modal

---

### 8. Testes - Dependem de dados no banco
**Arquivo:** `tests/integration/*.test.js`

**Problema:** Testes de integração dependem de usuário admin existir

**Impacto:** Se banco estiver vazio, testes falham

**Solução:** Seeds devem ser executados antes dos testes

---

### 9. Teste E2E - Requer frontend rodando
**Arquivo:** `tests/e2e/login.test.js`

**Problema:** Teste falha se frontend não estiver rodando

**Impacto:** Erro ao executar `npm run test:e2e`

**Solução:** Documentar que frontend deve estar rodando

---

## ✅ CORREÇÕES NECESSÁRIAS

### CORREÇÃO 1: EventForm - maxVolunteers
**Prioridade:** ALTA

### CORREÇÃO 2: EventList - Formato de data
**Prioridade:** MÉDIA

### CORREÇÃO 3: EventList - Nome do campo
**Prioridade:** ALTA

### CORREÇÃO 4: EventForm - Conversão de número
**Prioridade:** MÉDIA

---

## 🔧 VERIFICAÇÕES ANTES DE APRESENTAR

### Backend
- [ ] MySQL rodando
- [ ] Prisma migrations aplicadas (`npx prisma migrate dev`)
- [ ] Seeds executados (`npm run prisma:seed`)
- [ ] Diretório `logs/` existe
- [ ] Dependências instaladas (`npm install`)

### Frontend
- [ ] Dependências instaladas (`npm install`)
- [ ] Backend rodando (porta 3000)
- [ ] CORS configurado corretamente

### Testes
- [ ] Banco de dados populado (seeds)
- [ ] Backend rodando para testes de integração
- [ ] Frontend rodando para teste E2E

---

## 🎯 AÇÕES IMEDIATAS

1. **Corrigir EventForm** - Adicionar valor padrão
2. **Verificar campo maxVolunteers** - Testar se Prisma retorna camelCase
3. **Formatar data no frontend** - Melhorar exibição
4. **Testar fluxo completo** - Do login até criar evento
