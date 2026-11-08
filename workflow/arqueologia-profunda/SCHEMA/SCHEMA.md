# SCHEMA — arqueologia-profunda

Contrato de entrada/saída da arqueologia profunda genérica (W-1 a W10, multi-linguagem).

## Contrato

- Entradas:
  - `<REPO>` — raiz do projeto-alvo (qualquer linguagem sem dialeto dedicado; skill/documento + scripts auxiliares incluído).
  - Adapter da linguagem (W0.5): extensões de fonte `<EXT>`, denominador de tier, parser NATIVO (Tree-sitter sim/não), ferramenta de métricas + cobertura.
  - Script de build REAL do dono (quando existir) — fonte do argv; repo sem build → gate textual/hook do dono declarado.
- Saídas:
  - `<REPO>/.agents/receipts/` — receipt JSON de build (rota verde) + receipt de fechamento.
  - `<REPO>/.agents/` — ACTIVE, HANDOFF, GATILHOS-VIVOS (molde 5 campos), napkin, PENDENTES (schema v2 + bloco JSON), PLAN-TASKS, LIXEIRA/MANIFEST.md, `memorias/` + `lembranca.md` (via dex-memoria V2).
  - Raiz: `AGENTS.md` (build exato + status verde/vermelho + tabela Enc REAL + Painel de Ferramentas), `INDEX.md` (árvore com sub-indices), `DEPENDENCIES.md`/`NAMES.md` (quando aplicável).
  - Relatório final na conversa: inventário + tabela Enc, grafo, receipt, gate exit 0 SEM pipe, pódio, delta do Painel, contagem de memoráveis/tropeços + gatilhos L1 + créditos.
- Registro de meta-análise questionadora:
  - Entrada: snapshot do resultado/SPT, evidências, premissas e dependências.
  - Saída: registro no Trilho/relatório com revisão/hash, perguntas/respostas, oráculo/motivo, corpus reaberto, parecer, decisão/justificativa, impactos, ação, responsável, quando e prova.
  - Gate: executar antes de fechar e entre SPTs; checker verde prova estrutura, não consulta.
- Critérios de pronto:
  - Gate de CADA W fechado (verificações ✅) ou lacuna com owner/quando.
  - Build: exit 0 REAL medido SEM pipe + receipt JSON, OU rota vermelha completa (carimbo "build: NAO PROVADO" + pendência com owner/quando).
  - Memórias V2 validadas em lote (`validate-memory-batch.py` → `BATCH: N/N validos`); LIXEIRA com MANIFEST para resíduo.
  - Checklist W10 completo + contagens + créditos públicos.
