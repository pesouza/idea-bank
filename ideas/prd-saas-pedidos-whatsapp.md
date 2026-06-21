# PRD — PediPronto (nome provisório)
## SaaS de Gerenciamento de Pedidos com Notificação via WhatsApp

**Versão:** 1.0 — MVP  
**Data:** 03/06/2026  
**Inspiração:** Workflow IA_delivery, SendWhatsappInvoice, CustomerSupaBase, contato-Agendamento (n8n AerIA)

---

## 1. Resumo

SaaS B2B para estabelecimentos alimentícios (lanchonetes, padarias, restaurantes, food trucks, praças de alimentação) que permite ao cliente final fazer um pedido presencial no balcão e receber atualizações em tempo real via WhatsApp — confirmação do pedido e aviso de retirada — sem precisar baixar app nenhum.

O estabelecimento ganha: redução de filas, menos interrupção da equipe perguntando "está pronto?", experiência moderna para o cliente.

---

## 2. Problema que Resolve

### Dores do estabelecimento
- Clientes ficam aglomerados no balcão esperando o pedido
- Equipe é interrompida dezenas de vezes com "já está pronto?"
- Clientes se perdem: pegam pedido errado, esquecem o número da comanda
- Sem canal de comunicação com o cliente após o pedido

### Dores do cliente
- Não sabe exatamente quando o pedido fica pronto
- Precisa ficar voltando no balcão perguntando
- Em lugares cheios, difícil saber se a comanda é sua
- Ansiedade / frustração com fila de espera

---

## 3. MVP — Fluxo Completo

### 3.1 Experiência do Cliente

```
┌──────────────┐    ┌───────────────┐    ┌──────────────────────┐
│ Faz pedido   │───▶│ QR Code na    │───▶│ Recebe WhatsApp com  │
│ no balcão    │   │ comanda/recibo │    │ detalhes do pedido   │
└──────────────┘    └───────────────┘    └──────────┬───────────┘
                                                    │
                                           ┌────────▼───────────┐
                                           │ Quando ficar pronto │
                                           │ WhatsApp avisa:     │
                                           │ "✅ Seu pedido está │
                                           │  pronto! Retire no  │
                                           │  balcão."           │
                                           └─────────────────────┘
```

**Opções de entrada (MVP):**
1. **QR Code na comanda** — cliente escaneia e já associa o pedido ao WhatsApp
2. **Telefone no PDV** — atendente pergunta o número do celular e digita no sistema

### 3.2 Experiência do Estabelecimento

```
┌──────────────┐    ┌─────────────────┐    ┌──────────────────────┐
│ PDV /        │───▶│ Pedido entra no │───▶│ Cozinha vê na tela   │
│ Web App      │    │ sistema + fila   │    │ (ou imprime)         │
└──────────────┘    └────────┬────────┘    └──────────────────────┘
                             │                                       
                    ┌────────▼────────┐    ┌──────────────────────┐
                    │ Cliente recebe  │    │ Cozinha marca como   │
                    │ confirmação via │◀───│ "pronto" → WhatsApp  │
                    │ WhatsApp        │    │ notifica cliente     │
                    └─────────────────┘    └──────────────────────┘
```

---

## 4. Funcionalidades do MVP

### 4.1 Painel do Estabelecimento (Web)
- Cadastro do restaurante (nome, logo, WhatsApp do negócio, horário)
- Tela de **PDV simplificado** (ou integração via API)
- **Fila de pedidos** em tempo real com status: 🔵 Pendendo → 🟡 Preparando → ✅ Pronto
- Botão "✅ Pronto" que dispara WhatsApp automático
- Histórico de pedidos do dia

### 4.2 Fluxo WhatsApp (Cliente)
- **Mensagem 1 — Confirmação:** "🛵 PediPronto › Olá [Nome]! Seu pedido #[NÚMERO] foi recebido: [itens]. Total: R$ [valor]. Seu lugar na fila: [posição]. Avisaremos quando estiver pronto! 🍔"
- **Mensagem 2 — Pronto:** "✅ PediPronto › [Nome], seu pedido #[NÚMERO] está PRONTO! Pode retirar no balcão. Bom apetite! 🎉"
- **Opcional:** Botão "Quanto tempo falta?" → responde posição na fila + tempo estimado

### 4.3 Cadastro Rápido
- Cliente informa número uma única vez
- Sistema vincula WhatsApp ao CPF ou token do pedido
- Privacidade: número usado apenas para o ciclo do pedido, sem spam

---

## 5. Arquitetura Técnica (MVP)

```
                    ┌──────────────────┐
                    │   Evolution API  │
                    │ (WhatsApp Bridge)│
                    └────────┬─────────┘
                             │
┌──────────┐    ┌───────────▼──────────┐    ┌────────────────┐
│ Cliente  │◀───│   Backend (Flask)    │───▶│   Supabase     │
│ WhatsApp │    │   - Pedidos API      │    │   - Pedidos    │
│          │    │   - Fila             │    │   - Clientes   │
│          │    │   - Notificações     │    │   - Restaurantes│
└──────────┘    └───────────┬──────────┘    │   - Fila       │
                            │                └────────────────┘
                    ┌───────▼────────┐
                    │  Web App PDV   │
                    │  (React/Flask) │
                    │  - Fila tempo  │
                    │    real        │
                    │  - Status      │
                    │  - Histórico   │
                    └────────────────┘
```

