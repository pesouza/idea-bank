# Aplicativo de análise térmica muscular pré/pós-treino

- **nome da ideia**: App de leitura térmica muscular pré e pós-treino
- **resumo**: Aplicativo que compara duas imagens termais, captadas antes e depois do treino, para destacar regiões com maior e menor variação térmica e sinalizar padrões compatíveis com sobrecarga, edema e risco de lesão. Voltado para academias, estúdios e acompanhamento individual de clientes.
- **problema que resolve**: Hoje, a avaliação de esforço muscular e recuperação costuma depender de percepção subjetiva, dor relatada e observação manual. O app ajuda a transformar imagem térmica em um indicador visual e padronizado de possível sobrecarga e desequilíbrio de esforço.
- **viabilidade**: **média-alta**. Tecnicamente é possível, e o uso de *YOLO Pose* para validar a postura antes da captura aumenta a confiabilidade do pipeline. O uso de *YOLO Segmentation* para acompanhar regiões musculares de interesse também melhora a consistência da análise. Ainda assim, o maior risco continua sendo a qualidade dos dados, a padronização da captura, a variabilidade das câmeras e a necessidade de evitar promessas médicas indevidas. Como produto de suporte à performance e monitoramento, a ideia fica bem mais sólida do que como ferramenta diagnóstica.
- **prós / contras**:
  - **Prós**:
    - Diferenciação forte em academias e estúdios premium
    - Valor visual alto para treinador e cliente
    - Pode gerar retenção por acompanhamento de evolução
    - Pode ser integrado a planos de treino, check-ins e relatórios
    - Pode criar um posicionamento mais científico para a academia
  - **Contras**:
    - Exige câmera termográfica compatível e protocolo de captura
    - Risco de falso positivo / falso negativo sem validação robusta
    - Pode entrar em zona regulatória sensível se prometer diagnóstico
    - Mercado B2B pode ser lento para adoção
    - Necessita integração cuidadosa com rotina da academia para não virar “mais uma ferramenta”
- **MVP**:
  1. Cadastro do aluno e do treino
  2. Upload de imagem térmica pré e pós-treino
  3. Comparação automática com sobreposição de mapa de calor
  4. Destaque de regiões com maior delta térmico
  5. Relatório simples com interpretação orientada a performance: “áreas de maior carga”, “áreas de menor resposta”, “sinal de atenção para recuperação”
  6. Histórico por atleta com evolução ao longo do tempo
- **sinergias**:
  - Pode virar módulo de saúde/performance dentro da `aeria-apps.com.br`
  - Sinergia com um sistema de ficha do aluno, treino, check-in e evolução física
  - Pode ser combinado com IA para gerar relatórios automáticos e recomendações de recuperação
  - Pode ser oferecido como add-on premium para academias parceiras
  - Pode integrar com outras ideias de wellness, fisioterapia, nutrição ou recovery
- **próximos passos**:
  1. Definir o posicionamento correto: *monitoramento de performance* e não *diagnóstico médico*
  2. Validar quais câmeras termográficas serão suportadas
  3. Validar a pose com *YOLO Pose* antes de aceitar a captura
  4. Usar *YOLO Segmentation* para marcar regiões musculares de interesse
  5. Criar um protótipo que compare as imagens e destaque diferenças
  6. Conversar com 2 a 5 profissionais de educação física / fisioterapia para validar valor percebido
  7. Montar uma landing page na `aeria-apps.com.br` para captar interesse de academias
  8. Avaliar precificação B2B por unidade, por aluno ou por academia
  9. Fazer uma revisão de compliance antes de qualquer promessa de edema/lesão
- **análise de mercado**:
  - O mercado é nichado, mas com apelo forte em academias premium, estúdios de performance, fisioterapia esportiva e centros de recuperação.
  - A dor existe, mas a compra depende de demonstração clara de valor.
  - O melhor ângulo de mercado é vender como ferramenta de *insight visual* para treino, recuperação e retenção de alunos, não como dispositivo clínico.
- **monetização**:
  - Assinatura mensal por academia/estúdio
  - Licença por unidade com limite de alunos
  - Cobrança por avaliação realizada
  - Plano premium com relatórios e histórico
  - Serviço de implementação + treinamento + suporte
- **sugestões de nome**:
  - ThermaFit
  - HeatTrace
  - PulseMap
  - ThermoTrack Pro
  - CoreHeat
  - BioHeat Scan
- **arquitetura sugerida**:
  - **Frontend**: web app para academia e app mobile para captura/consulta
  - **Backend**: API para autenticação, armazenamento e processamento de imagens
  - **Processamento**: serviço de visão computacional com *YOLO Pose* para validação de postura, *YOLO Segmentation* para regiões musculares de interesse e alinhamento/comparação térmica
  - **IA**: camada para resumo automático e recomendações de recuperação
  - **Dados**: banco relacional para alunos, sessões, imagens, métricas e laudos gerados
  - **Armazenamento**: objeto para imagens termográficas
  - **Integração**: painel dentro da `aeria-apps.com.br` com gestão de alunos, planos e relatórios
