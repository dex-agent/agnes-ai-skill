# RULES — workflow/

Regras do ecossistema local (valem para TODOS os pacotes; hierarquia tipo AGENTS.md).

## Regras

- R1: antes de trabalho similar, consultar o INDEX deste diretório.
- R2: pacote existente cobre o caso → lapidar (CHANGELOG do pacote), não criar irmão.
- R3: seguir o WORKFLOW.md do pacote de ponta a ponta (cold-start); ajuste vira lapidação.
- R4: pacote `stale|superseded` → revalidar contra o estado vivo antes de seguir.
- R5: slug nunca renomeia; escopo mudou → slug novo + antigo `superseded`.
- R6: o RULES.md do pacote estreita estas regras; a mais específica vence no seu escopo.
- R7: todo pacote nasce com Meta-análise questionadora autocontida e verificável antes de fechar e entre SPTs; o checker valida estrutura, o executor produz prova.

## Limites

- criar/admitir pacote novo → skill `dex-criar-workflow-contexto-atual`.
- R13 global: esta instância usa o slug do template global (`arqueologia-profunda`); dados do repo entram nos placeholders/config locais, nunca no template.
