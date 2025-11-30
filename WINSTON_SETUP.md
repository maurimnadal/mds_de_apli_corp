# 📝 Guia de Setup do Winston

## Comando para executar:

```bash
cd backend
npm install winston
```

---

## ✅ O que foi implementado:

1. ✅ **Logger configurado** - `src/config/logger.js`
   - Logs em arquivo: `logs/error.log` e `logs/combined.log`
   - Logs no console (desenvolvimento)
   - Formato JSON estruturado

2. ✅ **Middleware de requisições** - `src/middlewares/logger.middleware.js`
   - Loga todas as requisições HTTP
   - Inclui: método, URL, status, duração, IP

3. ✅ **Logs nos Services**
   - AuthService: registro, login, erros
   - EventService: CRUD de eventos
   - VolunteerService: CRUD de voluntários

4. ✅ **Logs nos Controllers**
   - AuthController: erros de registro e login

5. ✅ **Logs na aplicação**
   - Conexão com banco de dados
   - Erros de conexão

---

## 📊 Níveis de Log:

- **error**: Erros críticos
- **warn**: Avisos (tentativas inválidas)
- **info**: Informações gerais (operações bem-sucedidas)

---

## 📂 Arquivos de Log:

- `logs/error.log` - Apenas erros
- `logs/combined.log` - Todos os logs

---

## 🔍 Exemplo de log estruturado:

```json
{
  "level": "info",
  "message": "Login realizado com sucesso",
  "timestamp": "2025-01-15 10:30:45",
  "userId": 1,
  "email": "admin@ifrs.edu.br"
}
```

---

## 🧪 Testar logs:

1. Inicie o servidor: `npm run dev`
2. Faça login via API
3. Verifique os arquivos em `logs/`
4. Veja logs coloridos no console
