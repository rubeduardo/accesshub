# 🔧 Setup de Desenvolvimento - AccessHub

Guia completo para configurar o ambiente de desenvolvimento do AccessHub.

---

## 📋 Pré-requisitos

### Sistema Operacional
- Linux, macOS ou Windows (com WSL2)
- 4GB RAM mínimo (8GB recomendado)
- 5GB espaço livre em disco

### Ferramentas Obrigatórias

```bash
# Git
git --version  # 2.30+

# Node.js
node --version # v18+ (18 ou 20 recomendado)
npm --version  # 9+

# Python
python --version # 3.10+
pip --version

# Docker & Docker Compose (opcional mas recomendado)
docker --version
docker-compose --version
```

### IDEs Recomendadas
- **VS Code** (recomendado) com extensões:
  - ESLint
  - Prettier
  - Python
  - Pylance
  - Thunder Client (testar APIs)

---

## 🚀 Instalação Rápida (5 minutos)

### 1. Clone o Repositório

```bash
git clone https://github.com/rubeduardo/accesshub.git
cd accesshub
```

### 2. Setup com Docker Compose (Recomendado)

```bash
# Inicie todos os serviços
docker-compose up -d

# Verificar se está rodando
docker-compose ps

# Logs do serviço específico
docker-compose logs -f backend
docker-compose logs -f frontend
```

Pronto! Acesse:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8000
- **API Docs (Swagger)**: http://localhost:8000/docs

### 3. Setup Manual (Sem Docker)

#### 3.1 Backend

```bash
# Entre na pasta do backend
cd backend

# Crie um virtual environment
python -m venv venv

# Ative o ambiente
# No macOS/Linux:
source venv/bin/activate
# No Windows:
venv\Scripts\activate

# Instale dependências
pip install -r requirements.txt

# Configure as variáveis de ambiente
cp .env.example .env.local
# Edite .env.local com suas configurações

# Crie as tabelas no banco
alembic upgrade head

# Inicie o servidor
uvicorn app.main:app --reload --port 8000
```

#### 3.2 Frontend

```bash
# Em outro terminal, entre na pasta do frontend
cd frontend

# Instale dependências
npm install

# Configure as variáveis de ambiente
cp .env.example .env.local
# Certifique-se de que NEXT_PUBLIC_API_URL apontar para http://localhost:8000

# Inicie o servidor de desenvolvimento
npm run dev
```

#### 3.3 Database (PostgreSQL)

```bash
# Instale PostgreSQL se ainda não tiver
# macOS:
brew install postgresql

# Linux (Ubuntu):
sudo apt-get install postgresql postgresql-contrib

# Windows:
# Baixe do https://www.postgresql.org/download/windows/

# Inicie o PostgreSQL
# macOS:
brew services start postgresql

# Linux:
sudo service postgresql start

# Crie um banco de dados
createdb accesshub

# Verifique a conexão
psql accesshub
# Digite: \dt (para listar tabelas)
# Digite: \q (para sair)
```

---

## 📦 Estrutura do Projeto

```
accesshub/
├── frontend/                  # Next.js 14
│   ├── app/                   # Rotas e páginas
│   ├── components/            # Componentes React
│   ├── lib/                   # Utilitários
│   ├── package.json
│   └── .env.example
│
├── backend/                   # FastAPI
│   ├── app/
│   │   ├── api/               # Endpoints
│   │   ├── models/            # SQLAlchemy models
│   │   ├── schemas/           # Pydantic schemas
│   │   ├── services/          # Lógica de negócio
│   │   └── main.py            # Entry point
│   ├── migrations/            # Alembic
│   ├── tests/                 # Testes
│   ├── requirements.txt
│   └── .env.example
│
├── database/                  # Esquema e migrations
├── docs/                      # Documentação
├── docker-compose.yml
├── .env.example
└── README.md
```

---

## 🔐 Configuração de Variáveis de Ambiente

### Frontend (.env.local)

```env
# URL da API
NEXT_PUBLIC_API_URL=http://localhost:8000

# Ambiente
NEXT_PUBLIC_ENV=development
```

### Backend (.env.local)

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/accesshub

# JWT Secret
SECRET_KEY=seu-secret-muito-seguro-aqui-min-32-chars

# Ambiente
ENVIRONMENT=development

# CORS
ALLOWED_ORIGINS=http://localhost:3000

# Email (opcional inicialmente)
SMTP_SERVER=smtp.gmail.com
SMTP_PORT=587
SMTP_USERNAME=seu-email@gmail.com
SMTP_PASSWORD=sua-senha-app

# QR Code
QR_CODE_SIZE=200
QR_CODE_ERROR_CORRECTION=M
```

---

## 🗄️ Database Setup

### Criar Banco de Dados

```bash
# Com Docker (recomendado)
docker-compose exec db psql -U postgres -c "CREATE DATABASE accesshub;"

