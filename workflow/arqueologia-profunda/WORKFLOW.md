---
schema: dex.workflow.v1
slug: arqueologia-profunda
version: 1.1.0
status: ativo
owner: agnes-ai-skill (instância local; dono = repo) — template global arqueologia-profunda@1.1.0
created: 2026-11-08
updated: 2026-11-08
origem: template global arqueologia-profunda@1.1.0 (instanciação local no repo agnes-ai-skill)
---

# Arqueologia Profunda Genérica (W-1 a W10, template de reuso multi-linguagem)

Documentos irmãos: [RULES.md](RULES.md) · [SCHEMA/SCHEMA.md](SCHEMA/SCHEMA.md) · [USAGE.md](USAGE.md) · [CHANGELOG.md](CHANGELOG.md) · [CAPACITY.md](CAPACITY.md)

## Promessa

Arqueologia completa e profunda de QUALQUER projeto legado/novo cuja linguagem não
tenha dialeto dedicado (ou como núcleo de lapidação dos dialetos): W-1 a W10 com
gates por etapa, tier por denominador da stack, read-only no código-fonte até a
prova de build/teste verde com receipt JSON (ou rota vermelha com owner/quando),
memórias locais V2 via dex-memoria validadas em lote e plaquinhas completas —
entregando inventário + tabela Enc, grafo, receipt, gate exit 0 sem pipe, pódio
e contagem de memoráveis/tropeços.

## Quando usar / quando NÃO usar

- Use quando: reconhecimento de qualquer repo de linguagem SEM dialeto próprio
  (PHP/Node têm dialetos; Delphi tem dialeto; skill/documento/Python/Go/Ruby/
  misto → este template).
- NÃO use quando: projeto Delphi → `arqueologia-delphi-profunda` (dialeto
  irmão); gotcha tático avulso → `napkin-projeto`; plano ANTES da execução →
  Trilho/SPT (`sprinter`); incidente caro → `dex-forjar-contexto-operacional-
  aprendizado-doloroso`; generalização cross-repo → promoção a skill via
  `governancia-skills`.

## Pré-requisitos

- Skill nuclear: `arqueologia-warmup-base` ($env:USERPROFILE\.agents\skills\
  arqueologia-warmup-base\SKILL.md) — fonte do contrato de cada W; dialetos
  irmã: `arqueologia-php-warmup`, `arqueologia-nodejs-warmup`,
  `arqueologia-delphi-warmup` (este template é o núcleo genérico; lapidação
  de invariante muda na base e replica nos dialetos).
- Skills donas por etapa: `dex-bootstrap` (W-1), `garimpeiro` + `dex-memoria`
  + `consciencia-memorias` + `estacionamento` (W9/W10), `dex-ppirtv-validate-spt`
  (quando houver Trilho), `guarda-plaquinhas` (fiscal), `check-schemas`
  (gates de schema).
- Ferramentas da máquina: `es.exe` ($env:USERPROFILE\.local\bin\es.exe —
  busca por NOME é a primeira batida), `rg`, Git Bash (file/od/iconv/diff),
  `find-registry-skills.py` (governancia-skills). Parser NATIVO Tree-sitter
  quando a linguagem tiver (ex.: php/js/ts/py) — feeder custom SÓ quando o
  parser não existir.
- Lentes de senso crítico ao vivo: `$chato` (premissas `E SE?`), `$burrinha`
  (estranha o óbvio), `$critico-cetico` (fronteira de evidência),
  `$entrevista-me` + `$questionador` (Muda/Se A/Se B), `$interrogador-
  documental` (dúvida não se adivinha: INTERROGA a fonte).
- Ambiente: `<REPO>` = raiz do projeto-alvo; escritas de evidência SÓ sob
  `<REPO>/.agents/`.

## Passos

Antes de fechar/veredictar ou passar ao próximo SPT, executar a seção
Meta-análise questionadora abaixo; ela integra a sequência obrigatória.

1. **Adapter da linguagem (W0.5 — antes de tudo)**: declare explicitamente o
   dialeto deste repo: extensões de fonte (`<EXT>`), denominador de tier
   (contagem de unidades editáveis), parser NATIVO disponível?
   (Tree-sitter cobre php/js/ts/py — `crg build` direto SEM feeder; sem
   parser → feeder custom ou plano B declarado), encoding esperado da stack,
   ferramenta de métricas oficial + cobertura. Registro no Trilho/receipt.
   ✅ Verificação: adapter declarado com 4 campos preenchidos; divergência
   (ferramenta ausente) REGISTRADA, não inventada.

