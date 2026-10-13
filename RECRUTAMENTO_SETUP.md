# QG NVB — Painel de recrutamento

Este pacote adiciona ao site QG NVB um painel de links individuais de recrutamento.

## Variáveis necessárias no Render

- `DISCORD_TOKEN`: token do aplicativo Discord usado pelo serviço QG.
- `CLIENT_ID`: ID do aplicativo Discord.
- `GUILD_ID`: ID do servidor NVB.
- `QG_PUBLIC_URL`: URL pública final do site, por exemplo `https://seu-site.onrender.com` (sem barra final).
- `RECRUT_CHANNEL_ID`: ID do canal que recebe as fichas. Padrão: `1555845609343164436`.
- `RECRUITER_ROLE_IDS`: IDs dos cinco cargos autorizados separados por vírgulas. O padrão já contém os cinco IDs fornecidos.
- `MAIN_DISCORD_INVITE`: convite enviado por DM quando a ficha é aprovada. Configure como `https://discord.gg/63S5czrN4` se já existir uma variável antiga no Render.

## Funcionamento

- O painel fica dentro da área interna do QG.
- A permissão é conferida no servidor, consultando os cargos reais do membro no Discord.
- Cada link recebe um código aleatório e expira em sete dias.
- O link é salvo em `recrutamento_links.json`.
- O serviço tenta enviar o link por mensagem privada ao recrutador. Se as DMs estiverem bloqueadas, o painel mostra o link para copiar.
- Formulários enviados com link inválido ou expirado são rejeitados.
- As fichas são encaminhadas ao canal configurado.
- Ao aprovar, o QG tenta enviar ao recrutado uma DM com o convite `https://discord.gg/63S5czrN4`, o link do site e o código de entrada.

## Importante

Este pacote precisa ser testado no Render após configurar as variáveis e permissões do bot. O Discord bot precisa estar no servidor, ter acesso aos membros e permissão para enviar mensagens no canal de recrutamento. Em hospedagens efêmeras, use disco persistente ou banco de dados para não perder arquivos JSON durante reinicializações/deploys.
