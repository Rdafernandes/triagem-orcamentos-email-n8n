# Workflows

Esta pasta contém apenas exports públicos sanitizados.

- `sanitizados/`: workflows revisados para publicação.

Exports originais de produção não devem ficar neste repositório. A pasta `workflows/originais/` permanece listada no `.gitignore` como proteção adicional caso algum export privado seja usado em análises futuras.

## Importação

O workflow sanitizado está desativado (`active: false`) e contém placeholders em credenciais, labels, tabela Supabase, caixa monitorada e destino WhatsApp. Para uso em outro ambiente, esses valores precisam ser configurados manualmente no n8n.
