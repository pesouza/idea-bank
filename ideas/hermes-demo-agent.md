
# Agente de Demonstração (Hermes Persona Switcher)

- **resumo**: Um agente Hermes 'mestre' com a capacidade de carregar dinamicamente diferentes perfis, personas e conjuntos de habilidades para conduzir demonstrações de software ao vivo para clientes. Em vez de uma demo estática, o cliente interage com um agente que assume o papel de diferentes usuários do sistema (ex: 'Gerente', 'Operador de Caixa', 'Técnico de Campo').
- **problema que resolve**: Demonstrações de software são frequentemente genéricas e não conseguem mostrar como o produto funciona na perspectiva dos diferentes papéis dentro de uma empresa cliente. É difícil para o cliente visualizar o valor para cada membro de sua equipe. Além disso, demos ao vivo são propensas a erros humanos e é difícil responder a perguntas 'e se...?' de forma interativa.
- **viabilidade**: 
- **Técnica (Média Complexidade):** O Hermes já suporta o conceito de 'perfis'. O desafio técnico é criar um mecanismo para que um agente possa 'trocar' de perfil (ou carregar um sub-agente com um perfil diferente) de forma fluida durante uma sessão de demonstração. Isso exigiria um script orquestrador.
- **Mercado (Ferramenta Interna de Alto Valor):** Como ferramenta de vendas para a Aeria, o valor é altíssimo. A capacidade de mostrar um agente assumindo o papel de um 'vendedor' do 'Pronto Zap' e depois o papel de um 'cliente' interagindo com o sistema seria uma apresentação de vendas extremamente poderosa e convincente.
- **Custo (Baixo):** O custo é puramente de tempo de desenvolvimento e configuração, utilizando a estrutura já existente do Hermes.

- **prós / contras**: 
**Prós:**
- **Demos Vivas e Interativas:** Aumenta drasticamente o engajamento do cliente.
- **Demonstração de Valor Clara:** Mostra exatamente como o produto beneficia cada tipo de usuário.
- **Fator "Wow":** É uma demonstração da própria tecnologia de agentes da Aeria, vendendo o conceito de Selfware de forma implícita.
- **Reutilizável:** Uma vez configurado, pode ser adaptado para demonstrar qualquer um dos nossos produtos.

**Contras:**
- **Complexidade de Setup:** Cada produto a ser demonstrado exigiria a configuração detalhada de múltiplos perfis (personas, habilidades, memórias).
- **Risco do Ao Vivo:** Uma falha durante a demonstração pode ser mais impactante do que em uma demo tradicional.
- **Pode ser confuso:** Se não for bem orquestrado, o cliente pode se perder na troca de papéis.

- **MVP**: 
1.  **Dois Perfis Manuais:** Não se preocupar com a troca dinâmica. Criar manualmente dois perfis completos para o "Pronto Zap":
    *   `perfil_vendedor`: Com habilidades para criar pedidos e atualizar status.
    *   `perfil_cliente`: Com habilidades para perguntar sobre o status do pedido.
2.  **Demo em Duas Etapas:** A demonstração seria feita em duas janelas de terminal separadas, uma para cada perfil, mostrando a interação entre eles através do sistema "Pronto Zap". Isso valida o conceito sem a complexidade da troca de perfil em tempo real.

- **Exemplo de Aplicação Prática**:
Um roteiro detalhado de como este agente pode ser usado para uma demonstração interativa do produto "Pronto Zap" foi criado. Ele inclui a definição das personas (vendedor e cliente) e o fluxo completo da apresentação. Veja em: [[demo-plan-pronto-zap]].

- **sinergias**: 
- **Aeria Selfware:** Esta é a ferramenta de vendas definitiva para o conceito de Selfware. Ela *é* a própria personificação de um agente autônomo e multifacetado.
- **OpenSquad:** Um fluxo de demo matador seria: 1) Apresentar uma ideia do banco de ideias. 2) Usar o OpenSquad para gerar o código-base do app. 3) Usar o Agente de Demonstração para assumir os papéis de usuário e interagir com o app recém-criado. Isso mostra o ciclo completo, da ideia ao uso, em minutos.

- **monetização**: 
- **Acelerador de Vendas (Principal):** Esta não é uma ferramenta para ser vendida, mas sim para ser usada para vender todos os outros produtos da Aeria. Seu valor não está na receita direta, mas no aumento da taxa de conversão de vendas.
- **Serviço de "Demo-as-a-Service" (Futuro):** No futuro, a Aeria poderia vender o serviço de criação de agentes de demonstração para outras empresas de software que queiram ter demos mais interativas.

- **próximos passos**: 
1.  **Definir os Perfis do 'Pronto Zap':** Detalhar a persona, os objetivos e as ferramentas necessárias para os papéis 'Vendedor do Balcão' e 'Cliente'.
2.  **Criar os Diretórios de Perfil:** Configurar as duas estruturas de perfil separadas para o MVP.
3.  **Desenvolver um Script de Demo:** Escrever um roteiro simples para a demonstração em duas etapas, para garantir que o fluxo seja claro e impressionante.

