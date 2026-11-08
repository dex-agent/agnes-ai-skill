---
schema: dex.workflow.capacity.v1
fotografia_id: arqueologia-profunda-nascimento-2026-11-08
fotografia_date: '2026-11-08'
---

# CAPACITY — arqueologia-profunda

## Capacidades comprovadas

| # | Capacidade | Oracle | Evidencia | Status |
|---|---|---|---|---|
| 1 | Arqueologia W-1..W10 completa em repo de skill/documento sem artefato binário (tier leve) | W6 exit 0 SEM pipe + receipt JSON | `.agents/receipts/w6-build-proof.json` (5 verdes + 1 vermelho declarado) | executado_ao_vivo |
| 2 | Memórias locais V2 via dex-memoria scope=project + validação em lote | `BATCH: 6/6 validos` | `validate-memory-batch.py --root .agents` (2026-11-08) | executado_ao_vivo |
| 3 | Fechamento com scan de 12 superfícies + workflow-review + commit | receipt fechamento com REDs rotacionados | `.agents/receipts/fechamento-20261108.json` + commit local | executado_ao_vivo |

## Laudo

- **Confirmadas**: arco completo W-1..W10 ao vivo no repo de skill público (tier leve, swift carimbado vermelho declarado com owner de ambiente).
- **Limites declarados**: repos de linguagem pesada com toolchain (Delphi/PHP/Node com build real) ainda têm dialetos próprios — este template cobre o núcleo genérico; W7 com parser Tree-sitter em repo JS/TS pesado não foi reexecutado na captura (capacidade herdada da skill nuclear `arqueologia-warmup-base` + dialetos irmãos).
