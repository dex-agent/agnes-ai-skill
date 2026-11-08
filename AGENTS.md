# Agnes AI Skill

Arqueologia W0-W10 do skill publico agnes-ai-skill (skill CLI-first de Agnes AI: texto/imagem/video) — projeto da casa Dex. Base gerada pelo `dex-bootstrap` em 2026-11-08.

## Bootstrap (toda janela nova, nesta ordem)

1. Leia o AGENTS global: `$env:USERPROFILE\.agents\AGENTS.md` (PowerShell) /
   `$USERPROFILE/.agents/AGENTS.md` (Git Bash); em trabalho não trivial, leia
   também `PRINCIPLES.md` e o `operational-contract.json` quando um princípio
   precisar virar gate.
2. Leia este `AGENTS.md` inteiro.
3. Leia o estado vivo, nesta ordem: `.agents\ACTIVE.md` → `.agents\HANDOFF.md`
   → `.agents\PLAN-TASKS\ACTIVE.md` + `.agents\PLAN-TASKS\INDEX.md` →
   `.agents\PENDENTES.md` → `.agents\napkin.md` (runbook tático de TROPEÇOS:
   gotchas, comandos confiáveis e "Faça em vez disso" — leia SEMPRE antes de
   operar) → `.agents\GATILHOS-VIVOS.md` (hub de gatilhos quentes de reuso).
4. Gatilhos L1: `.agents\lembranca.md` — abra L2/L3 somente por gatilho
   material (contrato `dex-memoria`).
5. Se existir `PLAYBOOK.md` na raiz (projeção externa das regras de decisão,
   instalada pelo `dex-playbook-entrada`), leia-o como parte do bootstrap:
   é a superfície do destinatário externo e as regras valem para o envio.

## Indexação (doutrina da casa)

- A raiz mantém `INDEX.md` (mapa das seções do repo); todo diretório com
  conteúdo curado (docs, fontes, auditorias) mantém o próprio `INDEX.md`.
  Quem cria conteúdo atualiza o índice do diretório na mesma sessão —
  descoberta barata por listagem, sem caçar arquivo por arquivo.

## Autoridade e fronteiras

- A fundação da família Dex vive em `C:\CodexProjetos\dex\docs\dex-foundation`
  (instalação desta máquina): ler por ponteiro, nunca copiar para o projeto.
- `ACTIVE.md` e `HANDOFF.md` vencem memória histórica para o próximo passo.
- Trilho/SPT é o único artefato canônico de execução:
  `.agents\PLAN-TASKS\AAAA-MM-DD-<slug>.md` (owner `sprinter`; manter
  `INDEX.md` e `ACTIVE.md` atualizados; NUNCA criar spec.md, plan.md ou
  tasks.md soltos).
- Pendências moram no ledger append-only `.agents\PENDENTES.md`
  (schema `dex.pendencias.v2`; gatilho `PENDENTES-LEDGER`).
- Nada se apaga sem garimpo antes: descarte vai para `.agents\LIXEIRA\` com
  `MANIFEST.md`; nunca copiar segredos, `.env`, tokens, cookies ou payloads
  privados.
- Este projeto é base documental local: não é memória interna do modelo, não
  garante autoload/sync — a linha de chegada é o disco (estado vivo +
  evidência real).

## Abertura e fechamento de bloco

Abertura: leia o estado vivo, o HANDOFF e os gatilhos L1 antes de concluir
qualquer coisa sobre o histórico. Fechamento de bloco material: consolide
somente decisões, memórias fortes e pendências úteis — com fonte, estado,
owner, `quando` e links verificáveis — via `dex-memoria` (L1→L2/L3),
`napkin-projeto` (gotcha tático) e Trilho. Não transcreva a conversa. Nunca
afirme que algo foi salvo sem evidência no disco.

## Envio a terceiros

`PLAYBOOK.md` + `PLAYBOOK.index.json` (raiz) já nascem instalados pelo
bootstrap via `$dex-playbook-entrada` (ferramentas em `tools\playbook\`, hook
anti-drift). Regras: a projeção é GERADA — nunca editada à mão; regen após
editar as fontes (`python -B tools\playbook\generate-playbook.py --repo . --write`);
`.agents\` não viaja no envio — a projeção é a superfície do destinatário.

## Painel de Ferramentas

(Seção padrão da casa — popule no onboarding; molde completo no AGENTS global.)

1. Mentor documental do tema: — (nenhuma skill `mentor-documental-agnes*` no registry; fonte canônica do tema = docs oficiais em `https://agnes-ai.com/doc`).
2. Dependências com IA embarcada (DEP-IA): NENHUMA — varredura W4b 2026-11-08 (`rg --files --hidden --no-ignore .`): sem `node_modules/`/`vendor/`/`libs/`/`modules/`; único achado = o próprio repo (SKILL.md/AGENTS.md), zero dependência vendorizada com IA embarcada.
3. Skills da casa aplicáveis: `dex-playbook-entrada` (envio), `check-schemas`, `governancia-skills` (admissão), `consciencia-memorias` (validação V2). Finder: `python -B "$USERPROFILE/.agents/skills/governancia-skills/scripts/find-registry-skills.py" --tag <tag>`.
4. Memórias quentes: `.agents/GATILHOS-VIVOS.md` — `CRLF-REPO-100-POR-CENTO`, `SWIFT-BUILD-AMB-MACOS`, `W6-HARNESS-RECEITA`; L1 em `.agents/lembranca.md` (6 memórias V2 project).
5. Demos/oficinas locais: `examples/apps/*.html` (3 demo self-contained do platform) + `assets/` (previews de imagem/vídeo) — são SUSTENTAÇÃO do skill, não oficina de ferramenta.
6. Ferramentas da máquina: inventário central do ecossistema em
   `C:\CodexProjetos\dex\docs\operacional\ferramentas-ecossistema.md`
   (instalação e verificação por item — máquina nova começa por lá).

