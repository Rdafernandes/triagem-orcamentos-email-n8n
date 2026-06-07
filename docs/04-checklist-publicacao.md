# Checklist de Publicação

## Estrutura

- [x] Criar `.gitignore`.
- [x] Remover exports originais e outputs reais do projeto.
- [x] Criar pasta de workflows sanitizados.
- [x] Criar documentação inicial.
- [x] Adicionar samples fictícios baseados na estrutura real.
- [x] Definir screenshot pública recomendada.
- [x] Adicionar arquivo da screenshot pública em `assets/screenshots/workflow-completo.png`.

## Workflow Sanitizado

- [x] JSON válido.
- [x] Topologia preservada.
- [x] `pinData` removido.
- [x] `credentials` removidas.
- [x] `webhookId` removidos.
- [x] IDs internos principais removidos.
- [x] Token Bearer substituído por placeholder.
- [x] ID de grupo/destino WhatsApp substituído por placeholder.
- [x] Domínio/e-mail interno substituído por placeholder.
- [x] Code node validado com `node --check`.

## Assets

- [x] Screenshot do canvas completo revisada.
- [x] Captura sem painel lateral de configuração.
- [x] Captura sem payloads, tokens, credenciais ou dados de cliente visíveis.
- [x] Arquivo da screenshot salvo dentro do projeto.
- [x] Screenshot inserida no README.

## Validações Finais

- [x] Todos os JSONs publicáveis foram validados.
- [x] Links Markdown e imagens foram conferidos.
- [x] Varredura final por tokens, e-mails reais, telefones, URLs privadas, IDs e nomes reais conhecidos foi executada.
- [x] Pasta `workflows/originais/` não existe no projeto.

## Status Final

O projeto está pronto para upload manual no GitHub.
