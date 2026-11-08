# USAGE — arqueologia-profunda

## Exemplos executados

- 2026-11-08 — repo de skill sem artefato binário (skill público de CLI:
  539 linhas de documento + 2 scripts auxiliares + assets), tier LEVE
  (denominador < 10 editáveis), swift carimbado vermelho declarado:
  - W-1/W0: `dex-bootstrap` instalou a base (AGENTS.md + `.agents/` +
    PLAYBOOK + hook pre-commit); censo `find-registry-skills.py --tag node`
    (32 matches) + `--tag documentation`; vault: zero memória do tema.
  - W0.5 adapter: `<EXT>` = .md/.html/.sh/.swift/.yaml; parser NATIVO
    inaplicável ao artefato (documento); métricas → PLANO B (CC manual).
  - W1: inventário por construção única `find -print0` (40 arquivos fora
    .git); build do dono = hook pre-commit `generate-playbook.py --repo .
    --check` + `bash -n` do script + dry-run URL sem rede.
  - W2: repo 100% CRLF (inclui .sh/.swift), zero BOM; ASCII puro nos
    códigos-fonte; UTF-8 válido sem BOM apenas nos docs .zh-CN (bytes
    medidos por `LC_ALL=C grep -c -P '[^\x00-\x7F]'` + `iconv` validação).
  - W3: grafo solto (zero import cruzado; varredura de asset refs e
    fetch/XHR vazia COM prova registrada).
  - W4/W4b: 3rd-party 2 colunas (npx MIT presente-fora-do-repo; litterbox
    externo; assets conteúdo-próprio); DEP-IA varrido — nenhum.
  - W5: padrão único de segredo `AGNES_API_KEY` (env var, nunca commitada)
    — zero valor de segredo no repo.
  - W6: harness 5 checks verdes + 1 vermelho DECLARADO (swift=127, owner
    amb macOS) — receipt JSON em `.agents/receipts/w6-build-proof.json`,
    exit 0 medido SEM pipe; gotcha pago ao vivo: hook pre-commit
    regenerou a projeção durante o commit → `--write` + re-stage na mesma
    transação.
  - W7/W8: tier leve — W7 = inventário+grafo do W3; W8 = plano B (CC
    manual: writeFirstFrame CC≈4; pódio God Class vazio declarado).
  - W9/W10: 6 memórias V2 `dex-memoria v2 remember` scope=project (6/6
    COMMITTED) + `validate-memory-batch.py` → `BATCH: 6/6 validos`;
    GATILHOS-VIVOS com molde 5 campos (CRLF-REPO-100-POR-CENTO,
    SWIFT-BUILD-AMB-MACOS, W6-HARNESS-RECEITA); pendência
    `SWIFT-BUILD-AMB-MACOS` no ledger schema v2 com bloco JSON; fechamento
    via `dex-fechamento-projeto-atualizado` (scan 12 superfícies +
    workflow-review) e commit local (identidade local do repo, sem config
    global).
  - Evidência viva: `<repo>/.agents/receipts/w6-build-proof.json` +
    `fechamento-20261108.json` + `.agents/memorias/` (6 L2).