2. **W-1 — Padrão + inventário de capacidade**: Se `<REPO>` não tiver
   AGENTS.md/`.agents/`, instale o esqueleto CORE via `dex-bootstrap`
   (nunca cole manual). Inventário de capacidade: `find-registry-skills.py
   --tag <linguagem>` (sem `--limit`), mentores do tema, CLIs da toolchain
   via `es.exe`, memórias do tema (Finder + rg em
   `$env:USERPROFILE\.agents\memories`). Nenhuma cola própria antes de
   esgotar este inventário.
   ✅ Verificação: padrão instalado + inventário declarado ANTES do W1.

3. **W0 — Identidade, rotas, tier**: dono, objetivo, rotas LEGADA vs VIVA
   (ambas no disco → `diff -rq`; a mais nova é a verdade, a outra vira ponte
   no HANDOFF). Tier pelo denominador do passo 1: `<=10` = LEVE (W7 reduzido
   a inventário+grafo, W8 opcional, gate com `--min-functions 1 --max-
   functions <N real>` documentado); `>10` = PADRÃO completo. Pedido do dono
   pode forçar completo no leve (registrar).
   ✅ Verificação: rotas+diff, tier com contagem, procedência de cada doc.

4. **W1 — Superfície + argv REAL**: inventário de TODOS os fontes com `wc -l`
   por CONSTRUÇÃO ÚNICA (`find -print0` + dedup; `rg --files` em Windows
   emite backslash que quebra loops bash; duplo caminhar duplica contagem).
   Fósseis (`__history`, backups, dist, vendor). Script de build REAL do dono
   transcrito (argv exato) OU lacuna com owner/quando. Repo SEM build
   (skill/documento): declare que o build do dono é o gate textual/hook
   disponível (ex.: `--check` do hook pre-commit, sintaxe de script,
   dry-run sem rede) e transcrita a argv.
   ✅ Verificação: inventário com linhas + argv transcrito ou lacuna.

5. **W2 — Encoding byte-a-byte**: para CADA fonte editável no escopo:
   `file`; `head -c 3 | od -An -tx1` (BOM); contagem bytes >=0x80 por
   `LC_ALL=C grep -c -P '[^\x00-\x7F]'`; validação `iconv -f UTF-8 -t UTF-8`.
   Classifique (ASCII/UTF-8/UTF-8 BOM/latin/CP1252 conforme o adapter do
   passo 1) E a terminação de linha em 3 camadas: (a) disco: `file` +
   `head -c 3 | od -An -tx1`; (b) LOJA git: `git cat-file blob HEAD:<arq>`
   (byte cru — `git show rev:path` MENTE: aplica o filtro smudge local no
   stdout) + `git ls-files --eol` (índice); (c) máquina: `git config
   core.autocrlf` (+ `--show-origin`: sistema? repo?). Perfil completo no
   R5; contaminação real só via modo ambíguo (R5).
   ✅ Verificação: tabela Enc completa por arquivo; encoding suspeito → gate
   de edição segura ANTES de qualquer escrita.

6. **W3 — Grafo de dependências interno**: quem importa/inclui/usca quem
   (adapter da linguagem: uses Delphi, require/import JS, include PHP...),
   interface vs implementation, ciclos, hubs de fan-in; módulos externos
   confirmados no disco. Se houver artefato de build listando linkados
   (.map, lockfile), cruzar o fechamento real. Repos soltos (documento +
   assets): declare "grafo solto, zero import cruzado" COM prova
   (varredura que retorna vazio).
   ✅ Verificação: grafo com números + artefatos salvos.

7. **W4/W4b/W5 — Escondido, 3rd-party, segredos**: ofuscação (padrões do
   corpus E novos; URLs por FRAGMENTO, nunca domínio completo; código morto
   comentado). 3rd-party em 2 colunas COM licença: "entra no artefato final
   (via evidência de build)" vs "presente no repo/lockfile". W4b DEP-IA por
   dependência vendorizada E na raiz: `rg --files --hidden --no-ignore <dep>
   | rg -i "(AGENTS|CLAUDE)\.md$|\.agents/|SKILL\.md$"` → achado vira bloco
   DEP-IA no Painel (nunca copiar skill para superfície global). W5: dados/
   configs/segredos — origem-destino-gatilho; segredos NUNCA ecoados, só
   metadado sanitizado (arquivo:linha, tipo).
   ✅ Verificação: dicionário iniciado (arquivo:linha); 3rd-party 2 colunas
   com licença; DEP-IA "varrido — achado|nenhum" por dependência; segredos
   sanitizados ou ausência.

