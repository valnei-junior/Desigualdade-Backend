# 🔧 Desigualdade Backend - API REST

Backend da plataforma CarreiraHub de Educação e Empregabilidade.

## 🚀 Instalação

```bash
npm install
```

## ▶️ Execução

```bash
npm run start
# ou
node index.js
```

O servidor será iniciado em **http://localhost:4000**

## 📋 Endpoints da API

### Healthcheck
- `GET /api/health` - Verifica se o servidor está funcionando

### Autenticação
- `POST /api/register` - Registrar usuário (requer aceites de Termos/Security/LGPD)
- `POST /api/login` - Autenticar usuário (retorna JWT quando válido)
- `POST /api/auth/forgot-password` - Solicitar redefinição de senha
- `POST /api/auth/reset-password` - Redefinir senha
- `POST /api/auth/request-email-verification` - Solicitar código de verificação
- `POST /api/auth/verify-email` - Verificar email com código
- `POST /api/auth/2fa/setup` - Configurar 2FA
- `POST /api/auth/2fa/verify` - Verificar código 2FA

### Vagas (Jobs)
- `GET /api/jobs` - Listar todas as vagas ativas
- `GET /api/jobs/company/:companyId` - Listar vagas de uma empresa
- `POST /api/jobs` - Criar nova vaga
- `PUT /api/jobs/:jobId` - Atualizar vaga
- `DELETE /api/jobs/:jobId` - Excluir vaga

### Candidaturas (Applications)
- `POST /api/applications` - Candidatar-se a uma vaga
- `GET /api/applications/company/:companyId` - Listar candidaturas de uma empresa
- `PUT /api/applications/:applicationId` - Atualizar status da candidatura
- `DELETE /api/applications/:applicationId` - Excluir candidatura

### Upload
- `POST /api/upload-resume` - Upload de currículo (PDF)

## 🗄️ Banco de Dados

Utiliza SQLite com as seguintes tabelas:
- `users` - Usuários do sistema
- `user_security` - Configurações de segurança (2FA, verificação de email)
- `jobs` - Vagas de emprego
- `applications` - Candidaturas
- `password_resets` - Tokens de redefinição de senha
- `email_verifications` - Códigos de verificação de email

## 🔒 Fluxo de Segurança

1. **Cadastro** - Aceitar Termos, Security e LGPD
2. **Verificação de Email** - Código enviado por email
3. **Setup 2FA** - Configurar autenticador TOTP
4. **Login** - Senha + código TOTP → JWT retornado

## 📦 Dependências Principais

- `express` - Framework web
- `sqlite3` - Banco de dados
- `bcryptjs` - Hash de senhas
- `speakeasy` - Autenticação 2FA (TOTP)
- `jsonwebtoken` - Tokens JWT
- `nodemailer` - Envio de emails

## 🧪 Testes

Scripts de teste disponíveis na pasta `scripts_tests/`:
- `test_upload_http.cjs` - Teste de upload
- `test_register.cjs` - Teste de registro
- `play_register_login.cjs` - Teste completo de fluxo

---

**Versão:** 1.0.0  
**Última Atualização:** Março 2026
