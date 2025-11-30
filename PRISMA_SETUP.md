# 🔧 Guia de Setup do Prisma

## Comandos para executar (na ordem):

### 1. Instalar dependências do Prisma
```bash
cd backend
npm install prisma @prisma/client
```

### 2. Gerar o Prisma Client
```bash
npx prisma generate
```

### 3. Criar a migration inicial (sincronizar com banco existente)
```bash
npx prisma db pull
npx prisma migrate dev --name init
```

**OU** se preferir criar do zero:
```bash
npx prisma migrate dev --name init
```

### 4. Popular o banco com dados fictícios (seed)
```bash
npm run prisma:seed
```

### 5. Testar a aplicação
```bash
npm run dev
```

### 6. (Opcional) Abrir Prisma Studio para visualizar dados
```bash
npm run prisma:studio
```

---

## ✅ Verificações

Após executar os comandos, verifique:

1. ✅ Pasta `node_modules/@prisma/client` foi criada
2. ✅ Banco de dados tem as tabelas `users` e `events`
3. ✅ Dados fictícios foram inseridos
4. ✅ API está rodando em `http://localhost:3000`
5. ✅ Swagger está acessível em `http://localhost:3000/api-docs`

---

## 🔍 Comandos úteis do Prisma

- `npx prisma studio` - Interface visual do banco
- `npx prisma migrate dev` - Criar nova migration
- `npx prisma db push` - Sincronizar schema sem migration
- `npx prisma generate` - Regenerar Prisma Client
- `npm run prisma:seed` - Executar seed novamente

---

## ⚠️ Troubleshooting

### Erro: "Can't reach database server"
- Verifique se o MySQL está rodando
- Confirme as credenciais no arquivo `.env`

### Erro: "Table already exists"
- Use `npx prisma db pull` para sincronizar com banco existente
- Ou delete as tabelas e rode `npx prisma migrate dev` novamente

### Erro no seed
- Verifique se as migrations foram aplicadas
- Confirme que o DATABASE_URL está correto no `.env`
