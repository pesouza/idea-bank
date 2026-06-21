# Prompt para OpenSquad: MVP do App "Como estou dirigindo?" (Arquitetura de Agentes)

## Objetivo Principal
Criar o backend para um aplicativo de segurança e gamificação para motoristas, "Como estou dirigindo?". A arquitetura deve ser baseada em agentes (microsserviços), cada um com uma responsabilidade específica, para garantir escalabilidade e manutenibilidade.

## Arquitetura Geral
O sistema será composto por 3 agentes principais e um gateway de API.
1.  **API Gateway:** Ponto de entrada para o aplicativo móvel. Gerencia autenticação e roteia as requisições para os agentes corretos.
2.  **TripProcessor Agent:** O cérebro do sistema. Recebe dados brutos dos sensores, processa a viagem e calcula a pontuação.
3.  **Ranking Agent:** Um serviço de background que calcula e atualiza os rankings de forma assíncrona.

---

### 1. API Gateway
- **Tecnologia:** Python, Flask.
- **Responsabilidade:** Autenticação (JWT), gerenciamento de usuários e delegação de tarefas.
- **Endpoints:**
    - `POST /register`, `POST /login`: Gerenciamento de usuários.
    - `POST /trip/start`: Notifica o `TripProcessor Agent` para iniciar uma nova sessão de viagem e retorna um ID de viagem para o app.
    - `POST /trip/data`: Recebe um lote de dados de sensores (GPS, acelerômetro) do app e os encaminha para o `TripProcessor Agent` via uma fila de mensagens (Redis Pub/Sub).
    - `POST /trip/end`: Notifica o `TripProcessor Agent` para finalizar o cálculo da viagem.
    - `GET /trip/<trip_id>`: Retorna o relatório final de uma viagem.
    - `GET /rankings/local`, `GET /rankings/global`: Busca os rankings do `Ranking Agent`.

---

### 2. TripProcessor Agent
- **Tecnologia:** Python (FastAPI para performance), Geopy, Pandas.
- **Responsabilidade:** Processar os dados de uma viagem em andamento, consultar APIs externas e calcular a pontuação final.
- **Fluxo de Trabalho:**
    1.  **Ouve uma fila de mensagens (Redis Pub/Sub)** para receber pacotes de dados de sensores enviados pelo API Gateway.
    2.  Para cada ponto de GPS, **consulta uma API de mapas (ex: OpenStreetMap/OSRM)** para obter o limite de velocidade da via.
    3.  **Analisa os dados do acelerômetro** para detectar eventos bruscos (aceleração, frenagem, curvas).
    4.  **Calcula a pontuação** com base nas infrações de velocidade e nos eventos bruscos.
    5.  Ao receber o sinal de `trip/end`, finaliza os cálculos, **salva o relatório completo no banco de dados principal (PostgreSQL)** e notifica o `Ranking Agent` que uma nova pontuação está disponível.

---

### 3. Ranking Agent
- **Tecnologia:** Python, Celery (para tarefas de background).
- **Responsabilidade:** Manter os rankings atualizados.
- **Fluxo de Trabalho:**
    1.  Recebe uma notificação (via Celery task) de que uma nova viagem foi concluída.
    2.  Periodicamente (ex: a cada 5 minutos), re-calcula os rankings (local, global) com base nas pontuações médias dos usuários.
    3.  **Armazena os rankings em um cache rápido (Redis Sorted Sets)** para leitura veloz pelo API Gateway.
    4.  Expõe um endpoint interno para o API Gateway consultar os rankings cacheados.

## Banco de Dados (PostgreSQL)
- **User**: `id`, `username`, `password_hash`, `city`, `country`.
- **Trip**: `id`, `user_id`, `start_time`, `end_time`, `final_score`, `distance_km`.
- **TripEvent**: `id`, `trip_id`, `timestamp`, `event_type` (ex: 'speeding', 'harsh_braking'), `magnitude`.

## Instruções de Geração
Gere a estrutura de diretórios para cada um dos 3 agentes e o API Gateway. Cada diretório deve conter seu próprio `main.py`, `Dockerfile` e `requirements.txt`. Crie também um `docker-compose.yml` na raiz do projeto para orquestrar o build e a execução de todos os serviços, incluindo as instâncias do PostgreSQL e do Redis.
