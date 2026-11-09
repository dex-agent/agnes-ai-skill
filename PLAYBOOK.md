---
name: "agnes-ai-skill playbook"
description: "Regras de decisao e procedimentos deste projeto - projecao gerada das fontes citadas. Nao editar a mao."
type: playbook
generated_by: "tools/playbook/generate-playbook.py"
authority: derived_projection
sources_revision: "sha256:2ba8950fcd445d922e1093c3ec74a7488821087775a94ea4fefdbe1380c750cd"
sent_revision: "sha256:dc05ca4a8e34733455ab064f69ffdcfd1b910e252a4c3b066c3a581fa575a831"
do_not_edit: true
---
# Playbook - agnes-ai-skill

## Como usar este playbook

Projecao GERADA das regras de decisao deste repo; a decisao completa mora na fonte citada.
Executar uma regra exige ler a fonte; extratos terminam em '...' quando truncados.
Regenerar apos editar fonte: `python -B tools/playbook/generate-playbook.py --repo . --write`.
Verificar frescor: `python -B tools/playbook/generate-playbook.py --repo . --check` (exit 0 limpo, exit 2 drift).
Ativar trava de commit: `git config core.hooksPath tools/playbook/hooks`.
Destinatario do projeto: `--check-sent` valida as fontes enviadas neste clone.

## Regras de decisao (plaquinhas)

### Autoridade e fronteiras

- Localizador: `PENDENTES-LEDGER`
- Gatilho: (schema `dex.pendencias.v2`; gatilho `PENDENTES-LEDGER`).
- Extrato: - A fundação da família Dex vive em `C:\CodexProjetos\dex\docs\dex-foundation`
- Fonte: `AGENTS.md#L30-L47`
- Selo: `pb-25bcea4f`

### Painel de Ferramentas

- Localizador: `CRLF-REPO-100-POR-CENTO`
- Gatilho: 4. Memórias quentes: `.agents/GATILHOS-VIVOS.md` — `CRLF-REPO-100-POR-CENTO`, `SWIFT-BUILD-AMB-MACOS`, `W6-HARNESS-RECEITA`; L1 em `.agents...
- Extrato: (Seção padrão da casa — popule no onboarding; molde completo no AGENTS global.)
- Rotas (nomes, na ordem):
  - Mentor documental do tema: — (nenhuma skill `mentor-documen...
  - Dependências com IA embarcada (DEP-IA): NENHUMA — varredura...
  - Skills da casa aplicáveis: `dex-playbook-entrada` (envio),...
  - Memórias quentes: `.agents/GATILHOS-VIVOS.md` — `CRLF-REPO-...
- Fonte: `AGENTS.md#L65-L77`
- Selo: `pb-591c036f`

### Conhecimento (arqueologia W0-W10 de 2026-11-08)

- Localizador: `SWIFT-BUILD-AMB-MACOS`
- Gatilho: - **Tabela Enc** (byte-a-byte, 2026-11-08; lapidada 2× em 2026-11-08 via `$dex-ignore` + revisão socrática): working tree 100% **CRLF**, ze...
- Extrato: - **Identidade**: skill pública `jomeswang/agnes-ai-skill` (repo local: `dex-agent/agnes-ai-skill`), CLI-first p/ Agnes AI. Artefato canôni...
- Fonte: `AGENTS.md#L78-L90`
- Selo: `pb-611967c5`

### Pesquisas

- Localizador: `PESQUISA-AGNES-UPDATE-261109`
- Gatilho: - `.agents/PESQUISA/INDEX.md` — pesquisas documentadas com relatórios, fontes e artifacts (gatilho: `PESQUISA-AGNES-UPDATE-261109`)
- Extrato: - `.agents/PESQUISA/INDEX.md` — pesquisas documentadas com relatórios, fontes e artifacts (gatilho: `PESQUISA-AGNES-UPDATE-261109`)
- Fonte: `AGENTS.md#L91-L96`
- Selo: `pb-a8d5ed1c`

## Runbook <-> Playbook (procedimentos)

- [2026-11-08] Edicao com LF puro neste repo vira diff de arquivo inteiro (repo 100% CRLF, ate .sh e .swift) - Faca: edicao preserva CRLF (ou `git config core.autocrlf input` por janela); tabela Enc completa no AGENTS.md §Conhecimento e memoria V2 `tabela-... -> `.agents/napkin.md#L16 (local)`
- [2026-11-08] Provar build nao existe binario: e o harness (rota `W6-HARNESS-RECEITA` no GATILHOS-VIVOS) - Faca: `bash .agents/scripts/w6-build-harness.sh` + leia o receipt JSON; swift fica carimbado vermelho ate amb macOS (pendencia `SWIFT-BUILD-AMB-M... -> `.agents/napkin.md#L18 (local)`

## Plano de execucao vigente

-> `.agents/PLAN-TASKS/ACTIVE.md (local)` - nao viaja no clone.

## Fontes e revisao

| caminho | sha256 | Enviado? |
| --- | --- | --- |
| `AGENTS.md` | `2246b28f1be9fffda03e7143abf57084e977f52381b34ebf523b873f9328a927` | sim |
| `.agents/napkin.md` | `555ece9839e7f5bc86027caaf57bcff7d2865a966110a887c965680c5fbe0885` | nao |
| `.agents/PLAN-TASKS/ACTIVE.md` | `bdebc9a84e62ccfd28a6ced56aa4e404b2ad1068a15f936d3f0e94f74983639b` | nao |

## Superficie enviada vs local

- O clone entrega: raiz commitada (fontes enviadas, PLAYBOOK.md, PLAYBOOK.index.json, tools/).
- Nao viajam: `.agents/` inteiro (napkin, trilhos, auditorias) - itens marcados (local).
- Como reagir: regra completa esta na fonte enviada; procedimento (local) pede data e localizador ao dono.

## Secoes nao decodificadas

- Bootstrap (toda janela nova, nesta ordem) -> `AGENTS.md#L5` (sem token de localizador)
- Indexação (doutrina da casa) -> `AGENTS.md#L23` (sem token de localizador)
- Abertura e fechamento de bloco -> `AGENTS.md#L48` (sem token de localizador)
- Envio a terceiros -> `AGENTS.md#L57` (sem token de localizador)
