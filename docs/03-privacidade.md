# Privacidade e Sanitização

## Dados Sensíveis Encontrados no Material Original

- Credenciais de Gmail, Supabase e DeepSeek.
- Token Bearer usado no HTTP Request.
- IDs de webhooks.
- IDs de labels do Gmail.
- ID de grupo ou destinatário de WhatsApp.
- ID da instância n8n.
- ID de workflow de erro.
- `pinData`.
- Nomes pessoais e dados operacionais.
- Domínio/e-mail interno usado no filtro do Gmail.
- Conteúdo real de e-mail e retorno real de API.

## Regras Aplicadas

- Remoção de `credentials`.
- Remoção de `webhookId`.
- Remoção de `pinData`.
- Remoção de `id`, `versionId`, `meta` e `tags` do workflow.
- Desativação do workflow público com `active: false`.
- Substituição de token, label, grupo WhatsApp, tabela Supabase e caixa monitorada por placeholders.
- Substituição de e-mails e destinatários por placeholders.
- Remoção dos exports originais e outputs reais do diretório do projeto.

## Arquivos Publicáveis

- `README.md`
- `docs/`
- `samples/`
- `assets/`
- `workflows/sanitizados/`

## Arquivos Não Publicáveis

- qualquer export original de produção;
- qualquer output real de execução;
- qualquer payload bruto de cliente;
- screenshots com painel de credenciais, URLs privadas, tokens, nomes reais ou dados operacionais;
- arquivos com `pinData`.

## Critério Final

Se houver dúvida sobre um dado, ele deve ser tratado como sensível e substituído por placeholder.
