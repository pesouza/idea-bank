# Prompt para OpenSquad: MVP do App "Pronto Zap"

## Objetivo Principal
Criar uma aplicação web monolítica e simples para gerenciar o status de pedidos em um balcão e notificar clientes via WhatsApp.

## Estrutura do Projeto
- **Tecnologia:** Python com Flask e Flask-SQLAlchemy. O frontend será HTML/CSS/JavaScript servido diretamente pelo Flask.
- **Estrutura de Arquivos:**
  - `app.py`: Arquivo principal com as rotas Flask, lógica de negócio e integração com WhatsApp.
  - `models.py`: Definições das tabelas do banco de dados (SQLite para o MVP).
  - `templates/index.html`: A interface única para o vendedor.
  - `static/`: Diretório para arquivos CSS e JS.
  - `config.py`: Configurações (ex: URL da API do WhatsApp).
  - `requirements.txt`: Dependências.
  - `Dockerfile`: Para containerizar a aplicação.

## Frontend (Vendor Interface - `templates/index.html`)
- Uma página única, que se atualiza dinamicamente (usando JavaScript e Fetch API).
- **Seção de Novo Pedido:**
  - Input de texto para "Nome do Cliente ou Número do Pedido".
  - Botão "Gerar QR Code". Ao clicar, deve chamar a API do backend, receber os dados e exibir o QR Code na tela (usar uma biblioteca JS para isso).
- **Seção de Pedidos Ativos:**
  - Uma lista de todos os pedidos com status "Preparando" ou "Pronto".
  - Cada item da lista deve mostrar o nome/número do pedido e três botões de ação: `[Preparando]`, `[Pronto]`, `[Entregue]`.
  - Clicar em um botão de status deve chamar a API do backend para atualizar o pedido e enviar a notificação via WhatsApp. Clicar em "Entregue" deve remover o pedido da lista de ativos.

## Backend (`app.py`)
- **API Endpoints:**
  - `GET /`: Renderiza a página `index.html`.
  - `GET /api/orders`: Retorna um JSON com todos os pedidos ativos.
  - `POST /api/order`: Recebe `{"name": "Pedido 123"}`. Cria um novo pedido no banco de dados com status inicial e retorna o ID do pedido e o link `wa.me` para ser transformado em QR Code no frontend.
  - `POST /api/order/<id>/status`: Recebe `{"status": "preparando" | "pronto" | "entregue"}`. Atualiza o status no banco e chama a função para enviar a mensagem correspondente via WhatsApp.
- **Webhook do WhatsApp:**
  - `POST /whatsapp/webhook`: Endpoint para receber mensagens da API do WhatsApp (Evolution API).
  - **Lógica:** Quando um cliente escaneia o QR Code, ele envia uma mensagem como "Quero acompanhar o pedido 123". O webhook deve:
    1. Extrair o número do pedido ("123") e o número de telefone do remetente.
    2. Encontrar o pedido no banco de dados.
    3. Salvar o número de telefone do cliente no registro daquele pedido para futuras notificações.
    4. Enviar a primeira mensagem de confirmação: "Olá! Recebemos seu pedido #123. Avisaremos quando estiver em preparação."

## Banco de Dados (`models.py`)
- **Tabela `Order`:**
  - `id` (PK)
  - `order_identifier` (String, ex: "123" ou "Paulo")
  - `customer_phone` (String, nullable)
  - `status` (String, ex: "novo", "preparando", "pronto", "entregue")
  - `created_at` (DateTime)

## Integração WhatsApp
- Usar a biblioteca `requests` para fazer chamadas HTTP para os endpoints da sua API do WhatsApp (ex: Evolution API).
- As URLs e tokens da API devem ser configuráveis via `config.py` ou variáveis de ambiente.

## Instruções de Geração
Gere o projeto Flask completo com a estrutura de arquivos descrita. Crie a interface `index.html` com HTML básico e placeholders para a lógica JavaScript. Implemente as rotas da API no `app.py` com a lógica de banco de dados e placeholders para as chamadas da API do WhatsApp.
