# Roadmap de Evolução

Este roadmap descreve melhorias planejadas para uma automação que já está ativa em produção. As iniciativas abaixo não são pré-requisitos para funcionamento do fluxo atual; elas representam oportunidades de amadurecimento operacional, aumento de robustez e ampliação do valor técnico da solução.

## 1. Processamento de Anexos

Objetivo: enriquecer a análise dos pedidos quando o cliente envia briefing, referência, planta, PDF, imagem ou planilha junto ao e-mail.

Possíveis implementações:

- Detectar presença de anexos no e-mail.
- Classificar anexos por tipo: PDF, imagem, planilha ou arquivo não suportado.
- Extrair texto de PDFs e documentos quando possível.
- Registrar metadados dos anexos: nome, tipo, tamanho e quantidade.
- Enviar conteúdo extraído para o LLM junto com o corpo limpo do e-mail.
- Diferenciar anexos usados na análise de anexos apenas registrados como referência.

Valor técnico:

- Demonstra tratamento de dados binários.
- Amplia o fluxo para além da leitura textual do e-mail.
- Melhora a qualidade da extração quando especificações técnicas estão em arquivos anexos.

## 2. Deduplicação e Controle de Reprocessamento

Objetivo: evitar duplicidade em cenários de reexecução, falha parcial ou recebimento de mensagens já processadas.

Possíveis implementações:

- Verificar `message_id` e `thread_id` antes de criar novo registro.
- Gerar hash do corpo limpo para detectar conteúdo repetido.
- Registrar motivo de descarte quando uma mensagem já tiver sido processada.
- Separar mensagens duplicadas reais de novas mensagens dentro da mesma thread.

Valor técnico:

- Aumenta confiabilidade operacional.
- Reduz inconsistência na base.
- Demonstra preocupação com idempotência.

## 3. Tratamento de Falhas e Observabilidade

Objetivo: tornar o fluxo mais rastreável em falhas de integração ou classificação.

Possíveis implementações:

- Criar caminhos específicos para falhas de LLM, Supabase, Gmail e Whapi.
- Registrar logs estruturados de erro.
- Aplicar label específica no Gmail para mensagens com falha.
- Criar tabela de eventos ou tentativas de processamento.
- Alertar a equipe quando uma etapa crítica falhar.

Valor técnico:

- Aproxima o workflow de práticas de operação contínua.
- Facilita diagnóstico de incidentes.
- Evita que falhas silenciosas interrompam o acompanhamento comercial.

## 4. Fila de Revisão Manual

Objetivo: encaminhar mensagens ambíguas ou incompletas para validação humana antes de gerar ação operacional.

Possíveis implementações:

- Criar status `REVISAO_MANUAL`.
- Enviar para revisão quando empresa, resumo ou tipo estiverem ausentes.
- Marcar divergências entre pré-filtro e classificação do LLM.
- Registrar o motivo da revisão.
- Permitir reprocessamento após ajuste manual.

Valor técnico:

- Reduz risco de falso positivo.
- Mostra desenho de human-in-the-loop.
- Mantém automação e decisão humana em pontos bem definidos.

## 5. Priorização Automática

Objetivo: destacar pedidos que exigem atenção mais rápida da equipe comercial.

Possíveis implementações:

- Adicionar campo `prioridade`: `ALTA`, `MEDIA` ou `BAIXA`.
- Criar `score_completude` baseado em presença de quantidade, medidas, prazo, local, anexos e contato.
- Considerar sinais de urgência, instalação, volume ou prazo curto.
- Destacar prioridade no alerta operacional.

Valor técnico:

- Transforma a automação em apoio à tomada de decisão.
- Ajuda a equipe a organizar atendimento.
- Cria uma camada de inteligência operacional além da classificação básica.

## 6. Workflow de Acompanhamento Comercial

Objetivo: ampliar o escopo da automação para o ciclo posterior ao recebimento do pedido.

Possíveis implementações:

- Criar workflow agendado para consultar registros `AGUARDANDO_RESPOSTA`.
- Alertar a equipe após determinado período sem atualização.
- Registrar data de último acompanhamento.
- Atualizar status conforme retorno comercial.

Valor técnico:

- Demonstra decomposição em múltiplos workflows.
- Conecta triagem inicial com rotina de follow-up.
- Ajuda a evitar perda de oportunidades comerciais.

## 7. Métricas e Visão Operacional

Objetivo: transformar registros do fluxo em indicadores úteis para gestão.

Possíveis implementações:

- Registrar datas de entrada, processamento e mudança de status.
- Medir volume de pedidos por período.
- Medir tempo médio até primeiro atendimento.
- Agrupar pedidos por tipo, prioridade e status.
- Preparar dados para dashboard futuro.

Valor técnico:

- Mostra preocupação com análise pós-processamento.
- Conecta automação com indicadores de negócio.
- Abre caminho para visualização operacional sem expor dados sensíveis.

## Priorização Recomendada

1. Processamento de anexos.
2. Deduplicação e controle de reprocessamento.
3. Tratamento de falhas e observabilidade.
4. Fila de revisão manual.
5. Priorização automática.
6. Workflow de acompanhamento comercial.
7. Métricas e visão operacional.

Essa ordem prioriza primeiro a expansão funcional mais relevante para o domínio da automação e, em seguida, reforça confiabilidade, governança e acompanhamento operacional.
