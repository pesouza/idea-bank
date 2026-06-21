
# Pronto Zap (Sistema de Pedidos e Notificações via WhatsApp)

- **resumo**: Uma solução para estabelecimentos comerciais (lanchonetes, food trucks, etc.) que otimiza o fluxo de retirada de pedidos. O vendedor registra o pedido em um tablet, gera um QR Code que o cliente escaneia para se conectar ao WhatsApp da loja e receber atualizações automáticas sobre o status do seu pedido ('em preparação', 'pronto para retirada', 'retirado').
- **problema que resolve**: A comunicação no balcão de retirada é ineficiente e caótica. Clientes se aglomeram esperando, vendedores gritam números ou nomes, e não há um canal direto de comunicação. Isso gera uma experiência ruim para o cliente e sobrecarrega a equipe, que é constantemente interrompida para dar status de pedidos.
- **viabilidade**: 
- **Técnica (Baixa Complexidade):** A tecnologia necessária é madura e acessível. A solução consiste em: um front-end simples (web app para o tablet), um gerador de QR Code (bibliotecas prontas), e um back-end que gerencia o estado do pedido e se comunica com uma API de WhatsApp (como a Evolution API).
- **Mercado (Alta):** O mercado de pequenos e médios estabelecimentos de comida e serviços rápidos é gigantesco. A dor é real e a solução é barata de implementar, tornando-a muito atraente.
- **Custo (Baixo):** Os custos operacionais são mínimos, envolvendo a hospedagem do sistema web e o custo da API do WhatsApp, que geralmente é um valor fixo mensal.

- **prós / contras**: 
**Prós:**
- Resolve um problema claro e visível.
- Baixo custo de desenvolvimento e manutenção.
- Grande mercado potencial.
- Melhora drasticamente a experiência do cliente e a eficiência operacional do vendedor.
- Potencial para se tornar a porta de entrada para outros serviços (CRM, marketing).

**Contras:**
- O mercado de sistemas para restaurantes (POS) é competitivo; alguns podem ter funcionalidades similares.
- Dependência da estabilidade e políticas da API do WhatsApp.
- Requer que o estabelecimento tenha um dispositivo (tablet/celular) dedicado no balcão.

- **MVP**: 
1.  **Tela do Vendedor:** Uma página web super simples onde o vendedor digita o número do pedido (ex: 123) e clica em "Gerar QR Code".
2.  **Geração de QR Code:** O sistema gera um QR Code que contém um link `wa.me` com uma mensagem pré-definida (ex: "Quero acompanhar o pedido 123").
3.  **Fluxo de Status:** Na tela do vendedor, ao lado do pedido, existem três botões: "Preparando", "Pronto" e "Entregue". Clicar em cada um dispara a respectiva mensagem para o cliente que iniciou a conversa.

- **sinergias**: 
- **Aeria CRM:** Esta é a sinergia mais forte. Cada cliente que escaneia o QR Code se torna automaticamente um contato no CRM da loja, com o histórico do pedido. O estabelecimento pode usar isso para campanhas de marketing futuras ("Vimos que você pediu um X-Burger na semana passada. Que tal um hoje com 10% de desconto?"). Isso agrega um valor imenso.
- **Aeria Selfware:** É a materialização de um "Agente Notificador de Pedidos".

- **monetização**: 
Aqui estão algumas estratégias, da mais simples à mais completa:

1.  **Assinatura Mensal (SaaS) por Terminal:**
    *   **Plano Básico (ex: R$ 49/mês):** Até 200 pedidos/mês, 1 terminal (tablet).
    *   **Plano Profissional (ex: R$ 99/mês):** Pedidos ilimitados, múltiplos terminais, personalização básica das mensagens.
    *   **Plano Premium (ex: R$ 149/mês):** Tudo do Profissional + **Integração com o Aeria CRM**, relatórios e analytics sobre o fluxo de pedidos.

2.  **Modelo Freemium com Upsell:**
    *   Oferecer um plano gratuito para sempre, limitado a um número baixo de pedidos (ex: 50 por mês).
    *   O objetivo é fazer o dono do estabelecimento se apaixonar pela ferramenta. Quando o negócio dele crescer e passar do limite, ele naturalmente fará o upgrade para um plano pago. O grande atrativo do upgrade seria a integração com o CRM.

3.  **Taxa por Pedido (Pay-per-use):**
    *   Cobrar um valor pequeno por cada notificação enviada (ex: R$ 0,15 por pedido concluído).
    *   É atraente para negócios com volume muito variável, mas gera receita menos previsível para você.

4.  **Venda como Módulo de um Sistema Maior:**
    *   Não vender o "Pronto Zap" de forma isolada, mas como um módulo essencial do **Aeria CRM para Pequenos Negócios**, justificando um ticket médio maior para a solução completa.

- **próximos passos**: 
1.  **Protótipo do Tablet:** Criar um protótipo navegável (em Figma ou HTML/JS simples) da interface do vendedor para validar o fluxo.
2.  **Validar com Clientes:** Apresentar o protótipo para 3 a 5 donos de lanchonetes ou food trucks e perguntar "Quanto você pagaria por mês para resolver esse problema?".
3.  **Implementar o MVP:** Desenvolver a funcionalidade básica descrita no MVP.

