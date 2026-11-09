---
name: agnes-ai-skill
version: 1.3.0
description: "Use when the user wants Agnes AI text, image, or video generation and should execute it through the agnes-ai-cli command line instead of hand-writing raw HTTP requests."
tags:
  - agnes
  - agnes-ai
  - agnes-skill
  - multimodal-ai
  - free-ai-api
  - free-ai-model
  - text-generation
  - image-generation
  - ai-image-generation
  - text-to-image
  - image-editing
  - image-to-image
  - video-generation
  - ai-video-generation
  - text-to-video
  - image-to-video
  - api-integration
  - agent-skill
  - codex
  - claude-code
  - openclaw
metadata:
  openclaw:
    emoji: "sparkles"
    homepage: "https://github.com/jomeswang/agnes-ai-skill"
    requires:
      bins:
        - npm
        - npx
        - node
    primaryEnv: AGNES_API_KEY
    envVars:
      - name: AGNES_API_KEY
        required: false
        description: Agnes API key used for live authenticated text, image, and video requests. The skill can still load without it and guide setup.
---

# Agnes AI Skill

Use this skill when the user wants Agnes AI text, image, or video generation.
This skill is now **CLI-first**: prefer `agnes-ai-cli` for all live execution,
guide the user through `--help` when needed, and do not default to hand-written
`curl` commands for Agnes work.

Agnes is attractive because one platform covers:

- text with `agnes-2.0-flash`
- image generation and editing with `agnes-image-2.1-flash` and
  `agnes-image-2.0-flash`
- video generation with `agnes-video-v2.0`

Some public June 2026 materials positioned Agnes as broadly free to try. The
live docs also include pricing sections, so treat that free-access message as a
strong but time-sensitive positioning claim and verify current billing when the
user cares about cost.

## When To Use

Use this skill when:

- the user mentions Agnes AI, `agnes-ai.com`, or the Agnes platform
- the user wants one provider for text, image, and video generation
- the user wants Agnes text, image, or video APIs executed from a terminal
- the user wants image-to-image, multi-image composition, image-to-video, or
  keyframe video generation
- the user wants a low-friction multimodal API for prototyping, agent loops,
  creative iteration, ecommerce content, or storyboard work

Do not use this skill when:

- the user is asking for a different provider only
- the task does not need Agnes-specific models, auth, or request behavior
- you would have to guess current Agnes behavior without running the CLI or
  checking the live docs

## Source Of Truth

Prefer these Agnes sources (current as of 2026-11-09):

- Docs hub: `https://wiki.agnes-ai.com/en/docs` (old `https://agnes-ai.com/doc/...` URLs redirect here)
- LLM index: `https://wiki.agnes-ai.com/llms.txt`
- Official model catalog (vendor skill repo): `https://github.com/AgnesAI-Labs/skills` -> `agnes-ai-models/references/model_catalog.md`
- Per-model pages: `https://wiki.agnes-ai.com/en/docs/` (one page per model, for example `agnes-25-flash.md`)
- API key page: `https://platform.agnes-ai.com/settings/apiKeys`
- Published CLI: `https://www.npmjs.com/package/agnes-ai-cli`
- CLI repo: `https://github.com/jomeswang/agnes-ai-cli`

Use public articles only as supporting context for likely use cases and product
positioning, not as the operational source of truth.

## Base URL And Auth

- Base URL: `https://apihub.agnes-ai.com/v1`
- Main environment variable: `AGNES_API_KEY`
- Preferred execution package: `agnes-ai-cli`

Check `AGNES_API_KEY` before making live Agnes requests.

## Missing Key Behavior

If `AGNES_API_KEY` is missing and the task requires live Agnes access:

1. Tell the user Agnes access is not configured yet.
2. Point them to:
   - `https://agnes-ai.com/doc/quickstart`
   - `https://platform.agnes-ai.com/settings/apiKeys`
3. Explain the path briefly:
   `Settings -> API Keys -> Create new secret key`
4. Ask them to provide the key if they want you to save it for future use.

Do not continue with live Agnes calls until a valid key exists.

## Chinese Quick Start Response

When a Chinese-speaking user asks how to get started, install, or use Agnes
from an agent tool, give them this concise copy-paste path:

