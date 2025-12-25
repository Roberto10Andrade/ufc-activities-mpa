# UFC Activities

Sistema web para gerenciamento de atividades acadêmicas da UFC Sobral, desenvolvido em Django com foco em acessibilidade e usabilidade.

![Django](https://img.shields.io/badge/Django-5.2.5-green)
![Python](https://img.shields.io/badge/Python-3.13+-blue)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38B2AC)
![License](https://img.shields.io/badge/License-MIT-yellow)

## Visão Geral

O UFC Activities é uma aplicação Multi-Page Application (MPA) que permite o gerenciamento completo de atividades acadêmicas, incluindo cursos, workshops, seminários, pesquisas e projetos de extensão.

### Principais Funcionalidades

- **Dashboard Interativo**: Estatísticas em tempo real com visualização de atividades por status
- **CRUD Completo**: Criar, visualizar, editar e excluir atividades
- **Sistema de Tags**: Categorização flexível de atividades
- **Filtros Avançados**: Busca por tipo, status, coordenador e local
- **Acessibilidade**: Alto contraste, fonte para dislexia, tamanhos ajustáveis

## Tecnologias

| Camada | Tecnologia |
|--------|------------|
| Backend | Django 5.2.5 |
| Frontend | HTML5, CSS3, JavaScript |
| Estilização | Tailwind CSS |
| Ícones | Font Awesome |
| Banco de Dados | SQLite (dev) / PostgreSQL (prod) |

## Instalação

### Pré-requisitos

- Python 3.8+
- pip
- Git

### Configuração Local

```bash
# Clone o repositório
git clone https://github.com/Roberto10Andrade/ufc_activities_django.git
cd ufc_activities_django

# Crie e ative o ambiente virtual
python -m venv venv
venv\Scripts\activate  # Windows
source venv/bin/activate  # Linux/Mac

# Instale as dependências
pip install -r requirements.txt

# Execute as migrações
python manage.py migrate

# Popule com dados de exemplo (opcional)
python populate_data.py

# Inicie o servidor
python manage.py runserver
```

Acesse: http://localhost:8000

## Deploy (Render)

```bash
# Build Command
pip install -r requirements.txt

# Start Command
gunicorn ufc_activities_django.wsgi:application
```

## Estrutura do Projeto

```
ufc_activities_django/
├── activities/           # App principal
│   ├── models.py         # Activity, ActivityTag
│   ├── views.py          # Views e lógica
│   ├── forms.py          # Formulários
│   └── urls.py           # Rotas
├── templates/            # Templates HTML
│   ├── base.html         # Template base
│   ├── dashboard/        # Dashboard
│   └── activities/       # CRUD de atividades
├── static/               # CSS, JS, imagens
├── requirements.txt      # Dependências Python
└── manage.py             # CLI Django
```

## Modelo de Dados

### Activity

| Campo | Tipo | Descrição |
|-------|------|-----------|
| title | CharField | Título (mín. 3 caracteres) |
| description | TextField | Descrição (mín. 10 caracteres) |
| status | CharField | Pendente, Em Andamento, Concluída, Cancelada, Ativa, Em Breve |
| start_date | DateField | Data de início |
| end_date | DateField | Data de término |
| location | CharField | Local da atividade |
| coordinator | CharField | Nome do coordenador |
| participants | PositiveIntegerField | Número de participantes (mín. 1) |
| tags | ManyToMany | Tags relacionadas |

## Recursos de Acessibilidade

- **Alto Contraste**: Melhora a legibilidade
- **Modo Invertido**: Cores invertidas
- **Tamanhos de Fonte**: Normal, Grande, Maior
- **Fonte para Dislexia**: OpenDyslexic
- **Navegação por Teclado**: Suporte completo

## API de Rotas

| Rota | Método | Descrição |
|------|--------|-----------|
| `/` | GET | Dashboard |
| `/atividades/` | GET | Lista de atividades |
| `/atividades/new/` | GET, POST | Criar atividade |
| `/atividades/<id>/` | GET | Detalhes da atividade |
| `/atividades/edit/<id>/` | GET, POST | Editar atividade |
| `/atividades/delete/<id>/` | POST | Excluir atividade |

## Autor

**Roberto Andrade**

- GitHub: [@Roberto10Andrade](https://github.com/Roberto10Andrade)

## Licença

Este projeto está sob a licença MIT.
