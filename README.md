# Cool Website (English)

A Codex skill for custom websites with scroll animations, spatial hero
entrances, and optional data-driven SEO. Websites are built in English by
default; you can explicitly ask for another language.

Looking for German output? Use the original
[cool-website](https://github.com/Arnie936/cool-website).

## What the skill does

- Clarifies the offer, audience, design, and the visitor action you want.
- Plans the page structure, visual layers, and fitting interactions.
- Uses your existing media or Codex's integrated image model for images and
  image edits. Videos are generated when needed via the official Higgsfield
  API (default) or kie.ai as the second option.
- After the first interview round it offers SEO with the DataForSEO MCP and
  guides you through setup, keyword research, implementation, and checks.
- Builds HTML pages on a bundled JavaScript/CSS engine.
- Checks the website in the integrated browser, fixes the issues it finds, and
  names any checks it could not run.

## Installation

In the root folder of your website project:

```sh
git clone https://github.com/Arnie936/cool-website-en.git .agents/skills/cool-website
```

Alternatively, download the repository as a ZIP and place its full contents in
`.agents/skills/cool-website/`. `SKILL.md` must sit directly in that folder.
Keep the references, engine, scripts, and license together.

Then start a new Codex turn, or a new chat in the project if needed. Example:

```text
Use $cool-website to build a website for my carpentry business.
The goal is enquiries from my region. I already have a logo and photos.
```

You can also delegate the design:

```text
Use $cool-website for my product. Decide the design yourself.
Use the integrated image model and plan without generated videos for now.
```

Delegating the design does not replace consent to paid API calls or new
external connections.

## Requirements

| Feature | Requirement |
|---|---|
| Run the skill | Codex with file/shell access |
| Generate and edit images | Integrated image model, no separate image API configuration |
| Check the website visually | Integrated browser via `mcp__cua_repl` |
| Use the helper scripts | Node.js 18 or newer |
| Prepare videos for scrolling | Full FFmpeg build and Bash, on Windows e.g. Git Bash |
| Generate videos, optional | Higgsfield API with `HF_API_KEY_ID` and `HF_API_KEY_SECRET` (default; [sign up here](https://higgsfield.ai/s/mcp-arnold-oberleiter-ecZvus)) or kie.ai with `KIE_AI_API_KEY`, each with API credit |
| Data-driven SEO, optional | DataForSEO account and a connected DataForSEO MCP |

The integrated image and browser features must be available in the Codex
environment you use. The skill does not install a separate browser automation
service as a substitute. API costs depend on the provider and the services you
actually call.

## Set the project folder

The output folder is resolved from `COOL_WEBSITE_HOME`, a `.cool-website.json`
in the project, or the nearest Git project folder. For an unambiguous location,
create this file in the root of your website project:

```json
{
  "workspace": "./website-output"
}
```

Save it as `.cool-website.json`. Builds then land in
`website-output/builds/<project-name>/`. Neither API keys nor private client
information belong in a public repository.

You can check the local requirements from the website project:

```sh
node .agents/skills/cool-website/scripts/doctor.mjs
```

Only if video generation is planned:

```sh
node .agents/skills/cool-website/scripts/doctor.mjs --video
```

The preflight checks local requirements. It does not confirm that integrated
tools are available or that an external login succeeded.

## Configure the video provider

Higgsfield is the default video provider, kie.ai is the second option.
No Higgsfield account yet? **[Sign up here](https://higgsfield.ai/s/mcp-arnold-oberleiter-ecZvus)**,
then create your API keys in the [Higgsfield Console](https://console.higgsfield.ai/).

There is a [.env.example](.env.example). Copy it as `.env` into the root of your
website project and fill in only the credentials of the provider you want.
Default configuration for Higgsfield:

```dotenv
COOL_WEBSITE_VIDEO_PROVIDER=higgsfield
HF_API_KEY_ID=your_higgsfield_key_id
HF_API_KEY_SECRET=your_higgsfield_key_secret
KIE_AI_API_KEY=your_kie_api_key
```

For KIE, set the provider to `kie` and fill in `KIE_AI_API_KEY`.
Unused placeholders can stay. Without a provider choice, Higgsfield is the
default. Environment variables that are already set take precedence over the
nearest `.env` above the working folder. Images and existing videos need none
of these keys. Never copy `.env` into the public website folder or commit it;
exclude it via `.gitignore` in the website project as well.

```sh
node .agents/skills/cool-website/scripts/doctor.mjs --video
node .agents/skills/cool-website/scripts/doctor.mjs --video --provider kie
```

The check rejects empty values and the shipped placeholders, and only requires
the credentials of the selected provider. It does not authenticate Higgsfield.
`--provider` overrides the selection for this check only. For Higgsfield the
agent follows the [REST guide](references/higgsfield-api.md); KIE keeps using
`scripts/kie.mjs`. You get API keys in the
[Higgsfield Console](https://console.higgsfield.ai/). A website subscription or
CLI login does not replace these API credentials.

## Optional SEO

The skill asks early whether you want SEO with DataForSEO. It reuses what you
have already said and only clarifies missing decisions on target market, offer,
domain, and research budget. If needed, it offers setup through this remote
endpoint:

```text
https://mcp.dataforseo.com/v3/mcp
```

The address identifies the server; the account login comes afterwards. The
research feeds into search topics, page structure, copy, metadata, internal
links, and technical improvements. Rankings are not guaranteed. Sign-up and
possible offers are explained in the
[setup guide](references/dataforseo-setup.md); the full process is in the
[SEO guide](references/seo-dataforseo.md).

## Structure

| Path | Contents |
|---|---|
| [SKILL.md](SKILL.md) | Workflow and rules for Codex |
| `agents/` | Display name and example prompt |
| `engine/` | Scroll engine and design defaults in JavaScript/CSS |
| `references/` | Design, media, SEO, and browser verification |
| `scripts/` | Preflight, project folder, video generation, encoding, and preview |
| `templates/` | Registry for comparing your own website projects |

The skill delivers project files and a local preview. Public hosting is a
separate step. A DataForSEO crawler cannot check private previews or localhost.
Mobile layout tests do not replace a test on a real smartphone.

## License

[MIT](LICENSE). The license, including the copyright notice, must be kept with
copies or substantial portions of the software.
