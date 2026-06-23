# Plano de Demonstração: "Pronto Zap"
## O Conceito: "Um Dia na Lanchonete"

A demonstração será uma pequena peça de teatro interativa, ao vivo. Usaremos dois agentes Hermes, cada um atuando como um personagem, para mostrar o fluxo completo do "Pronto Zap" da perspectiva do vendedor e do cliente. O objetivo é que o cliente em potencial se sinta dentro da lanchonete, vendo o problema dele ser resolvido em tempo real.

---

### Os Personagens (Perfis Hermes)

1.  **Beca, a Atendente de Balcão**
    *   **Perfil Hermes:** `hermes_beca_vendedora`
    *   **Personalidade:** Rápida, eficiente, focada. Sua linguagem é direta e operacional ("Pedido #124 para o Alex, gerando QR Code.", "Atualizando status para 'Pronto'.").
    *   **Objetivo na Demo:** Mostrar como o "Pronto Zap" torna seu trabalho mais fácil e organizado, eliminando a necessidade de gritar nomes e gerenciar uma multidão no balcão.
    *   **Ferramentas (Skills):** Um skill `pronto-zap-vendor` com comandos como `criar_pedido(nome_cliente)`, `atualizar_status(id_pedido, novo_status)`.

2.  **Alex, o Cliente (com Fome)**
    *   **Perfil Hermes:** `hermes_alex_cliente`
    *   **Personalidade:** Ansioso, moderno, não gosta de esperar em filas. Quer conveniência e informação.
    *   **Objetivo na Demo:** Mostrar como a experiência do cliente é drasticamente melhorada. Ele pode esperar sentado, conversando, e saberá exatamente quando seu pedido estiver pronto.
    *   **Ferramentas (Skills):** Um skill que simula um cliente de WhatsApp, com comandos como `ler_notificacoes()`.

---

### O Cenário (Setup da Demo)

Apresentaremos em 3 telas (ou 3 áreas da mesma tela):

1.  **Terminal da Beca:** Mostrando o agente "Beca" em ação, executando seus comandos.
2.  **Tela do Alex:** Simulando a tela do celular do "Alex", mostrando as notificações do WhatsApp chegando.
3.  **Painel "Pronto Zap":** A interface web real do produto, para o cliente ver o painel que a Beca estaria usando.

---

### O Roteiro da Demo (Passo a Passo)

1.  **Apresentação (Eu, Sophia):** "Vamos simular uma lanchonete em horário de pico. Conheçam a Beca, nossa atendente, e o Alex, um cliente. O Alex vai fazer um pedido."

2.  **O Pedido (Interação):**
    *   **Eu:** "@Beca, o Alex acabou de pedir um X-Burger. Por favor, registre o pedido."
    *   **Beca (executa):** `pronto-zap-vendor.criar_pedido(nome_cliente="Alex")`
    *   **Sistema:** O painel do "Pronto Zap" exibe um QR Code na tela.

3.  **A Conexão (A Mágica Acontece):**
    *   **Eu:** "Agora, em vez de esperar no balcão, o Alex simplesmente escaneia o código com seu celular."
    *   *(Neste momento, simulamos o scan)*
    *   **Tela do Alex (mostra notificação):**
      > "Olá, Alex! Seu pedido #124 foi recebido. Vamos te manter informado por aqui. 👍"

4.  **O Preparo:**
    *   **Eu:** "A cozinha avisou que o pedido do Alex começou a ser preparado. @Beca, atualize o status."
    *   **Beca (executa):** `pronto-zap-vendor.atualizar_status(id_pedido=124, novo_status="preparando")`
    *   **Tela do Alex (mostra notificação):**
      > "Seu X-Burger já está na chapa! 🍔 Em breve estará pronto."

5.  **A Entrega (O Clímax):**
    *   **Eu:** "O pedido ficou pronto! @Beca..."
    *   **Beca (executa):** `pronto-zap-vendor.atualizar_status(id_pedido=124, novo_status="pronto")`
    *   **Tela do Alex (mostra notificação):**
      > "Pode vir buscar! Seu pedido #124 está pronto te esperando no balcão. Bom apetite!"

---

### O "Grand Finale": A Venda

Após o roteiro, o agente conclui a apresentação para o cliente:

"Vejam que em nenhum momento a Beca precisou gritar, e o Alex não precisou ficar de pé, ansioso, no balcão. A experiência foi tranquila para ambos.

Mas o verdadeiro poder está aqui: a lanchonete agora tem o contato do Alex no seu sistema. Amanhã, ela pode enviar uma promoção do 'Pronto Zap', transformando uma venda única em um cliente fiel. **É isso que o Selfware da Aeria faz: ele não apenas organiza, ele cria oportunidades.**"
