# Cool Website changes

## English edition

- English is the default language for websites and their visitor-facing content
  (`<html lang="en">`); another language still applies when the user asks for it.
- Translate the README, the DataForSEO setup and SEO guides, the page template
  copy, the SEO question in Step 0a, and the agent metadata to English.
- Higgsfield API is the default video provider; kie.ai is the second option
  (`COOL_WEBSITE_VIDEO_PROVIDER=kie`). Preflight, tests, and docs follow suit.
- Add the Higgsfield sign-up link for users without an account.
- Engine and the remaining scripts are unchanged.

## Optional Higgsfield video API

- Add `.env.example` with KIE and Higgsfield API credential placeholders.
- Keep KIE as default; support an explicit Higgsfield choice in the skill and preflight.
- Check only selected-provider credentials and reject empty/example values.
- Document official Higgsfield REST generation, model-specific inputs, polling,
  budget checks, and local video download/encoding.
- Share project environment loading between preflight and the KIE helper.

## Optional SEO phase

- Offer SEO immediately after the first interview round, before page planning.
- Guide optional DataForSEO remote MCP setup, account onboarding and verification.
- Add focused market intake, budgeted research, keyword-to-page planning,
  implementation, release checks and evidence-based follow-up.
- Preserve the language defaults, integrated image generation and browser control.
- Record the supplied registration offer without guaranteeing unverified credit
  or search rankings; check the actual balance and current costs.

## Local configuration

- Skill, engine files, public runtime name, configuration and workspace names
  use Cool Website / cool-website.
- German was the default language for websites in the original edition.
- Images and image edits use the integrated image model by default.
- kie.ai supports video generation only; image-generation code was removed.
- Browser control and verification use the integrated browser.
- Creator anecdotes, approval claims and personal example paths were removed
  from the workflow. The original software license is retained in LICENSE.
