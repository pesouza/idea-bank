# Prompt para OpenSquad: MVP do App "Anjo da Guarda"

## Objetivo Principal
Criar o backend para um aplicativo de segurança pessoal chamado "Anjo da Guarda". O sistema permitirá que usuários monitorem seus trajetos e acionem alertas para contatos de emergência.

## Estrutura do Projeto
Use Python com Flask e Flask-SQLAlchemy. Organize o projeto da seguinte forma:
- `app.py`: Arquivo principal com as rotas da API.
- `models.py`: Definições das tabelas do banco de dados (User, EmergencyContact, MonitoredTrip).
- `services.py`: Lógica de negócio (iniciar/finalizar trajeto, enviar alertas).
- `config.py`: Configurações do aplicativo.
- `requirements.txt`: Dependências do Python.

## Modelo de Dados (`models.py`)
Crie os seguintes modelos SQLAlchemy:
1.  **User**:
    - `id` (PK, Integer)
    - `username` (String, unique)
    - `password_hash` (String)
    - `phone_number` (String, unique)
    - `safeword_hash` (String, nullable) - Para a palavra de segurança.
2.  **EmergencyContact**:
    - `id` (PK, Integer)
    - `user_id` (FK para User)
    - `name` (String)
    - `phone_number` (String)
3.  **MonitoredTrip**:
    - `id` (PK, Integer)
    - `user_id` (FK para User)
    - `start_location` (String)
    - `destination` (String)
    - `eta_minutes` (Integer)
    - `start_time` (DateTime)
    - `status` (String: 'active', 'completed', 'alert')

## Endpoints da API (`app.py`)
Crie os seguintes endpoints RESTful:
- `POST /register`: Cria um novo usuário.
- `POST /login`: Autentica um usuário e retorna um token JWT.
- `POST /contacts/add` (protegido): Adiciona um novo contato de emergência para o usuário logado.
- `POST /trip/start` (protegido): Inicia um novo trajeto monitorado. Recebe `destination` e `eta_minutes`.
- `POST /trip/end` (protegido): Marca o trajeto atual como 'completed'.
- `POST /panic` (protegido): Aciona o alerta imediatamente para todos os contatos.

## Lógica de Negócio (`services.py`)
- **Alertas via SMS:** Crie uma função `send_alert(phone_number, message)` que se integra com uma API de SMS (ex: Twilio). As chaves da API devem vir de variáveis de ambiente.
- **Verificação de Trajetos (Scheduler):** Uma função a ser executada a cada minuto para verificar todos os trajetos 'active'. Se `current_time > start_time + eta_minutes`, muda o status para 'alert' e chama `send_alert` para todos os contatos de emergência do usuário.

## Tecnologias
- Backend: Python, Flask, Flask-SQLAlchemy, Flask-JWT-Extended
- Banco de dados: SQLite (para o MVP)
- Alertas: Interface para API de SMS (Twilio ou similar)
- Deploy: Dockerfile pronto para produção.
