# RULES — arqueologia-profunda

Regras do workflow, escritas para LLM (declarativas, rotuladas, sem prosa).
Estreita `workflow/RULES.md` do ecossistema global.

## Regras

- R1: READ-ONLY no código-fonte do alvo até o build verde (W6); na rota vermelha PERMANECE read-only até correção externa. Escritas de evidência SÓ sob `<REPO>/.agents/`.
- R2: argv do build é SEMPRE transcrito do script REAL do dono; versão da tool DERIVADA do script, nunca literal; sem script do dono → lacuna com owner/quando.
- R3: adapter da linguagem é declarado no W0.5 (extensões, denominador, parser NATIVO sim/não, métricas); W7 usa parser NATIVO quando existir, feeder custom SÓ quando não existir.
- R4: rotas LEGADA vs VIVA com `diff -rq` quando ambas existirem; a mais nova é a verdade; a outra vira ponte no HANDOFF.
- R5: encoding byte-a-byte ANTES de qualquer edição; terminação de linha CRLF global = achado forte (edição LF vira diff de arquivo inteiro).
- R6: 3rd-party em 2 colunas COM licença ("entra no artefato" vs "presente no repo/lockfile"); DEP-IA varrido por dependência E na raiz; achado vira PONTEIRO, nunca cópia.
- R7: segredos NUNCA ecoados — só metadado sanitizado (arquivo:linha, tipo).
- R8: W6 exige exit 0 REAL medido SEM pipe + gate textual do dono + receipt JSON; ferramenta ausente = vermelho DECLARADO com owner do ambiente certo (ex.: swift no macOS), nunca falso verde.
- R9: repos tier leve (denominador <=10): W7 reduzido a inventário+grafo, W8 com plano B declarado (CC manual ou pódio vazio justificado).
- R10: W9/W10 — garimpeiro ANTES de gravar; memórias locais SÓ via `dex-memoria v2 remember` scope=project (tags nested lowercase; payload em arquivo, nunca heredoc); validação em lote `consciencia-memorias`; resíduo → LIXEIRA com MANIFEST.
- R11: lentes de senso crítico ($chato, $burrinha, $critico-cetico, $entrevista-me, $questionador, $interrogador-documental) vivas durante TODO o bloco em modo fiscalização; dúvida se resolve INTERROGANDO fonte (código/doc/mentor), nunca adivinhando; créditos públicos aos cooperadores substanciais no fechamento.
- R12: lapidação de invariante muda na skill nuclear `arqueologia-warmup-base` e replica nos dialetos (nunca o contrário); dialeto muda só quando a LINGUAGEM muda.
- R13: inventário W1 por CONSTRUÇÃO ÚNICA (`find -print0` + dedup); `rg --files` no Windows quebra loops bash (backslash).
- R14: tier decidido no W0 por contagem do denominador; pedido do dono pode forçar etapas completas no leve (registrar no Trilho/receipt).
- R15: executar Meta-análise questionadora do WORKFLOW antes de fechar e entre SPTs; consulta real ao oráculo/corpus, impacto transitivo, correção/reteste e registro com responsável/quando. Incerteza não vira proibição inventada.

## Limites

- Corrigir os achados do código é DECISÃO do dono (fora do workflow; recomendações no laudo).
- Projeto com dialeto dedicado (Delphi/PHP/Node) → dialetos irmãos; este template é o núcleo genérico e o alvo de lapidação.
- Sem toolchain da linguagem na máquina: rota vermelha documentada com owner/quando — o gate trava a CONFIANÇA na doc, não a arqueologia.
