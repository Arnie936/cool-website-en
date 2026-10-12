# SEO with DataForSEO

This optional phase starts after the first interview round and then shapes
research, page planning, content, implementation, and verification. Guide the
user all the way to implemented improvements. A keyword report alone does not
fulfil the task. An SEO tool delivers data, not guaranteed rankings. Do not use
promises like "perfect SEO" or "guaranteed #1".

## 1. Decide early, ask briefly

Ask the choice from SKILL.md Step 0a once, or reuse an answer already given. For
"technical basics only" or "later", continue without paid research. Normal page
titles, understandable HTML content, and usable links still belong on the
website.

For yes, reuse existing answers from BRIEF.md. At most three short questions per
round; ask only about decisive gaps. Do not require the user to know SEO
terminology, finished keywords, or their search competitors.

A sensible first SEO round:

1. "Which offers, and which places or countries, do you want to be found for?"
2. "Is there already a website or domain, and should visitors mainly enquire,
   book, or buy?"
3. "Do you already have a DataForSEO account? For the first research pass I'll
   suggest a small budget within your existing credit."

Make the last question about account and budget concrete in the next step, once
access and prices are known. Skip parts that are already answered.

| Information needed | Why, and when to ask |
|---|---|
| Top 1–3 offers, real advantages, target customers, and main action | Search terms that fit the business instead of just high search volume |
| Country, language, and for local offers the city/catchment area | English copy does not automatically mean the target market is the US or the UK |
| Existing domain, new build or relaunch, allowed page scope | Preserve rankings and URLs; fitting pages instead of needless restructuring |
| Relevant products, services, prices, or solid proof | Ask for missing facts; never invent reviews or references |
| Known competitors and typical customer questions, if any | Take them as hints; research the real search competitors yourself |
| Search Console/Analytics/Business Profile, if they already exist | Use existing data; missing accounts do not block a new build |
| Budget ceiling and desired scope | A cheap first decision; expand only for concrete benefit |

Local businesses additionally need correct business details, actual locations,
opening hours, and services offered. Shops need real product/category
information; multilingual projects need their target markets. Go deeper only on
the branch that applies. Never create invented branches or automatically
multiplied location pages. If a language was already chosen explicitly, keep it
over the English default.

## 2. Connect and plan a small research pass

If access is missing, use [dataforseo-setup.md](dataforseo-setup.md). Reuse MCPs
that are already connected. While a login is pending, work on existing content
and technical basics without inventing search data.

Before the first paid call, show a concrete research plan with a cost ceiling.
Available credit is not permission to spend. Adopt a ceiling that has already
been approved and do not ask for approval of every single call. For example,
suggest a one-off start of at most 5 USD, but only if current credit, prices,
and scope support it; with less credit, plan smaller. The goal is a good first
page plan, not using up the budget.

A small starter plan is one market and one language, 3–5 seed terms, roughly
20–50 relevant candidates, 3–5 informative search result pages, and 2–3
relevant competitors. These are ceilings for a first pass, not required counts.
Retrieve less for simple projects. More markets, large crawls, backlink
analyses, and ongoing monitoring are extensions.

## 3. Use the MCP efficiently

The v3 connection may offer documentation access and a universal `api_request`.
Look at the real tool schemas first, search the documentation index in a
targeted way, and read only the endpoint pages you need. No catalogue of
invented tool names and no guessed API parameters.

| Decision | Matching data, if available in the account |
|---|---|
| What do suitable customers search for? | Keyword suggestions and relevant related terms |
| Which terms are in demand? | Bundled search volume/trend data for the chosen market and language |
| What kind of page does the search expect? | Current organic SERPs for the prioritised topics |
| What content is missing compared with search competitors? | A small domain/keyword gap analysis or targeted SERP evaluation |
| What matters for local offers? | Location-based SERPs/Maps and matching business data |
| What is still technically broken? | A bounded on-page check of a reachable, authorised public URL |

Efficiency rules:

- Resolve location and language parameters from the schema or the available
  lists. Store market, search engine, device, and date with the data.
- Deduplicate candidates locally first and remove off-topic terms. Use bundled
  keyword queries where the endpoint supports them. Read limits and costs per
  task/keyword/result beforehand.
- Request small result sets and only the depth required. Use live data only
  where the decision needs it. When a wait is acceptable, use cheaper
  asynchronous tasks; store the task ID and poll the existing task.
- Batch independent queries only within rate limits and budget. Reuse identical
  responses within the project. The cache key covers endpoint, parameters, and
  date; watch for price changes and stale SERPs.
- Keep a compact `seo/requests.jsonl`: timestamp, purpose, endpoint,
  non-secret parameters, task ID, status, estimated/reported cost, and result
  file. Keep only the fields you need. Never store credentials/headers. No
  second spreadsheet workflow for a simple keyword set.
- Before every further batch, add up costs already spent and still running
  against the approved cap. Clarify unclear prices before the call, do not
  replace them with "it'll be cheap". Stop when the remaining budget is
  uncertain.
- Distinguish HTTP, API, and task errors. On 401/403, fix the connection or
  permissions first. On 429, respect the stated delay. At most two justified
  retries of transient errors; check a job that may already have been accepted
  via its ID instead of paying again.
- Mark missing search volume as unknown, not zero. Google Ads competition and
  CPC are not organic SEO difficulty. Database estimates and third-party
  rankings are not your own Search Console data.

Save a compact keyword table in `seo/keywords.json` with term, market/language,
source/timestamp, available volume, search intent, relevant SERP observation,
priority, and intended URL. Metrics that are not available stay empty.
Prioritise fit with the offer, reachable search intent, and usefulness; high
volume alone does not justify a page.

## 4. Turn the results into a page plan

