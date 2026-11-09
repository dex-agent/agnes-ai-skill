# CHANGELOG

Fonte das versões: `SKILL.md` §Version History (projeção canônica deste repo).
Regra da casa: quem edita fonte regenera; nada de entrada inventada.

## [1.3.0] — Skill Agnes AI

- Linha de modelos alinhada ao catálogo oficial AgnesAI-Labs: família 2.5 como padrão
  (texto `agnes-2.5-flash`; imagem `agnes-image-2.5-flash`; vídeo `agnes-video-2.5`
  e `agnes-video-2.5-flash`).
- Série 3.0 documentada conforme docs oficiais (`3.0-flash` disponível; `3.0-pro` em
  preparação); modelos 2.0 marcados como legacy (catálogo oficial).
- Polling de vídeo: `GET /agnesapi?video_id=<ID>&model_name=<modelo>` (`model_name`
  obrigatório); `taskId` legado permanece compatível.
- img2img da imagem 2.5 via `extra_body` (sem `tags img2img`).
- Nota CLI: caret `^0.1.0` instala o 0.1.6 (publicado 2026-11-09); upload interno de
  mídia (fallback Litterbox/tmpfiles/Uguu/x0.at); `scripts/agnes-media-url.sh` vira
  fallback documentado.
- Fonte de verdade atualizada: hub de docs em `wiki.agnes-ai.com` + índice `llms.txt`
  + catálogo do fornecedor `AgnesAI-Labs/skills`.

## [1.2.2] — Skill Agnes AI

- Adicionado README chinês linkado e orientação de quick-start em chinês para respostas de agentes.

## [1.2.1] — Skill Agnes AI

- `npx -y agnes-ai-cli@^0.1.0` virou o caminho padrão de execução em ambientes novos; `agnes` global permanece caminho rápido opcional.

## [1.2.0] — Skill Agnes AI

- Mudança para execução CLI-first; remoção da orientação curl bruto; `--help` de descoberta virou parte do fluxo esperado.

## [1.1.2] — Skill Agnes AI

- Orientação de CLI em duas pistas: agente prefere a camada de execução separada quando disponível e mantém `curl` bruto como fallback.

## [1.1.0] — Skill Agnes AI

- Expansão da cobertura de docs oficiais para parâmetros, cenários, estrutura de prompt, campos de resposta e estados de tarefa de Image 2.0, Image 2.1 e Video 2.0.

## [1.0.0] — Skill Agnes AI

- Primeira release pública: setup da plataforma Agnes, auth persistente, e fluxos de texto, imagem e vídeo.

## Casa Dex (infraestrutura local, não viaja no skill)

- [2026-11-08] Base `dex-bootstrap` instalada (AGENTS.md, `.agents/`, PLAYBOOK.md + tools/playbook). Caminho local da máquina; o skill público não é afetado.
