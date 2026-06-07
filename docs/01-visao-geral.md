# Visão Geral

Este workflow automatiza a triagem de pedidos de orçamento recebidos em uma caixa de e-mail comercial.

O fluxo acompanha mensagens não lidas, busca o conteúdo completo do e-mail, limpa o texto, descarta respostas ou encaminhamentos, identifica candidatos a novo pedido de orçamento e usa LLM para classificar e extrair dados estruturados.

Quando a mensagem é confirmada como novo orçamento, o workflow registra o atendimento no Supabase, aplica uma label de processamento no Gmail e envia um alerta operacional via WhatsApp.

## Responsabilidades Principais

- Monitorar a entrada de e-mails comerciais.
- Reduzir falsos positivos antes de acionar o LLM.
- Classificar a mensagem em categorias operacionais.
- Extrair contato, empresa, data, hora e resumo técnico.
- Registrar o item para acompanhamento.
- Avisar a equipe responsável.

## Categorias Usadas pelo LLM

- `NOVO_ORCAMENTO`
- `REVISAO_ORCAMENTO`
- `DUVIDA`
- `OUTRO`

## Critério de Sucesso

O workflow é considerado bem-sucedido quando identifica um novo pedido de orçamento, registra os dados estruturados e prepara a comunicação operacional sem reprocessar o mesmo e-mail.
