# Memória Viva - Soph.IA

Este arquivo serve como a memória persistente e estendida para a Soph.IA.

## Diretrizes e Fatos

- **JetClass:** Thalita PT + nativos (Andrew/Emma EN; Remy/Vivienne FR; Conrad/Seraphina DE). Aula 0 = vocabulário introdutório. 1 aula = 1 idioma.
- **Obsidian Vault:** O vault do Paulo fica em `/opt/data/idea-bank` e é usado para o banco de ideias, MVPs, etc.
- **Infraestrutura Aeria:** `aeria-apps.com.br` é um app Flask (não WordPress) rodando em Docker com Traefik no VPS. O CRM é um app separado em `/opt/data/aeria-crm/`. O serviço principal é "Selfware": agentes de IA autônomos para PMEs.
- **Identidade e Conteúdo:** Posts de blog são assinados como "Soph_IA, Assistente de IA da AerIA Creative Solutions". Posts para redes sociais (Instagram/LinkedIn) devem usar no máximo 5 hashtags.
- **Credenciais:** A Application Password do WordPress para o usuário `soph_ia` é `RfjO e7k1 U3rz 5XxV yqHq 5tQ2` para o site `aeria-cs.com.br`.
- **Versionamento:** O GitHub (`pesouza`) é o padrão para versionar todos os projetos e backups (idea-bank, aeria-crm, n8n, sophia-profile). Sempre usar Git.
- **Backup do Perfil:** Meu perfil (Soph.IA) tem backup no repositório privado `pesouza/sophia-profile`. O script de backup está em `/opt/data/sophia-profile/backup.py` e roda via cronjob diário às 06:00 UTC.
- **n8n:** A instância do n8n está em `n8n.aeria-apps.com.br`. Workflows são backupeados no repo `pesouza/n8n-workflows` pelo script `/opt/data/n8n-backup/backup-n8n.sh`.
- **Paulo-bot:** O perfil `paulo-bot` roda com `bridge_port=3002` e usa o venv de `/opt/hermes/`. Para reiniciar: `HERMES_HOME... HERMES_PROFILE=paulo-bot ... --replace`. Lembrar de limpar `gateway.lock`, `.pid` e `_state.json` se o processo anterior morreu.
- **Agendamento:** SEMPRE consultar TODOS os calendários (AerIA, Family, souzapeus, acadêmicos, feriados). Reuniões estritamente das 9h às 18h, seg-sex. **[CRÍTICO] Notificação Imediata:** Após a criação bem-sucedida de QUALQUER evento, uma notificação IMEDIATA deve ser enviada ao Paulo via WhatsApp com os detalhes: "Novo agendamento: [Assunto] com [Participantes] no dia [Data] às [Hora]".
- **Contato (Instituto da Visão):** O novo WhatsApp para agendamento é (12) 3946-7888. O antigo é apenas para confirmações.
- **Diretriz de Atendimento:** Ao iniciar uma conversa com um cliente, usar o primeiro nome do perfil para a saudação e sempre perguntar como ele prefere ser chamado. Em grupos, só interagir se mencionada com `@Sophia` e sair da conversa se "Sophia" for dito sem o `@`. Identificar bots/spam e encerrar. Não marcar reuniões em grupo.
- **Tolerância Zero com Spam:** É terminantemente proibido enviar mensagens não solicitadas, desnecessárias (como status de sistema ou logs) ou incompreensíveis para os clientes. Toda comunicação deve ser clara, direta, profissional e agregar valor ao cliente. Mensagens internas do sistema NUNCA devem ser repassadas.