8. **W6 — Prova de build/teste (o como definitivo)**: harness em
   `<REPO>/.agents/scripts/` transcrevendo o argv REAL do dono (rota VIVA;
   versão da tool DERIVADA do script, nunca literal), saída no próprio
   projeto, guarda contra sobrescrever artefato de produção. Exigir exit 0
   + evidência de saída + receipt JSON em `<REPO>/.agents/receipts/`. O gate
   do dono PODE ser TEXTUAL (ex.: "terminar com 0 FAIL", hook `--check`
   drift) — o harness lê o resumo declarado, não só o exit code.
   **ROTA VERMELHO**: cada erro vira ACHADO (erro→causa→arquivo:linha);
   W7-W9 prosseguem carimbados "build: NAO PROVADO"; pendência no
   ESTACIONAMENTO/PENDENTES com owner/quando. Ferramenta ausente no host
   (ex.: swiftc no Windows para .swift macOS-only) = vermelho DECLARADO com
   owner do ambiente certo, não falso verde.
   ✅ Verificação: exit 0 REAL medido SEM pipe + gate textual limpo + receipt
   JSON OU rota vermelha completa.

9. **W7 — Grafo canônico (tier leve: inventário+grafo)**: parser NATIVO da
   linguagem quando existir (Tree-sitter: php/js/ts/py — `crg build` direto,
   SEM feeder); feeder custom SÓ quando o parser não existir (exemplo
   Object Pascal → `code-review-graph-delphi-feeder`). Depois postprocess →
   `graphify update .` (estrutural; `.graphifyignore` antes) → `grafo_gate.py`
   com faixa ajustada ao N real. Repos tier leve: W7 reduzido a
   inventário+grafo do passo 6 (declaração registrada no receipt).
   ✅ Verificação: gate exit 0 real medido sem pipe OU plano B registrado.

10. **W8 — Métricas/toxicidade + pódio**: ferramenta oficial da stack SE
    instalada E com COBERTURA confirmada (relatório parcial bem-formado NÃO é
    cobertura — confira quantos módulos entraram); senão PLANO B declarado
    no receipt (CC manual: contagem de branches por rotina; Long Method por
    linhas; God Class por fan-in). Pódio God Class/Long Method/maior CC com
    arquivo:linha; repos sem código de classe: pódio vazio DECLARADO com
    justificativa (documento + scripts auxiliares ≠ sistema OO).
    ✅ Verificação: pódio com arquivo:linha + plano ou divergência declarada.

11. **W9 — Camada de conhecimento + memórias V2**: Fase 1 raiz (AGENTS.md
    com build EXATO + status verde/vermelho + tabela Enc REAL; INDEX;
    DEPENDENCIES com grafo ASCII; NAMES se ofuscação; napkin canônico).
    Fase 2 `.agents/` (ACTIVE, HANDOFF, GATILHOS-VIVOS com molde 5 campos
    Por que/Como/Quando/Onde/E se??, tropecos, ESTACIONAMENTO, PENDENTES,
    PLAN-TASKS). **Fase 2b MEMÓRIA LOCAL V2 OBRIGATÓRIA**: convoque
    `garimpeiro` ANTES de gravar (típico 6-10 memórias: build, rotas,
    encoding, segredo sanitizado, métricas, estrutura/peso, hotspot, dados);
    gravação SÓ via `dex-memoria v2 remember` scope=project (tags nested
    lowercase `#tema/assunto`; payload por arquivo/JSON, nunca heredoc com
    backslash duplo) — hand-write é proibido; resíduo V1 → LIXEIRA com
    MANIFEST.
    ✅ Verificação: checklist fechado; `rg` confirma build/encoding/números;
    formato V2 sem arquivo colapsado; carimbo vermelho quando aplicável.

12. **W10 — Integração + fechamento**: todas as plaquinhas existem (crie na
    MESMA operação do achado); localizador cita fonte viva. Validar CADA par
    L1↔L2/L3 em LOTE (`consciencia-memorias/scripts/validate-memory-batch.py
    --root <REPO>/.agents` → `BATCH: N/N validos`). Achados cross-project →
    scope global. Delta do Painel de Ferramentas do AGENTS.md. Fechamento:
    contagem de memoráveis/tropeços + gatilhos L1 quentes usados + créditos
    públicos aos cooperadores substanciais + pergunta de edição (silêncio =
    mantém).
    ✅ Verificação: checklist W10 completo; validação em lote verde; Painel
    com delta; contagens + créditos registrados.

