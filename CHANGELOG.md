# CHANGELOG

Fonte das versões: `SKILL.md` §Version History (projeção canônica deste repo).
Regra da casa: quem edita fonte regenera; nada de entrada inventada.

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