### Stack Técnico
| Componente | Tecnologia | Por quê |
|---|---|---|
| **Backend** | Flask (Python) | Já existe na AerIA, domínio da equipe |
| **Frontend (PDV)** | React ou Jinja2 + HTMX | Simplicidade para MVP |
| **Banco** | Supabase (PostgreSQL) | Já usado nos workflows n8n |
| **WhatsApp** | Evolution API | Já integrada nos workflows ativos |
| **Fila** | Redis | Já usado no IA_delivery, ideal para fila em tempo real |
| **QR Code** | qrcode (Python lib) | Geração simples server-side |
| **Deploy** | Docker + Traefik | Padrão AerIA |

### Modelo de Dados (MVP)

```
restaurantes
  id, nome, logo_url, whatsapp_business, horario_funcionamento, ativo

pedidos
  id, restaurante_id, cliente_id, numero_comanda,
  itens (jsonb), total, status (pendente/preparando/pronto/retirado),
  posicao_fila, created_at, updated_at

clientes
  id, nome, telefone, cpf (opcional), created_at

notificacoes
  id, pedido_id, tipo (confirmacao/pronto), status (enviado/entregue/falha),
  mensagem, sent_at, delivered_at
```

---

## 6. Diferenciais vs Concorrentes

| Concorrente | Diferença do PediPronto |
|---|---|
| **iFood Pedido Pronto** | Focado em delivery, não em balcão. Cliente não está no local |
| **WaiteTime** | Apenas fila virtual, sem integração com WhatsApp |
| **QR Cardápio** | Só cardápio digital, sem gestão de pedidos e notificações |
| **ZapCardápio** | Catálogo no WhatsApp, sem integração com PDV físico |
| **Sistemas de senha (senha normal)** | Não avisam via WhatsApp, cliente precisa ficar olhando painel |

**Diferenciais competitivos:**
- Cliente não precisa baixar app (só escaneia QR Code)
- Integração direta com o fluxo de trabalho da cozinha
- Custo baixo por estabelecimento
- Setup em minutos (cria conta, configura WhatsApp, imprime QR Code)

---

## 7. Monetização

### Modelo Freemium (MVP)

| Plano | Preço | Funcionalidades |
|---|---|---|
| **Free** | R$ 0 | Até 30 pedidos/dia, 1 estabelecimento, notificações básicas |
| **Pro** | R$ 49/mês | Pedidos ilimitados, múltiplos painéis, relatórios, suporte prioritário |
| **Enterprise** | R$ 99/mês | Multi-unidades, API para integrar com PDV existente, custom branding |

### Gatilhos de upgrade
- Estabelecimento que ultrapassa 30 pedidos/dia
- Precisa de relatórios de tempo médio de preparo
- Quer personalizar mensagens WhatsApp

---

## 8. Sinergias com AerIA

### O que já existe e pode ser reaproveitado:

| Recurso | Origem | Como usar |
|---|---|---|
| **Evolution API** | IA_delivery, SendWhatsappInvoice | Envio de mensagens WhatsApp — já configurada |
| **Supabase** | CustomerSupaBase, CustomerLocation | BD de clientes e pedidos |
| **Redis** | IA_delivery | Fila de pedidos em tempo real |
| **Flask + Traefik** | aeria-apps.com.br, aeria-crm | Infraestrutura pronta |
| **aeria-apps.com.br** | Landing page | Página de vendas do SaaS |
| **Selfware** | Proposta AerIA | Posicionar como mais um agente autônomo: "Agente de Filas" |
| **n8n** | Workflows existentes | Automações internas (relatórios diários, lembretes) |

### Integração estratégica:
- O SaaS pode ser **mais um app no ecossistema aeria-apps.com.br**
- O DNS `pedipronto.aeria-apps.com.br` (ou similar)
- Usar o mesmo login do CRM AerIA para gerenciar clientes do SaaS
- Pipeline de vendas via WhatsApp usando os mesmos fluxos

---

## 9. Roteiro MVP

### Semana 1 — Fundação
- [ ] Setup do projeto Flask no Docker
- [ ] Modelos Supabase (restaurantes, pedidos, clientes, notificações)
- [ ] Integração Evolution API + templates de mensagem
- [ ] Geração de QR Code estático

### Semana 2 — PDV + Fila
- [ ] CRUD de pedidos via API
- [ ] Tela PDV (web) — criar pedido, listar fila
- [ ] Botão "Pronto" → dispara WhatsApp
- [ ] Fila em tempo real (Redis + SSE ou polling)

### Semana 3 — Experiência do Cliente
- [ ] Página pública de status do pedido (via QR Code)
- [ ] Notificação de confirmação + notificação de pronto
- [ ] Teste com usuários reais

### Semana 4 — Lançamento
- [ ] Onboarding de 3 estabelecimentos piloto (grátis)
- [ ] Landing page + captura de leads
- [ ] Polimento e correções

---

## 10. Riscos e Mitigações

| Risco | Mitigação |
|---|---|
| **Cliente não tem WhatsApp** | Queda para SMS ou painel visual |
| **Número bloqueado pela Evolution API** | Fallback para outro provider (wweb.js, WhatsApp Cloud API) |
| **Estabelecimento quer integração com PDV existente** | Oferecer API REST simples na fase Enterprise |
| **Baixa adesão — "prefiro chamar pelo nome"** | Educar sobre redução de fila e experiência do cliente |
| **Custo da Evolution API por mensagem** | Negociar volume ou usar WhatsApp Cloud API (gratuito até 1k conversas/mês) |

---

## 11. Próximos Passos

1. ✅ **Validar este PRD com você** — ajustar prioridades
2. 🔲 Definir nome definitivo (PediPronto? FilaPronto? AviseMe? JáVai?)
3. 🔲 Setup do projeto e infraestrutura
4. 🔲 Onboarding de 3 estabelecimentos piloto (escambo: gratuito em troca de feedback)
5. 🔲 Iterar com base no uso real

---

*Documento gerado por Soph.IA — Assistente de IA da AerIA Creative Solutions*