- **observação importante**: A proposta é promissora, mas precisa de linguagem cuidadosa. O produto deve evitar afirmar que detecta lesões com certeza. O correto é posicioná-lo como apoio à análise de esforço, assimetria térmica e alerta de acompanhamento.

## versão 2.0

### nome da ideia
ThermaScan Performance / ThermoFit Insight / HeatMap Recovery

### resumo
Plataforma de leitura térmica esportiva que compara imagens pré e pós-treino, valida a postura com visão computacional, segmenta regiões musculares de interesse e gera um relatório de atenção por grupo muscular. Voltada para academias, estúdios, fisioterapia esportiva e performance.

### problema que resolve
A academia normalmente não consegue mostrar, de forma visual e padronizada, onde houve maior carga, assimetria ou possível necessidade de recuperação. Isso reduz a percepção de valor do acompanhamento e dificulta intervenções preventivas.

### viabilidade
**média-alta** como produto de performance. O core é viável se houver protocolo de captura e posicionamento cuidadoso. O maior risco não é o algoritmo em si, mas a consistência da captura, a calibração da câmera e o enquadramento regulatório da comunicação.

### prós / contras
- **Prós**:
  - Diferencial forte para academias que querem vender experiência premium
  - Gera prova visual imediata para o cliente
  - Ajuda retenção e pode ser usado como relatório recorrente
  - Pode ser integrado à jornada do aluno na `aeria-apps.com.br`
  - Abre espaço para upsell de acompanhamento de recovery
- **Contras**:
  - Exige hardware e protocolo de captura
  - Pode gerar ruído se a pose não estiver padronizada
  - Precisa cuidado para não soar como diagnóstico médico
  - Pode ter adoção mais lenta se o valor não for demonstrado rápido

### MVP
1. Captura guiada do aluno antes e depois do treino
2. Validação de pose com *YOLO Pose*
3. Segmentação de regiões musculares com *YOLO Segmentation*
4. Comparação térmica por região
5. Relatório com score visual e resumo textual
6. Histórico por aluno com evolução semanal

### sinergias
- Painel dentro da `aeria-apps.com.br` como módulo de performance
- Base de dados compartilhada com ficha do aluno, treino e evolução
- Possibilidade de cruzar com outras ideias de wellness, nutrição e recovery
- Pode virar produto de entrada para vender serviços maiores de consultoria e automação para academias

### próximos passos
1. Definir o discurso do produto como monitoramento e não diagnóstico
2. Escolher 1 câmera termográfica inicial para suporte oficial
3. Criar um fluxo de captura simples e repetível
4. Fazer um protótipo funcional com upload de duas imagens
5. Testar com 1 academia piloto
6. Validar preço e percepção de valor
7. Subir uma landing page de pré-venda

### escambo com academia parceira
A ideia do escambo pode funcionar bem como aquisição de piloto:
- oferecer o desenvolvimento da beta sem custo inicial de caixa
- em troca, a academia concede um pacote de mensalidades, acesso ao espaço e uso com alunos reais
- o contrato pode ser em formato de **crédito de serviço**: o valor do desenvolvimento é convertido em mensalidades da academia até quitar um montante combinado
- alternativa: **piloto com exclusividade temporária** na região em troca do desenvolvimento e uso do logo como case
- importante deixar claro:
  - prazo do piloto
  - quantidade de alunos incluídos
  - entregáveis da beta
  - limites de suporte
  - autorização de uso de imagem e dados
  - cláusula de cancelamento se o piloto não entregar valor

### landing page sugerida
**Objetivo:** captar academias parceiras e agendar piloto.

**Seções principais:**
- Hero com promessa clara: "Veja a resposta muscular do treino em imagens térmicas"
- Subtítulo reforçando performance e recuperação, não diagnóstico
- 3 benefícios principais:
  - visualização da sobrecarga
  - acompanhamento de evolução
  - aumento do valor percebido da academia
- Como funciona em 3 passos:
  - captura pré-treino
  - captura pós-treino
  - relatório comparativo
- Mockup da tela com mapa térmico
- Bloco "para quem é" com academias, estúdios e fisioterapia esportiva
- Prova / autoridade: parceria piloto, depoimentos, validação técnica futura
- CTA forte: "Quero testar na minha academia"
- FAQ com transparência sobre limitações e uso seguro

### monetização
- assinatura mensal por academia
- taxa de implantação da beta
- cobrança por aluno analisado
- plano premium com relatórios avançados e histórico
- add-on para academias da `aeria-apps.com.br`

### arquitetura sugerida
- frontend web para gestão e landing page
- app mobile ou web responsivo para captura guiada
- backend com autenticação, cadastro e sessão por aluno
- módulo de visão computacional para pose + segmentação + comparação térmica
- storage de imagens e relatórios
- camada de IA para gerar resumo e recomendações de recuperação

### síntese estratégica
A versão 2.0 fica mais vendável se o foco for: **produto de performance visual para academias premium**.
O caminho mais inteligente é validar com um piloto escambo, usar isso para gerar case, e depois transformar a landing page da `aeria-apps.com.br` no canal principal de aquisição.