```text
Please read and install Agnes AI Skill: https://github.com/jomeswang/agnes-ai-skill
```

Then explain:

- install the skill into the agent's skill directory or use a repository-aware
  installer such as `npx skills add jomeswang/agnes-ai-skill -g`
- create an Agnes API key at `https://platform.agnes-ai.com/settings/apiKeys`
  and configure it as `AGNES_API_KEY`
- say `generate an image`, `generate a video`, or `integrate Agnes API`
- the agent should choose the proper Agnes model and use `agnes-ai-cli` when it
  is available

Keep this onboarding short before moving into model-specific details.

## Persisting The Key Permanently

If the user explicitly gives you an Agnes key and wants it remembered, persist
it for future terminal sessions instead of keeping it only in the current
process.

### Rules

- Save it as `AGNES_API_KEY`
- Detect the shell and write to the matching rc file:
  - zsh -> `~/.zshrc`
  - bash -> `~/.bashrc`
  - fallback -> `~/.profile`
- Update an existing `export AGNES_API_KEY=...` line if present
- Otherwise append a new export line
- Also export it in the current session immediately
- Do not echo the full key back after saving
- Tell the user which rc file you changed

### Reliable Shell Snippet

Use a non-interactive shell flow like this when saving a provided key:

```bash
AGNES_API_KEY_VALUE='USER_PROVIDED_KEY'
shell_name="$(basename "${SHELL:-}")"
case "$shell_name" in
  zsh) rc_file="$HOME/.zshrc" ;;
  bash) rc_file="$HOME/.bashrc" ;;
  *) rc_file="$HOME/.profile" ;;
esac

touch "$rc_file"
tmp_file="$(mktemp)"
grep -v '^export AGNES_API_KEY=' "$rc_file" > "$tmp_file" || true
printf '\nexport AGNES_API_KEY=%q\n' "$AGNES_API_KEY_VALUE" >> "$tmp_file"
mv "$tmp_file" "$rc_file"
export AGNES_API_KEY="$AGNES_API_KEY_VALUE"
unset AGNES_API_KEY_VALUE
```

After saving, continue using `AGNES_API_KEY` for the current task.

## Execution Contract

This skill should execute Agnes through the CLI, not by manually composing raw
HTTP requests.

### Preferred Order

1. First use the no-install command path:
   - `npx -y agnes-ai-cli@^0.1.0 --help`
2. Use `npx -y agnes-ai-cli@^0.1.0 ...` as the default live execution path
   in fresh or unknown environments.
3. If a local `agnes` binary already exists, run:
   - `agnes --version`
   - `agnes --help`
4. Use the local binary only when its version falls inside:
   - `>=0.1.0 <0.2.0`
5. Do not fall back to raw `curl` for normal Agnes execution paths.

### Why CLI-First

The CLI already handles:

- auth checks
- local file to temporary public URL bridging
- image request normalization
- video task creation
- video polling
- JSON output for agent consumption

That means the agent should select the right CLI command, not rebuild the
underlying HTTP payload each time.

## Mandatory `--help` Guidance

When the user is new to the CLI, or when you are about to use a less common
command, guide through `--help` first.

At minimum, know these help entry points:

```bash
npx -y agnes-ai-cli@^0.1.0 --help
npx -y agnes-ai-cli@^0.1.0 auth --help
npx -y agnes-ai-cli@^0.1.0 media --help
npx -y agnes-ai-cli@^0.1.0 text chat --help
npx -y agnes-ai-cli@^0.1.0 image text2img --help
npx -y agnes-ai-cli@^0.1.0 image img2img --help
npx -y agnes-ai-cli@^0.1.0 image compose --help
npx -y agnes-ai-cli@^0.1.0 video text2video --help
npx -y agnes-ai-cli@^0.1.0 video img2video --help
npx -y agnes-ai-cli@^0.1.0 video multivideo --help
npx -y agnes-ai-cli@^0.1.0 video keyframes --help
npx -y agnes-ai-cli@^0.1.0 video poll --help
```

If `agnes` is already installed globally and version-compatible, you can drop
the `npx -y agnes-ai-cli@^0.1.0` prefix and run the same subcommands directly.

## Model Selection