## Conhecimento (arqueologia W0-W10 de 2026-11-08)

- **Identidade**: skill pública `jomeswang/agnes-ai-skill` (repo local: `dex-agent/agnes-ai-skill`), CLI-first p/ Agnes AI. Artefato canônico = `SKILL.md` (539 linhas, v1.2.2); docs oficiais Agnes são a fonte de verdade de comportamento.
- **Build EXATO do dono** (W6, exit 0 medido SEM pipe em 2026-11-08):
  `bash .agents/scripts/w6-build-harness.sh` — 5 checks verdes (bash -n, URL passthrough, --help, playbook check, yaml) + 1 vermelho DECLARADO (`swift` = 127, owner `SWIFT-BUILD-AMB-MACOS`).
  Status: **VERDE** (resalva swift declarada em `.agents/receipts/w6-build-proof.json`).
- **Tabela Enc** (byte-a-byte, 2026-11-08; lapidada 2× em 2026-11-08 via `$dex-ignore` + revisão socrática): working tree 100% **CRLF**, zero BOM. Códigos-fonte (`SKILL.md`, `scripts/*.sh`, `*.swift`, `examples/*.html`, `agents/openai.yaml`, `.gitattributes`) = **ASCII puro** (0 bytes ≥ 0x80). UTF-8 válido sem BOM apenas em `README.md` (30 B), `README.zh-CN.md` (1206 B) e `docs/.../2026-06-02-agnes-cli-design-zh.md` (3111 B) — CJK. **Perfil exato de linha**: a LOJA git = **LF** (prova autoritativa: `git cat-file blob <ref>:<arq>` → 0 CR; `git ls-files --eol` → `i/lf w/crlf`); `git show rev:path` **mente** — aplica o filtro smudge local (`core.autocrlf=true`) e mostra CRLF; a working tree é CRLF apenas pelo `core.autocrlf=true` do gitconfig do sistema no checkout. `.gitattributes` NÃO pin `text/eol` → modo ambíguo: um working tree CRLF em máquina SEM clean-filter colapsa para CRLF no add e **contamina a loja para CRLF** (dif-inteiro para todos). Risco atual: ZERO neste working tree (clean); modo ambíguo CONCRETIZADO em 2026-11-08 pelo GO do dono: pin `* text=auto` ativo no `.gitattributes` (commit d15462b) + `.zcodeignore` criado (`assets/`, `.agents/`) — gatilhos `GITATTR-TEXT-AUTO-GO` e `ZCODEIGNORE-DO-OWNER` consumidos.
- **Grafo interno**: solto (zero import cruzado local). Fechamento: `SKILL.md → npm agnes-ai-cli (externo, MIT) → apihub.agnes-ai.com/v1`; `scripts/agnes-media-url.sh → litterbox.catbox.moe (upload bridge)`. Ciclos: ausentes.
- **Segredos**: zero valor de segredo no repo; padrão único = `AGNES_API_KEY` (env var, nunca commitada — frontmatter `primaryEnv`).
- **Pódio (plano B declarado)**: tier leve (denominador < 10 editáveis) → sem ferramenta oficial de métricas; CC manual: `writeFirstFrame` (swift, CC~4, 75 linhas) e `agnes-media-url.sh` (CC~5, 41 linhas). God Class/Long Method: **ausentes** (repo é documento + scripts auxiliares).
- **W4b DEP-IA**: varrido — nenhum.


<!-- playbook-pointer:start -->
## Playbook (entrada externa)

Este repo publica `PLAYBOOK.md` e `PLAYBOOK.index.json` na raiz: projecao GERADA
das regras de decisao (fontes declaradas em `tools/playbook/playbook-sources.txt`).
Nao editar a mao; a decisao completa mora na fonte citada.
Regenerar apos editar fonte:
`python -B tools/playbook/generate-playbook.py --repo . --write`.
Verificar frescor: mesmo comando com `--check` (exit 0 limpo, exit 2 drift).
Ativar trava de commit: `git config core.hooksPath tools/playbook/hooks`.
<!-- playbook-pointer:end -->
