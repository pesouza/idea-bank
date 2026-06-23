# Plano de Demonstração: "Pronto Zap"
## O Conceito: "Um Dia na Lanchonete"

A demonstração será uma pequena peça de teatro interativa, ao vivo. Usaremos dois agentes Hermes, cada um atuando como um personagem, para mostrar o fluxo completo do "Pronto Zap" da perspectiva do vendedor e do cliente. O objetivo é que o cliente em potencial se sinta dentro da lanchonete, vendo o problema dele ser resolvido em tempo real.

---

### Os Personagens (Abordagem Interativa)

Esta nova abordagem é mais imersiva e coloca o cliente potencial no centro da demonstração.

1.  **Beca, a Atendente de Balcão (Agente Hermes)**
    *   **Perfil:** `hermes_beca_vendedora`
    *   **Personalidade:** Dinâmica. A diretora da demo (Sophia) pode instruí-la a assumir diferentes personalidades ("seja rápida e eficiente", "seja mais simpática") para se adaptar ao cliente.
    *   **Objetivo:** Demonstrar a eficiência e simplicidade do lado do vendedor.

2.  **O Cliente Final (Interpretado pelo Cliente Potencial)**
    *   **Ator:** O próprio cliente que está assistindo à demonstração.
    *   **Ferramenta:** Seu próprio smartphone.
    *   **Objetivo:** Viver em primeira mão a experiência de conveniência e comunicação clara que o "Pronto Zap" oferece, recebendo as notificações em tempo real no seu próprio WhatsApp.

### O Cenário (Setup da Demo)

1.  **Terminal da Beca (IA):** Mostra o agente "Beca" executando os comandos operacionais.
2.  **Celular do Cliente (Real):** Onde a mágica acontece. O cliente escaneia o QR Code e recebe as notificações.
3.  **Painel "Pronto Zap":** A interface web que a "Beca" está operando.

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
