# Samples

Esta pasta contém exemplos públicos fictícios baseados na estrutura real dos outputs observados em execução teste do workflow.

Os valores foram substituídos por dados neutros ou placeholders, mas os campos preservam os estados relevantes do fluxo.

## Organização

- `entrada/email-recebido.sanitizado.json`: estrutura do e-mail recuperado pelo Gmail.
- `processamento/pre-filtro.sanitizado.json`: saída do Code node de pré-filtro.
- `processamento/classificacao-llm.sanitizado.json`: JSON estruturado pelo LLM.
- `distribuicao/registro-supabase.sanitizado.json`: registro criado na base operacional.
- `distribuicao/label-gmail.sanitizado.json`: retorno após aplicação de label no Gmail.
- `distribuicao/mensagem-whatsapp-preparada.sanitizado.json`: mensagem montada para envio operacional.
- `distribuicao/envio-whapi.sanitizado.json`: retorno sanitizado do envio pelo Whapi.

## Cuidados

- Não incluir payloads reais.
- Não incluir nomes reais.
- Não incluir telefones, e-mails ou documentos reais.
- Não incluir anexos de clientes.
- Não incluir conteúdo bruto de e-mails.