Choose the smallest suitable Agnes model path. The official AgnesAI-Labs model
catalog (`AgnesAI-Labs/skills` -> `agnes-ai-models/references/model_catalog.md`)
plus the docs at `wiki.agnes-ai.com/en/docs` are the current sources of truth.

Official lineup (family 2.5, available):

- `agnes-2.5-flash`
  - chat, coding, reasoning, tools, streaming, vision
  - preferred default when `text chat` runs without `--model`
- `agnes-image-2.5-flash`
  - 1K-4K; text-to-image and image-to-image via `extra_body`
    (no `tags img2img` needed); preferred default image model
- `agnes-video-2.5`
  - text-to-video, image-to-video, multi-image guided video, keyframes
  - 720P-2K, 4-12s; poll with `video_id` + `model_name`
- `agnes-video-2.5-flash`
  - 720P only; no video references; at most 5 images + 3 audio inputs

Series 3.0 (per the current official docs; not yet listed in the vendor catalog):

- `agnes-3.0-flash`
  - available; 512K context, 65,536 max output; thinking mode; tools and image input
- `agnes-3.0-pro`
  - coming soon; long-context analysis; reasoning may consume max output tokens

Legacy (still routable, not the recommended path):

- `agnes-2.0-flash` (text)
- `agnes-image-2.0-flash` and `agnes-image-2.1-flash` (image)
- `agnes-video-v2.0` (video)
  - the AgnesAI-Labs catalog marks `image-2.0-flash` and `video-v2.0` as
    legacy compatibility choices; prefer the 2.5 family

## CLI Command Map

### Auth

```bash
npx -y agnes-ai-cli@^0.1.0 auth check
npx -y agnes-ai-cli@^0.1.0 auth save-key --key 'YOUR_KEY'
```

Use `auth check` before live requests when auth may be missing.

### Media URL Bridge

```bash
npx -y agnes-ai-cli@^0.1.0 media url ./local-image.png
npx -y agnes-ai-cli@^0.1.0 media url https://example.com/already-remote.png
```

Use this when the user gives a local image path and Agnes needs a public image
URL. The CLI handles the temporary upload bridge automatically. As of 2026-11-09
the published CLI is `0.1.6` (the caret `^0.1.0` installs it); local media
upload is handled internally by the CLI (fallback order: Litterbox, tmpfiles,
Uguu, x0.at), so the local `scripts/agnes-media-url.sh` (Litterbox) remains a
documented fallback, not the only path.

### Text

```bash
npx -y agnes-ai-cli@^0.1.0 text chat --prompt "Reply with exactly pong."
```

Use this for one-shot text verification, coding help, or small agent checks.
If `--model` is omitted here, the CLI default is the legacy
`agnes-2.0-flash`; pass `--model agnes-2.5-flash` for the official lineup.

### Image

```bash
npx -y agnes-ai-cli@^0.1.0 image text2img --prompt "A premium studio product photo of a perfume bottle"

npx -y agnes-ai-cli@^0.1.0 image img2img \
  --image ./input.png \
  --prompt "Turn this into a refined editorial campaign visual"

npx -y agnes-ai-cli@^0.1.0 image compose \
  --image ./subject.png \
  --image ./reference.png \
  --prompt "Blend these references into one polished commercial still"
```

Use:

- `text2img` for prompt-only image generation
- `img2img` for one input image
- `compose` for multiple input images
- if `--model` is omitted, the CLI default is the legacy
  `agnes-image-2.1-flash`; pass `--model agnes-image-2.5-flash` for the
  official lineup
- image 2.5: `extra_body` carries `image`, `size`, `ratio` and
  `response_format`; no `tags img2img` needed

### Video

```bash
npx -y agnes-ai-cli@^0.1.0 video text2video \
  --prompt "A cinematic beach scene at dusk"

npx -y agnes-ai-cli@^0.1.0 video img2video \
  --image ./frame.png \
  --prompt "Add subtle wind and a slow camera push"

npx -y agnes-ai-cli@^0.1.0 video multivideo \
  --image ./frame-a.png \
  --image ./frame-b.png \
  --prompt "Blend these frames into one smooth motion concept"

npx -y agnes-ai-cli@^0.1.0 video keyframes \
  --image ./frame-a.png \
  --image ./frame-b.png \
  --prompt "Transition between these frames with a polished morph"

npx -y agnes-ai-cli@^0.1.0 video poll video_123 --interval 5 --timeout 600
```