# Ou manual
createdb accesshub
```

### Executar Migrations

```bash
# Entre na pasta backend
cd backend

# Crie a primeira migration
alembic revision --autogenerate -m "Initial schema"

# Aplique as migrations
alembic upgrade head

# Verificar status
alembic current
```

### Seed de Dados (Desenvolvimento)

```bash
# Backend
cd backend

# Adicionar dados de teste
python -m app.scripts.seed_db

# Você terá:
# - 1 organização (ADEMOC)
# - 3 usuários (admin, manager, viewer)
# - 5 associados de teste
```

---

## 🧪 Testes

### Frontend

```bash
cd frontend

# Rodar testes
npm test

# Com cobertura
npm test -- --coverage

# Específico
npm test -- --testPathPattern="auth"

# Watch mode
npm test -- --watch
```

### Backend

```bash
cd backend

# Rodar testes
pytest

# Com cobertura
pytest --cov=app

# Específico
pytest tests/test_auth.py -v

# Watch mode (com pytest-watch)
ptw
```

---

## 🔍 Verificar Instalação

### Checklist

```bash
# ✅ Backend rodando
curl http://localhost:8000/docs

# ✅ Frontend rodando
curl http://localhost:3000

# ✅ Database conectado
# Backend deve se conectar sem erro

# ✅ Git configurado
git config user.email
git config user.name
```

### Comum Issues & Soluções

#### ❌ "Port already in use"
```bash
# Linux/macOS - Encontrar o processo
lsof -i :3000
lsof -i :8000

# Matar o processo
kill -9 <PID>

# Windows
netstat -ano | findstr :3000
taskkill /PID <PID> /F
```

#### ❌ "Database connection refused"
```bash
# Verificar se PostgreSQL está rodando
# macOS:
brew services list

# Linux:
sudo service postgresql status

# Verify credenciais em .env.local
```

#### ❌ "ModuleNotFoundError: No module named 'app'"
```bash
# Ativar virtual environment
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows

# Instalar dependências novamente
pip install -r requirements.txt
```

#### ❌ "Module not found" (npm)
```bash
# Limpar cache
npm cache clean --force

# Reinstalar
rm -rf node_modules package-lock.json
npm install
```

---

## 🔄 Workflow de Desenvolvimento

### Criar Feature

```bash
# 1. Crie uma branch
git checkout -b feature/minha-feature

# 2. Faça suas mudanças
# Frontend:
cd frontend && npm run dev

# Backend:
cd backend && python -m uvicorn app.main:app --reload

# 3. Testes
npm test        # Frontend
pytest          # Backend

# 4. Commit
git add .
git commit -m "feat: descrição da feature"

# 5. Push
git push origin feature/minha-feature

# 6. Abra um Pull Request no GitHub
```

### Formatar Código

```bash
# Frontend (Prettier + ESLint)
cd frontend
npm run lint
npm run format

# Backend (Black + isort)
cd backend
black app/
isort app/
```

### Atualizar Dependências

```bash
# Frontend
cd frontend
npm update

# Backend
cd backend
pip install --upgrade -r requirements.txt
```

---

## 🐛 Debugging

### Frontend

```javascript
// Adicione console.log
console.log('Debug:', variavel);

// Ou use debugger
debugger;

// VS Code - F5 para rodar debugger
```

### Backend

```python
# Adicione print
print(f"Debug: {variavel}")

# Ou use debugger
import pdb; pdb.set_trace()

# VS Code - Configure .vscode/launch.json
```

---

## 📚 Recursos Úteis

### Documentação
- [FastAPI Docs](https://fastapi.tiangolo.com/)
- [Next.js Docs](https://nextjs.org/docs)
- [PostgreSQL Docs](https://www.postgresql.org/docs/)
- [SQLAlchemy Docs](https://docs.sqlalchemy.org/)

### Ferramentas de API Testing
- [Postman](https://www.postman.com/)
- [Thunder Client](https://www.thunderclient.com/) (extensão VS Code)
- [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client)

---

## 🆘 Precisa de Ajuda?

- 📖 [Veja o README.md](../README.md)
- 🤝 [Abra uma discussão](../../discussions)
- 🐛 [Reporte um issue](../../issues)
- 💬 Comente em issues relacionadas

---

## ✅ Próximos Passos

Depois de fazer setup:

1. ✅ Leia [CONTRIBUTING.md](../CONTRIBUTING.md)
2. ✅ Veja issues com `good-first-issue`
3. ✅ Explore a [ARCHITECTURE.md](./ARCHITECTURE.md)
4. ✅ Faça seu primeiro commit!

---

**Bem-vindo ao AccessHub! 🎉**

*Se encontrar problemas, abra uma issue descrevendo o erro.*