## Meta-análise questionadora

- Quando: antes de fechar/veredictar e ao concluir cada SPT, inclusive o último; repetir se ajuste material mudar a premissa revisada.
- Perguntas: ESTAMOS SEGUINDO NOSSOS PRINCÍPIOS e o planejado? Para quê, por quê, onde, quando, quanto e quem responde? Já foi pensado/planejado, do que se alimenta, qual origem/destino/gatilho, onde nasce/configura, qual contrato/owner, precisa lembrar? E SE falhar, der certo ou afetar outra fase? Corrigimos causa ou sintoma? Separar fatos, suposições e lacunas nas fases aplicáveis P→P→I→R→T→V; preservar RED e interrogar fontes, sem excesso de confiança.
- Oráculo: definir na criação ou selecionar no fechamento pelo domínio dos achados; executar a skill e reabrir corpus com obra/edição/seção/linha e identidade da fonte. Separar confirmado, inferido, divergente e não localizado; escolha de nome não prova consulta.
- Impacto: revisar resultado atual e todos os próximos trabalhos afetados, inclusive dependências indiretas; registrar manter, ajustar, lapidar, reordenar ou substituir. No último SPT, declarar próximo=N/A e avaliar efeitos residuais.
- Retorno: achado material volta à fase causadora; corrigir e retestar os afetados. SPT vinculado exige adendo/sucessor pelo owner e revalidação; mudança material de premissa exige nova consulta focal.
- Registro: anexar ao Trilho/relatório da execução revisão/hash, perguntas e respostas, oráculo/motivo, fonte reaberta, parecer, decisão justificada, ação, responsável, quando e prova; sem mudança também exige justificativa.
- Avanço: liberar fechamento/próximo dependente somente com evidências atuais e achados materiais resolvidos. Corpus indisponível pede recuperação e revisão pendente, nunca selo inventado; incerteza não vira proibição. Trabalho independente autorizado continua, decisão fora do escopo vai ao dono. ✅ Verificação: registro reabrível e impacto no plano reconciliado antes do verdict.

## Gotchas

- `$?`/exit após pipe mente (PIPE-EXIT-FALSO) → Faça em vez disso: redirecionar saída para arquivo e medir exit sem pipe.
- `rg --files` em Windows emite backslash que quebra loops bash e duplo caminhar raiz+dirs duplica contagem → Faça em vez disso: `find -print0` com dedup por path relativo, construção única.
- Ferramenta de build ausente no host (swiftc no Windows, dcc32 sem Studio) → Faça em vez disso: vermelho DECLARADO com owner do ambiente certo + pendência com quando; nunca falso verde, nunca bloquear a arqueologia.
- Hook pre-commit regenerando artefato (ex.: playbook `--check` drift) derruba o commit → Faça em vez disso: rodar o `--write` do gerador, re-stage e commitar na mesma transação (a projeção é da casa: quem edita fonte regenera).
- Hand-write de lembranca/memoria produz shape V1 → Faça em vez disso: `dex-memoria v2 remember` scope=project por achado; lote via `validate-memory-batch.py`.
- `v2 remember` com tag single-level ou payload heredoc com backslash duplo → Faça em vez disso: tags nested lowercase + payload em arquivo/`json.dump`; tags de exemplo no corpo L2 entram no conjunto real e divergem do L1.
- Editar `AGENTS.md` global sem rodar `AGENTS-auto-copy.cmd` → espelhos driftam em silêncio → Faça em vez disso: `cd ~/.agents && cmd //c AGENTS-auto-copy.cmd` e conferir `GATE: OK`.
- Script de cola que a skill dona já cobre → Faça em vez disso: varrer registry (`find-registry-skills.py`) ANTES; gap real → ESTACIONAMENTO com owner/quando.
- Repo CRLF global editado com LF puro → diff de arquivo inteiro → Faça em vez disso: tabela Enc do W2 + edição preservando CRLF.
- `git show rev:path` lido como byte do blob → conclusão "repo commita CRLF" FALSA (o smudge do `autocrlf` local expande o stdout) → Faça em vez disso: `git cat-file blob` (byte cru) + `git ls-files --eol` (índice); o que a loja commita é a camada (b), não o working tree.
- Tabela Enc declarada sem as 3 camadas (disco/loja/máquina) → perfil de risco invertido (o repo de skill agnes pagou 2× em 2026-11-08) → Faça em vez disso: R5 (a+b+c) ANTES de declarar a Tabela Enc.
