
# Como estou dirigindo? (Game de Direção Segura)

- **resumo**: Um aplicativo gamificado que utiliza os sensores do celular (câmera, microfone, GPS, acelerômetro) para analisar e pontuar a qualidade da direção do motorista em tempo real. Ações positivas como dar seta e respeitar a velocidade somam pontos, enquanto ações negativas como freadas bruscas, uso do celular e desrespeito a pedestres diminuem a pontuação. Para aumentar o engajamento, o app contaria com rankings de motoristas (locais, por cidade, e globais).
- **problema que resolve**: Muitos motoristas desenvolvem maus hábitos de direção por falta de um feedback imediato e objetivo. Aulas de direção ensinam o básico, mas não há um acompanhamento contínuo. Isso leva a um trânsito mais perigoso e a custos mais altos (multas, acidentes, seguros). As soluções existentes são focadas em punição (multas) ou são passivas (rastreadores de seguradora).
- **viabilidade**: 
- **Técnica (Alta Complexidade):** Este é o maior desafio. Analisar o uso da seta, prioridade para pedestres e uso do celular via câmera em tempo real exige modelos de Computer Vision muito avançados e um processamento intenso, o que consumiria muita bateria. A detecção de velocidade (via GPS vs. API de mapas) e freadas bruscas (via acelerômetro) é mais simples e já validada no mercado. A análise do som da seta via microfone é uma possibilidade interessante, mas desafiadora.
- **Mercado (Médio/Alto):** O conceito de 'Usage-Based Insurance' (Seguro Baseado no Uso) é uma tendência global. Seguradoras têm grande interesse em dados que comprovem bons motoristas para oferecer descontos. O público de pais monitorando filhos recém-habilitados e frotas de empresas também é um alvo claro. O desafio é a concorrência com apps das próprias seguradoras.
- **Custo (Alto):** Alto custo de P&D para os modelos de IA. Custos recorrentes elevados com APIs de mapas para dados de limite de velocidade.

- **prós / contras**: 
**Prós:**
- Potencial de impacto social enorme na segurança do trânsito.
- Altamente inovador e com grande apelo de marketing.
- Abre portas para parcerias estratégicas com seguradoras e montadoras.
- Modelo de negócio claro (assinatura para usuários premium, venda de dados anonimizados para seguradoras).

**Contras:**
- Dificuldade técnica extrema para entregar a visão completa do produto.
- Risco de distração: o próprio app pode se tornar um risco se o motorista interagir com ele.
- Alto consumo de bateria e dados do celular.
- Questões de privacidade sobre monitorar e gravar o comportamento do motorista.

- **MVP**: 
Simplificar radicalmente, focando nos sensores mais confiáveis e deixando a Computer Vision para depois:
1.  **Monitoramento Baseado em Sensores:** Usar apenas GPS e acelerômetro.
2.  **Pontuação de Velocidade:** Comparar a velocidade do GPS com os limites de velocidade da via (obtidos via API de mapa). Pontuar por se manter no limite.
3.  **Pontuação de Suavidade:** Usar o acelerômetro para detectar e penalizar acelerações, freadas e curvas bruscas.
4.  **Relatório Pós-Viagem:** Ao final do percurso, mostrar um dashboard simples com a pontuação final e os pontos a melhorar (ex: "Você teve 3 freadas bruscas e excedeu o limite de velocidade 2 vezes").

- **sinergias**: 
- **Anjo da Guarda:** Uma sinergia poderosíssima. Uma pontuação de direção que cai abruptamente (ex: aceleração extrema seguida de parada brusca) pode ser um indicador de acidente ou outra emergência, acionando automaticamente um alerta do 'Anjo da Guarda'.
- **Aeria Selfware:** Pode ser o "Agente de Direção Pessoal", oferecendo dicas e relatórios semanais sobre como melhorar.

- **próximos passos**: 
1.  **Prova de Conceito (PoC):** Desenvolver um protótipo mínimo que apenas captura e exibe dados do acelerômetro em um gráfico durante uma viagem para validar a detecção de eventos bruscos.
2.  **Pesquisa de APIs de Mapas:** Levantar o custo e a viabilidade técnica de obter limites de velocidade em tempo real para ruas e avenidas no Brasil.
3.  **Análise de Concorrentes:** Estudar a fundo os aplicativos de seguradoras (ex: Porto Seguro Auto) para entender suas funcionalidades e modelos de pontuação.

