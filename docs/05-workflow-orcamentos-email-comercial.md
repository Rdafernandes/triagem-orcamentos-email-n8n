# Workflow: Orçamentos Recebidos por E-mail Comercial

## Objetivo

Identificar novos pedidos de orçamento recebidos por e-mail, estruturar os dados principais, registrar o atendimento e alertar a equipe comercial.

## Topologia

1. `Gmail Trigger`
2. `Get Message Content`
3. `Pré-Filtro`
4. `If`
5. `Basic LLM Chain`
6. `DeepSeek Chat Model`
7. `If1`
8. `Create a row`
9. `Adicionar label orc_processado`
10. `Estruturar mensagem`
11. `Whapi - Alertar Grupo`

## Pré-Filtro

O Code node executa três tarefas principais:

- converte HTML em texto;
- remove histórico de conversas, respostas e encaminhamentos;
- marca a mensagem como candidata quando há indícios de pedido de orçamento no assunto ou corpo.

Essa etapa reduz acionamentos desnecessários do LLM e evita que conteúdos antigos da thread influenciem a classificação.

## Classificação por LLM

O LLM recebe remetente, e-mail do remetente, assunto, data e corpo limpo. Ele deve retornar somente JSON com:

- `tipo`;
- `e_novo_orcamento`;
- `nome_contato`;
- `empresa`;
- `data_recebido`;
- `hora_recebido`;
- `resumo`.

## Persistência

Quando o resultado final é `NOVO_ORCAMENTO`, o workflow cria um registro no Supabase com dados da mensagem, dados extraídos e status inicial `AGUARDANDO_RESPOSTA`.

## Comunicação Operacional

Após o registro, o workflow aplica uma label de processado no Gmail e monta uma mensagem para envio ao canal operacional de WhatsApp.

O retorno do node Whapi foi documentado em sample público com ID de mensagem, destino, remetente e corpo sanitizados.

## Sanitização

A versão pública remove credenciais, IDs internos, webhooks, token, ID de grupo/destino, e-mail/domínio interno, dados de instância e `pinData`.
