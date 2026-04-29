#  Workout API

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/Alembic-6BA539?style=for-the-badge&logo=python&logoColor=white"/>
</p>

API REST para gerenciamento de atletas, treinos, categorias e centros de treinamento. Desenvolvida com **FastAPI** e **PostgreSQL**, seguindo arquitetura em camadas com separação clara de responsabilidades.

---

## Arquitetura

O projeto segue uma arquitetura em camadas, garantindo organização, manutenibilidade e facilidade de testes:

```
workout_api/
├── atleta/
│   ├── controller.py       # Rotas e lógica de controle
│   ├── models.py           # Modelos ORM (banco de dados)
│   └── schemas.py          # Schemas Pydantic (validação)
├── categorias/
│   ├── controller.py
│   ├── models.py
│   └── schemas.py
├── centro_treinamento/
│   ├── controller.py
│   ├── models.py
│   └── schemas.py
├── configs/
│   ├── database.py         # Configuração da conexão PostgreSQL
│   └── settings.py         # Variáveis de ambiente
├── contrib/
│   └── repository/         # Camada de acesso a dados (Repository Pattern)
│       ├── models.py
│       └── dependecies.py
├── main.py                 # Inicialização da aplicação
└── routers.py              # Agregação de todas as rotas
```

---

##  Funcionalidades

-  **Atletas** - cadastro, consulta, atualização e remoção
-  **Categorias** - organização dos atletas por categoria de treino
-  **Centros de Treinamento** - gerenciamento de locais de treino
-  **Migrations** com Alembic - controle de versão do banco de dados
-  **Docker** - ambiente completo containerizado
-  **Validação automática** de dados via Pydantic

---

##  Como Executar

### Pré-requisitos
- [Docker](https://www.docker.com/) e Docker Compose instalados

### Com Docker (recomendado)

1. Clone o repositório:
```bash
git clone https://github.com/Thiiagoramos/workout-api.git
cd workout-api
```

2. Suba os containers:
```bash
docker-compose up -d
```

3. Execute as migrations:
```bash
make run-migrations
```

4. Acesse a documentação interativa:
```
http://localhost:8000/docs
```

---

### Sem Docker (ambiente local)

1. Clone o repositório e crie um ambiente virtual:
```bash
git clone https://github.com/Thiiagoramos/workout-api.git
cd workout-api
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

2. Instale as dependências:
```bash
pip install -r requirements.txt
```

3. Configure as variáveis de ambiente — crie um arquivo `.env` na raiz:
```env
DATABASE_URL=postgresql+asyncpg://usuario:senha@localhost:5432/workout
```

4. Execute as migrations:
```bash
alembic upgrade head
```

5. Inicie a aplicação:
```bash
uvicorn workout_api.main:app --reload
```

---

##  Endpoints

A documentação completa e interativa dos endpoints está disponível via Swagger UI em `http://localhost:8000/docs` após subir a aplicação.

| Recurso | Método | Rota |
|---------|--------|------|
| Atletas | GET / POST / PATCH / DELETE | `/atletas` |
| Categorias | GET / POST | `/categorias` |
| Centros de Treinamento | GET / POST | `/centros_treinamento` |

---

##  Tecnologias

| Tecnologia | Uso |
|-----------|-----|
| FastAPI | Framework web assíncrono |
| PostgreSQL | Banco de dados relacional |
| SQLAlchemy | ORM para mapeamento objeto-relacional |
| Alembic | Migrations e versionamento do banco |
| Pydantic | Validação e serialização de dados |
| Docker | Containerização do ambiente |

---

##  Próximas melhorias

- [ ] Autenticação e autorização via JWT
- [ ] Paginação nos endpoints de listagem
- [ ] Testes automatizados com pytest
- [ ] CI/CD com GitHub Actions

---

##  Autor

**Thiago Ramos** — [LinkedIn](https://www.linkedin.com/in/thiago-ramos-a86107279)
