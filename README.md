# Mental Me | Chat Maria

## n8n Workflows 

Repositório simples para versionar e manter backup dos **workflows do n8n** usados no projeto.  
Os arquivos são exportados como **JSON** e o repositório é atualizado **de hora em hora** por uma automação (somente quando há mudanças).

## Estrutura

workflows/

├─ Chat-Maria.json

├─ Chat-Maria-\[TESTE].json

└─ Vector-Build.json

## Visão geral dos workflows

- **Chat-Maria.json**  
  Workflow principal do assistente (“Maria”). Orquestra o atendimento por chat: identifica intenção, coleta/valida dados passo a passo, consulta serviços externos (ex.: agendas/planos), registra interações e envia respostas. É o fluxo que roda em produção.

- **Chat-Maria-[TESTE].json**  
  Cópia para **homologação**. Mantém a mesma lógica do principal, porém com nós de **debug**, dados **mock** e gatilhos isolados para testar sem afetar o ambiente real.

- **Vector-Build.json**  
  Pipeline de **ingestão e embeddings**: recebe textos (transcrições, registros, notas), normaliza, gera vetores e faz **upsert** no banco vetorial (ex.: pgvector/Supabase). Suporta busca semântica e RAG em consultas futuras do assistente.

## Uso rápido

1. No n8n: **Workflows → Import** e selecione o arquivo `.json` correspondente.  
2. Configure as credenciais/variáveis diretamente na instância do n8n (este repositório **não** guarda segredos).  
3. Para testar, use o workflow **[TESTE]** antes de publicar alterações no **Chat-Maria**.

## Observações

- Commits automáticos: feitos por bot, sem incluir credenciais.  
- Mantenha nomes descritivos de nós e docs de mudanças em PRs para facilitar auditoria e rollback.

- Desenvolvido por **@ValeAdriano**.
