# Index Agnes AI Skill

Mapa do repo (doutrina da casa: todo diretorio com conteudo curado mantem INDEX.md).
Criado pelo dex-bootstrap; populado na arqueologia W0-W10 (2026-11-08).

- `AGENTS.md` — bootstrap, autoridade e fronteiras, abertura/fechamento, envio + §Conhecimento (W0-W10).
- `README.md` — visao geral (EN, UTF-8, 30 B nao-ASCII).
- `README.zh-CN.md` — quick start em chines (UTF-8, 1206 B nao-ASCII).
- `SKILL.md` — artefato canonico do skill (539 linhas, v1.2.2, CLI-first; fonte de verdade de comportamento).
- `PLAYBOOK.md` + `PLAYBOOK.index.json` — projecao externa das regras (GERADA; regen via `tools/playbook/`).
- `LICENSE` — MIT.
- `agents/openai.yaml` — frontmatter de agent (display_name/default_prompt).
- `.agents/` — estado vivo e memoria do projeto (nao viaja em envio externo): ACTIVE, HANDOFF, GATILHOS-VIVOS, napkin, L1 lembranca + `memorias/` (6 V2), `receipts/w6-build-proof.json`, `scripts/w6-build-harness.sh`, LIXEIRA.

## Sub-indices

- [scripts/INDEX.md](scripts/INDEX.md) — agnes-media-url.sh (bash) + extract_first_frames.swift (macOS-only).
- [docs/superpowers/specs/INDEX.md](docs/superpowers/specs/INDEX.md) — spec do design do CLI Agnes (EN + ZH).
- [examples/](examples/) — 3 demos self-contained do platform (beijing-map-ui, cinematic-ai-landing, watch-experience).
- [assets/](assets/) — previews de imagem e vídeo de marketing do skill (jpg/png/mp4; sustentação, não ferramenta).

## Regra anti-lixo

`assets/` e `examples/` NAO ganham INDEX proprio (conteudo de suporte/derivado, nao curado); sao apontados acima. `tools/playbook/` e infra de ferramenta (dono: dex-playbook-entrada), nao ganha INDEX.