Use:

- `text2video` for prompt-only video
- `img2video` for one image input
- `multivideo` for multiple guiding images
- `keyframes` for explicit keyframe interpolation
- `poll` for asynchronous completion
- if `--model` is omitted, the CLI default is the legacy `agnes-video-v2.0`;
  pass `--model agnes-video-2.5` (or `agnes-video-2.5-flash`) for the
  official lineup
- Video 2.5 uses `size` (720P-2K), `seconds` (4-12) and `mode`; polling is
  `GET https://apihub.agnes-ai.com/agnesapi?video_id=<ID>&model_name=<model>`,
  and `model_name` is required; legacy `taskId` polling still works for older tasks

## Practical CLI Workflow

### Text Verification

1. `npx -y agnes-ai-cli@^0.1.0 text chat --help`
2. `npx -y agnes-ai-cli@^0.1.0 text chat --prompt "Reply with exactly pong." --json`

### Text-To-Image

1. `npx -y agnes-ai-cli@^0.1.0 image text2img --help`
2. run `npx -y agnes-ai-cli@^0.1.0 image text2img ... --json`
3. read the returned image URL

### Image-To-Image

1. `npx -y agnes-ai-cli@^0.1.0 image img2img --help`
2. if the user gave a local path, let the CLI bridge it automatically
3. run `npx -y agnes-ai-cli@^0.1.0 image img2img ... --json`

### Multi-Image Composition

1. `npx -y agnes-ai-cli@^0.1.0 image compose --help`
2. pass `--image` multiple times
3. run with `npx -y agnes-ai-cli@^0.1.0 image compose ... --json`

### Text-To-Video

1. `npx -y agnes-ai-cli@^0.1.0 video text2video --help`
2. run `npx -y agnes-ai-cli@^0.1.0 video text2video ... --json`
3. capture `videoId`
4. run `npx -y agnes-ai-cli@^0.1.0 video poll <videoId> --json`

### Image-To-Video

1. `npx -y agnes-ai-cli@^0.1.0 video img2video --help`
2. if the user gave a local path, let the CLI bridge it automatically
3. run `npx -y agnes-ai-cli@^0.1.0 video img2video ... --json`
4. capture `videoId`
5. run `npx -y agnes-ai-cli@^0.1.0 video poll <videoId> --json`

### Keyframes

1. `npx -y agnes-ai-cli@^0.1.0 video keyframes --help`
2. pass `--image` at least twice
3. run `npx -y agnes-ai-cli@^0.1.0 video keyframes ... --json`
4. capture `videoId`
5. run `npx -y agnes-ai-cli@^0.1.0 video poll <videoId> --json`

## Image Guidance

Use the CLI as the execution layer, but keep these Agnes-specific rules in mind:

- Image 2.5 flash is the official default for new image work; Image 2.1
  remains available and Image 2.0 is a legacy compatibility choice
- for 2.5, img2img goes through `extra_body.image`; sizes run 1K-4K
- For edits, explicitly separate:
  - what should change
  - what must stay fixed
- For dense images, be explicit about:
  - primary subject
  - background environment
  - important secondary details
  - style and lighting
  - composition constraints

## Video Guidance

Use the CLI as the execution layer, but keep these Agnes-specific rules in mind:

- the API is asynchronous
- Video 2.5: use `size` (720P-2K), `seconds` (4-12) and `mode`; poll with
  `video_id` + `model_name` (the `model_name` parameter is required);
  the 2.5-flash variant is 720P-only, allows no video references and takes
  at most 5 images + 3 audio inputs
- legacy Video 2.0 rules (only when explicitly using `agnes-video-v2.0`):
  - `num_frames` must be `<= 441`
  - `num_frames` must satisfy `8n + 1`
  - `frame_rate` supports `1-60`
  - common safe example settings are:
    - `width: 1152`
    - `height: 768`
    - `num_frames: 121`
    - `frame_rate: 24`
- for keyframes, use the dedicated CLI subcommand instead of inventing your
  own payload shape

For text-to-video prompts, describe:

- subject
- action
- environment
- camera movement
- lighting
- style

For image-to-video prompts, describe:

