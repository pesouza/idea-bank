# Curso Offline para Viagens de Avião

**Criado em:** 05/06/2026
**Status:** 💡 Ideia inicial

## Resumo
Curso offline consumido durante voos — módulos curtos de ~20 minutos cada, totalizando ~10 horas de conteúdo. Aproveita o tempo ocioso do passageiro para aprendizado produtivo, sem necessidade de internet.

## Problema que Resolve
- Passageiros passam horas em voos sem fazer nada produtivo
- Conteúdo de streaming (filmes/séries) cansa ou não interessa
- Wi-Fi de bordo é caro, lento ou inexistente
- Cursos online tradicionais exigem conexão constante
- Falta de opções de aprendizado micro-estruturado para viagens

## Viabilidade: **Alta**
- Nenhuma tecnologia nova necessária
- Conteúdo pré-download (app ou site responsivo offline-first)
- Produção relativamente simples: áudio + texto + quiz simples
- Pode começar com um tópico só (ex.: inglês para viagem, inteligência artificial, finanças pessoais)
- Distribuição via app mobile (iOS/Android) com conteúdo empacotado

## Prós
✅ Niche claro: viajantes frequentes (business, turismo)
✅ Offline-first = sem dependência de infraestrutura
✅ Microlearning (20min) encaixa perfeitamente em voos
✅ Modelo B2B: companhias aéreas podem oferecer como diferencial
✅ Baixo custo de produção inicial (voz + slides/PDF)
✅ Replayability: pode ser refeito em voos diferentes
✅ Conteúdo reaproveitável em outras plataformas (Spotify, YouTube)

## Contras
❌ Descoberta: difícil o usuário encontrar o curso antes do voo
❌ Monetização direta via app pode ser baixa (público troca de app com frequência)
❌ Concorrência indireta: Audible, podcasts, Duolingo offline
❌ Tamanho do download precisa ser pequeno (dados móveis antes do voo)
❌ Se for multimodal (áudio + texto + vídeo), ocupa espaço no celular

## MVP
**"Inglês para Viajantes — 10 Horas de Bordo"**
1. Pacote de 30 lições de ~20min cada (10h totais)
2. Cada lição: áudio explicativo + texto de apoio + mini-quiz
3. App mobile simples (React Native ou PWA offline-first) com download único
4. Progressão por módulos: Básico → Intermediário → Situações de Viagem
5. Funcionalidade essencial: marcar progresso, continuar de onde parou

## Sinergias com Aer.IA
- **Selfware + WhatsApp**: distribuição via bot — usuário envia "quero o curso de inglês" e recebe as lições no WhatsApp em formato áudio/texto, consumíveis offline depois
- **Landing page em aeria-apps.com.br**: página de apresentação e download do pacote
- **Conteúdo gerado por IA**: Soph_IA pode produzir roteiros, quizzes e materiais de apoio
- **n8n**: automação de entrega do pacote, sequenciamento de lições, lembretes
- **Modelo freemium**: primeiras 5 lições grátis, pacote completo pago

## Monetização
1. **Compra única**: R$ 29-49 por pacote de curso (10h)
2. **Assinatura**: R$ 9,90/mês — acesso a todos os pacotes
3. **B2B com aéreas**: licenciamento para programas de bordo (ex.: Latam, Gol, Azul)
4. **Bundles temáticos**: "Viagem aos EUA" (inglês + cultura + dicas práticas)
5. **Upgrade para certificado**: R$ 19 para emitir certificado de conclusão

## Próximos Passos
1. Validar com 5-10 viajantes frequentes se fariam um curso de 10h em voo
2. Definir o primeiro tópico (recomendo: inglês prático para viagens)
3. Produzir 3 lições piloto (roteiro + áudio + quiz) e testar com usuários reais
4. Construir MVP em PWA (rápido, sem loja de apps)
5. Testar distribuição via WhatsApp (Selfware) antes de app dedicado
