# MVP Técnico v2 — ThermaScan Performance

## Objetivo do MVP
Validar se academias e estúdios conseguem usar imagens térmicas pré/pós-treino para obter um relatório visual simples de sobrecarga muscular, sem prometer diagnóstico médico.

## Escopo do MVP
### Inclui
- cadastro de aluno
- cadastro de sessão de avaliação
- upload de 2 imagens térmicas: pré e pós-treino
- validação automática de postura
- alinhamento visual das imagens
- comparação térmica por região
- relatório simples com destaque de áreas com maior variação
- histórico por aluno
- exportação básica em PDF ou imagem compartilhável

### Não inclui no MVP
- detecção clínica de lesão
- integração com prontuário médico
- recomendação médica automática
- análise multi-câmera complexa
- app nativo completo no início

## Fluxo do usuário
1. Profissional entra no painel da academia
2. Seleciona ou cadastra o aluno
3. Inicia uma nova avaliação
4. Captura ou envia a imagem térmica pré-treino
5. Captura ou envia a imagem térmica pós-treino
6. Sistema verifica postura e enquadramento
7. Sistema alinha as imagens
8. Sistema calcula delta térmico por região
9. Sistema gera score visual de atenção
10. Profissional revisa e salva
11. Aluno recebe resumo/relatório

## Fluxo técnico
```text
Upload imagem pré
  -> checagem de qualidade
  -> detecção de pose
  -> segmentação/recorte de regiões
  -> normalização térmica
  -> armazenamento

Upload imagem pós
  -> checagem de qualidade
  -> detecção de pose
  -> segmentação/recorte de regiões
  -> alinhamento com imagem pré
  -> cálculo de diferença térmica
  -> geração do relatório
```

## Telas do MVP
### 1. Login / acesso
- entrada da academia
- recuperação de senha
- seleção de unidade, se houver mais de uma

### 2. Dashboard
- alunos recentes
- últimas avaliações
- alertas de sessões com variação alta
- botão "Nova avaliação"

### 3. Cadastro de aluno
- nome
- idade
- sexo
- objetivo
- observações opcionais
- termos de consentimento

### 4. Nova avaliação
- selecionar aluno
- selecionar tipo de avaliação
- iniciar captura pré-treino
- iniciar captura pós-treino

### 5. Captura de imagem
- preview da câmera termográfica
- guia visual de postura
- indicador de qualidade da imagem
- botão de confirmar captura

### 6. Análise automática
- status de processamento
- validação de pose
- alinhamento
- comparação térmica

### 7. Relatório da sessão
- mapa corporal com destaque por região
- áreas de maior e menor variação
- observações automáticas
- campo para anotação do profissional
- salvar e exportar

### 8. Histórico do aluno
- linha do tempo das avaliações
- filtros por período
- comparação entre sessões
- evolução visual

## Regras de negócio do MVP
- só permitir comparação quando a pose estiver dentro do padrão mínimo
- bloquear captura com imagem muito desfocada ou mal enquadrada
- exigir consentimento do aluno antes do primeiro uso
- guardar histórico por sessão e por aluno
- registrar que o resultado é de **monitoramento**, não diagnóstico

## Arquitetura sugerida
### Frontend
- painel web para academia
- captura via tablet/celular no início

### Backend
- API de autenticação
- API de alunos e sessões
- API de upload de imagens
- API de relatórios

### Pipeline de visão
- detecção de pose
- segmentação de regiões de interesse
- alinhamento entre pré e pós
- cálculo de delta térmico
- geração de score por região

### IA / automação
- resumo textual da análise
- sugestão de próximos passos
- geração de observações para o treinador

### Persistência
- banco relacional para metadados
- storage de objetos para imagens térmicas
- cache para resultados de processamento

## Stack recomendada para iniciar
- **Frontend**: Next.js
- **Backend**: FastAPI ou NestJS
- **Banco**: PostgreSQL
- **Storage**: S3 compatível
- **IA/Vision**: Python com OpenCV + modelo de pose/segmentação
- **PDF/relatórios**: geração server-side

## Integração com aeria-apps.com.br
- página pública do produto
- formulário de interesse de academias
- área de demonstração
- catálogo de módulos da Aeria
- possibilidade de vender como add-on premium para clínicas, estúdios e academias

## Métrica de validação do MVP
- número de academias interessadas
- taxa de uso por aluno
- tempo médio de captura
- qualidade percebida do relatório
- intenção de compra após demonstração

## Próximos passos práticos
1. desenhar wireframe das 8 telas
2. criar landing page com CTA para piloto
3. escolher câmera termográfica compatível
4. construir protótipo de upload + comparação
5. testar com 1 academia parceira
6. ajustar linguagem e usabilidade
7. validar preço e formato comercial