- what should move
- what should stay stable
- how subtle or dramatic the motion should be

For keyframes and multi-image work, describe:

- how the inputs relate
- what continuity should remain stable
- what transition feeling is desired

## JSON Output

Prefer `--json` whenever the command result will be consumed by the agent.

Examples:

```bash
npx -y agnes-ai-cli@^0.1.0 image text2img --prompt "..." --json
npx -y agnes-ai-cli@^0.1.0 video text2video --prompt "..." --json
npx -y agnes-ai-cli@^0.1.0 video poll video_123 --json
```

This makes it easier to:

- read `taskId` and `videoId`
- extract image URLs
- extract final video URLs
- detect failures cleanly

## Operational Guidance

- Supported companion CLI range for this skill release:
  - `>=0.1.0 <0.2.0`
- Prefer live CLI tests over guessing when the user asks whether a model path
  or parameter actually works.
- For image results, expect a URL in the response.
- For video results, expect task creation first, then polling.
- Prefer `videoId` for polling. Passing an older `taskId` remains compatible
  through the CLI's legacy endpoint routing.
- Use the CLI's local-file bridge instead of manually uploading files yourself
  unless the user explicitly wants a separate upload step.
- If the user asks for SDK code, translate the confirmed CLI behavior into the
  target language only after the CLI path has been validated.
- If the user asks about pricing, limits, or free access, verify the live docs.

## Compact Reference

- Base URL: `https://apihub.agnes-ai.com/v1`
- Text endpoint behind CLI: `/chat/completions`
- Image endpoint behind CLI: `/images/generations`
- Video create endpoint behind CLI: `/videos`
- Video recommended poll endpoint behind CLI: `/agnesapi?video_id={video_id}`
- Video legacy poll endpoint behind CLI: `/videos/{task_id}`

- Text model: `agnes-2.0-flash`
- Image model: `agnes-image-2.1-flash`
- Image compatibility model: `agnes-image-2.0-flash`
- Video model: `agnes-video-v2.0`

## Do Not

- Do not proceed with live Agnes calls when the key is missing
- Do not default to raw `curl` for Agnes execution in this skill
- Do not rebuild request payloads by hand when the CLI already covers the flow
- Do not skip `video poll` and assume video generation is synchronous
- Do not trust stale marketing claims over the current API docs

## Safety

- Never echo a full Agnes API key back to the user after it has been supplied
- Never continue with live Agnes requests when auth is missing or clearly
  invalid
- Never treat article copy or marketing claims as more authoritative than the
  official Agnes docs
- Never promise pricing, limits, or "forever free" terms without noting they
  can change over time
- Never write the key to a project file unless the user explicitly asks for
  that behavior

## Installation

With repository-aware skill installers:

```bash
npx skills add jomeswang/agnes-ai-skill -g
```

After installation, invoke this skill whenever Agnes setup or Agnes model usage
comes up.

## Version History

`1.3.0` - Refreshed the model lineup to the official AgnesAI-Labs family 2.5 (text 2.5-flash, image-2.5-flash, video-2.5 and 2.5-flash), added the 3.0 series per the current official docs, marked the 2.0 models as legacy, documented video polling with `video_id` + `model_name`, image-to-image via `extra_body` (no `tags img2img`), CLI 0.1.6 notes and the updated docs hub (`wiki.agnes-ai.com` + vendor model catalog).
- `1.2.2` - Added a linked Chinese README and Chinese quick-start onboarding
  guidance for agent responses.
- `1.2.1` - Made `npx -y agnes-ai-cli@^0.1.0` the default copy-paste execution
  path in fresh environments and kept global `agnes` as an optional fast path.
- `1.2.0` - Switched the skill to CLI-first Agnes execution, removed raw curl
  execution guidance, and made `--help` discovery part of the expected flow.
- `1.1.2` - Added dual-track CLI guidance so agents prefer the separate Agnes
  execution layer when available and keep raw `curl` as the fallback.
- `1.1.0` - Expanded official doc coverage for Image 2.0, Image 2.1, and Video
  2.0 parameters, scenarios, prompt structures, response fields, and task
  states.
- `1.0.0` - Initial public release with Agnes platform setup, persistent auth,
  text, image, and video workflow guidance.
