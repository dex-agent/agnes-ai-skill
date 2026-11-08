---
name: "agnes-ai-skill playbook"
description: "Regras de decisao e procedimentos deste projeto - projecao gerada das fontes citadas. Nao editar a mao."
type: playbook
generated_by: "tools/playbook/generate-playbook.py"
authority: derived_projection
sources_revision: "sha256:d8a747564c8010afc2213545b10f25ed92609342329f2154188c4ea28eafe739"
sent_revision: "sha256:e33a5664148ac22a51be6a59a6ae1c8dcd628a87c983049d7f53903a16bcf1fc"
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
- Fonte: `AGENTS.md#L78-L91`
- Selo: `pb-0e403a86`

## Runbook <-> Playbook (procedimentos)

- [2026-11-08] Edicao com LF puro neste repo vira diff de arquivo inteiro (repo 100% CRLF, ate .sh e .swift) - Faca: edicao preserva CRLF (ou `git config core.autocrlf input` por janela); tabela Enc completa no AGENTS.md §Conhecimento e memoria V2 `tabela-... -> `.agents/napkin.md#L16 (local)`
- [2026-11-08] Provar build nao existe binario: e o harness (rota `W6-HARNESS-RECEITA` no GATILHOS-VIVOS) - Faca: `bash .agents/scripts/w6-build-harness.sh` + leia o receipt JSON; swift fica carimbado vermelho ate amb macOS (pendencia `SWIFT-BUILD-AMB-M... -> `.agents/napkin.md#L18 (local)`

## Plano de execucao vigente

-> `.agents/PLAN-TASKS/ACTIVE.md (local)` - nao viaja no clone.

## Fontes e revisao

| caminho | sha256 | Enviado? |
| --- | --- | --- |
| `AGENTS.md` | `d572c1a15864e2f58d1c5dffca81fb7569f0f78630c2f6dd1366005813d23cbb` | sim |
| `.agents/napkin.md` | `555ece9839e7f5bc86027caaf57bcff7d2865a966110a887c965680c5fbe0885` | nao |
| `.agents/PLAN-TASKS/ACTIVE.md` | `23d915fe3b00a9c68137f183793c324c50a147fca99002c308c531aff307ad56` | nao |

## Superficie enviada vs local

- O clone entrega: raiz commitada (fontes enviadas, PLAYBOOK.md, PLAYBOOK.index.json, tools/).
- Nao viajam: `.agents/` inteiro (napkin, trilhos, auditorias) - itens marcados (local).
- Como reagir: regra completa esta na fonte enviada; procedimento (local) pede data e localizador ao dono.

## Secoes nao decodificadas

- Bootstrap (toda janela nova, nesta ordem) -> `AGENTS.md#L5` (sem token de localizador)
- Indexação (doutrina da casa) -> `AGENTS.md#L23` (sem token de localizador)
- Abertura e fechamento de bloco -> `AGENTS.md#L48` (sem token de localizador)
- Envio a terceiros -> `AGENTS.md#L57` (sem token de localizador)
