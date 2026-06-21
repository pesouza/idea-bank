
# Anjo da Guarda (Monitor de Deslocamento Pessoal)

- **resumo**: Um sistema de segurança pessoal que monitora ativamente o deslocamento de um usuário. Caso o usuário se desvie significativamente da rota ou não chegue ao destino no tempo previsto, o sistema alerta automaticamente contatos de emergência pré-selecionados e, como último recurso, as autoridades.
- **problema que resolve**: A preocupação com a segurança pessoal durante deslocamentos (a pé, de carro, transporte público) é uma constante. Familiares e amigos se preocupam, e não há uma rede de segurança automatizada que possa agir proativamente em caso de um imprevisto, como um sequestro, um acidente ou um mal súbito.
- **viabilidade**: 
- **Técnica (Média):** Requer uso intensivo e preciso do GPS do celular. O backend precisa processar dados de localização em tempo real, comparar com rotas de APIs de mapas (Google Maps, OSRM) e gerenciar uma lógica de alertas complexa para evitar falsos positivos. A integração com serviços de emergência (polícia, bombeiros) é o maior desafio técnico e burocrático.
- **Mercado (Alta):** Existe uma demanda latente e muito forte por soluções de segurança pessoal. O público-alvo é vasto: pais de adolescentes, mulheres, pessoas que trabalham à noite, idosos, etc. O apelo emocional é um grande impulsionador de vendas.
- **Custo (Médio):** O principal custo recorrente será o uso de APIs de mapas e geolocalização, que cobram por requisição e podem escalar rapidamente com o número de usuários. Haverá também custos de servidores para o processamento em tempo real e gateways de SMS/Voz para os alertas.

- **prós / contras**: 
**Prós:**
- Atende a uma necessidade humana fundamental: segurança.
- Potencial viral e de marketing "boca a boca" muito forte.
- Modelo de negócio claro (assinatura mensal/anual).
- Causa um impacto social positivo e tangível.

**Contras:**
- Enorme responsabilidade e potencial de litígio em caso de falha.
- Risco de falsos alarmes, o que pode gerar descrédito e problemas com serviços de emergência.
- Questões de privacidade sobre o monitoramento constante da localização do usuário.
- Forte concorrência de funcionalidades já existentes (Life360, Localização em tempo real do WhatsApp/Google Maps), embora o diferencial seja o alerta *proativo*.

- **MVP**: 
1. **Cadastro de Usuário e Contatos de Emergência:** O usuário cria uma conta e cadastra de 1 a 3 contatos de confiança.
2. **Iniciar Trajeto Monitorado:** O usuário insere um endereço de destino e inicia o monitoramento. O app calcula o tempo estimado de chegada (ETA).
3. **Alerta de Não Chegada:** Se o usuário não desativar o monitoramento manualmente ao chegar, o sistema envia um alerta via SMS para os contatos de emergência X minutos após o ETA, contendo a última localização conhecida.
4. **Botão de Pânico / Palavra de Segurança:** Um botão visível no app para acionamento imediato de alerta. Alternativamente, o usuário pode pré-cadastrar uma palavra/frase de segurança que, se enviada em resposta a um 'check-in' do sistema, aciona o alerta silenciosamente.
(O desvio de rota e o acionamento de autoridades ficariam para uma versão futura, para simplificar o MVP).

- **sinergias**: 
- **Aeria Selfware:** Perfeitamente alinhado com o conceito de "agentes autônomos" que cuidam de você. Seria o "Agente de Segurança Pessoal".
- **Integração com Wearables:** No futuro, poderia se conectar a smartwatches para detectar quedas ou alterações de batimentos cardíacos.
- **aeria-apps.com.br:** Plataforma para a venda das assinaturas, landing page e blog com dicas de segurança.

- **próximos passos**: 
1. **Análise Jurídica:** Consultar um advogado para entender as implicações legais e a responsabilidade civil de um serviço como este.
2. **Estudo de APIs:** Comparar o custo e as funcionalidades das APIs de mapas (Google Maps Platform vs. Mapbox vs. OpenStreetMap) para o MVP.
3. **Design de UX/UI:** Focar em uma interface extremamente simples e rápida de usar em uma situação de estresse. O botão "iniciar trajeto" tem que ser óbvio e acessível.

