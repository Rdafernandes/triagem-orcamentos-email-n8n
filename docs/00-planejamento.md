# Planejamento do Repositório

## Estado Atual

- Exports originais do n8n foram usados apenas para análise local.
- Outputs reais de execução foram usados apenas para entender a estrutura dos dados.
- Exports originais, outputs reais e dados sensíveis foram removidos do projeto antes da preparação para upload.
- A pasta `workflows/originais/` permanece no `.gitignore` como proteção adicional.
- O workflow público está em `workflows/sanitizados/01-orcamentos-email-comercial.sanitizado.json`.
- A documentação inicial foi criada com base na arquitetura real do fluxo.
- Os samples públicos foram criados com dados fictícios e placeholders, mantendo a estrutura observada nos outputs reais.
- A screenshot pública do canvas completo está em `assets/screenshots/workflow-completo.png`.
- O roadmap documenta melhorias planejadas para uma automação já ativa em produção.

## Decisões de Publicação

- Publicar somente o workflow sanitizado.
- Não publicar prints de configuração interna dos nodes.
- Não publicar payloads brutos de e-mail, respostas reais de API ou outputs com `pinData`.
- Usar exemplos fictícios para demonstrar evolução dos dados.
- Manter documentação suficiente para avaliação técnica sem exigir acesso ao ambiente original.
- Separar claramente funcionalidades implementadas de evoluções planejadas.

## Status

Nenhum insumo adicional obrigatório. O projeto está pronto para upload manual no GitHub.