Record an understandable plan in `SEO-PLAN.md` with:

- Goal, market, target customers, conversion, budget, and connection status.
- The most important opportunities with data evidence and a short rationale.
- Per planned URL: main topic/keyword group, search intent, page type, unique
  title, H1, content outline, real proof, call to action, and sensible internal
  links.
- Technical tasks, priority by impact/effort, and open facts.
- Existing URLs, content to preserve, and required redirects on a relaunch.

Bundle similar terms with the same intent on one helpful page. Different
services or intents can need their own pages; section anchors on a landing page
are not independently indexable URLs. Explain a larger page scope briefly and
agree on it within the agreed task. If the user insists on one page, choose the
most important focus and mark other topics as later expansion steps.

Guide the user through the decisions in plain words. Decide pure implementation
details yourself. Only ask again about real business information, cost
increases, or an expansion of scope. If the user lacks expertise, make a
reasoned proposal; do not ask them to do the SEO review.

## 5. Actually implement SEO

**Content and navigation.** Write helpful, original English copy that fulfils
the chosen search intent and explains real differences. Use natural headings,
meaningful titles, and individual descriptions. Use search terms where they fit,
without density targets, hidden text, or strings of place names. Set meaningful
internal links with ordinary `a href` targets. Never invent rankings or revenue.

**Scroll website.** Ship essential text, headings, and links in the initial
HTML or server-side/prerendered. Content must not appear only after scrolling,
mouse movement, or an API call. Without animation and with reduced motion, all
content must remain readable. Canvas, WebGL, images, and videos do not replace
indexable product/service copy.

**Technical.** Implement one stable URL per public page, sensible status codes,
unique metadata, and a fitting canonical strategy. On a relaunch, keep an
old-to-new URL mapping and correct permanent redirects. Check 404 pages and
internal links. Align the XML sitemap with indexable canonical URLs, robots.txt,
and indexing rules on the real host. Never write localhost, test, or made-up
domains into production canonicals/sitemaps. If the domain is still open,
explicitly leave these publishing steps open.

**Preview and publishing.** Keep private previews private. A robots.txt
disallow does not replace `noindex` and does not protect confidential content.
Crawlers must be able to read a `noindex`. Before publishing, check for
accidental noindex/crawl blocks; do not remove all blocks indiscriminately.

**Media and performance.** Size images appropriately, compress them, and give
them width/height against layout shifts. Prioritise important above-the-fold
media and load other media as needed. Mind video posters, mobile sizes, little
render-blocking JavaScript, and restrained animation. Alt text describes the
content; decorative images get empty alt text. Judge Core Web Vitals/load time
from available measurements and distinguish lab from field data. No invented
scores or "100/100" guarantees.

**Structured data.** Mark up only fitting types such as Organization,
LocalBusiness, BreadcrumbList, Product, or Article with accurate facts that are
visible on the page. Use real prices/availability/business data. No invented
star ratings. Valid JSON-LD does not promise rich results; do not put FAQ markup
on every page indiscriminately. Multilingual variants need actual translated
URLs and correct reciprocal hreflang references.

**Relevant special cases.** For local businesses, account for consistent
business details and existing Business Profile goals. For shops, clarify the
category, product, and filter URL strategy. On a relaunch, protect existing
search performance and important URLs. Use documented editorial authorship and
sources where they belong to the content. Never invent people or experiences.
Change external profiles, send outreach, or connect Google services only when
asked to. No automatic backlink buying.

## 6. Verify and publish

Visual and interactive checks stay in the integrated browser per
[verify.md](verify.md). DataForSEO adds SEO data and possibly a remote audit to
that; it does not replace the browser check.

Before a deploy, check HTML content, titles, descriptions, headings, internal
links, image attributes, language tags, and JSON-LD in the final package. Check
publishing-dependent items separately. Document results in `SEO-REPORT.md` as
**implemented**, **locally verified**, **live verified**, or **pending**, each
with URL/file and evidence instead of a blanket "SEO is good".

An external on-page crawler needs a reachable public URL. Never report
`localhost`, login pages, or private previews as successful audits. Deploy only
within the authorised scope. If a public target page is available and there is
audit budget, check a few important URLs first; explicitly limit crawl limit,
depth, and rendering options. Fix relevant problems found and rerun only the
affected checks.

After an authorised publish, check redirects, canonicals, robots rules, sitemap,
HTTP status, and important links on the real host. If Search Console is already
connected with authorisation, run URL inspection/sitemap where supported;
otherwise explain the few owner steps needed. Neither creating nor submitting a
sitemap proves indexing.

## 7. Handover and sensible follow-up

Deliver a short summary: prioritised search topics, implemented
pages/content/technical work, data used, known API costs, open items, and the
next three sensible steps. Raw data, plan, and report live in the project. The
user should not have to translate the analysis into a website themselves.

Suggest a later review once enough data has been collected, for example after a
few weeks: indexing, impressions, clicks, CTR, relevant queries, and
enquiries/purchases. Prioritise changes based on that data. If needed, compare
targeted DataForSEO rankings for the same market and device. New domains need
time; do not over-interpret fluctuating snapshots. Do not set up cron jobs,
recurring API costs, or top-ups without being asked.

## Sources

Official foundations, checked on 2026-09-20. Check for changes to endpoints,
prices, access, and search engine rules before decisions that rely on them.

- [DataForSEO documentation](https://docs.dataforseo.com/v3/)
- [DataForSEO MCP and universal tools](https://dataforseo.com/help-center/dataforseo-new-mcp-server-and-cli-connection-a-quickstart-guide)
- [Google SEO starter guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)
- [JavaScript and indexable content](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
- [Structured data policies](https://developers.google.com/search/docs/appearance/structured-data/sd-policies)
