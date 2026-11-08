# Phase 10: Launch

| | |
|---|---|
| **Status** | 🟨 In progress |
| **Effort** | 2–3 days [Estimate] (plus community follow-up) |
| **Milestone** | M7: Launched |

## Goal
Make OfflineBench public, get it indexed, and introduce it to the right communities honestly and without spam.

## Entry criteria
- M6 reached: all Phase 9 release gates pass.

## Read first
- `06-delivery/launch-checklist.md` (from P9)
- [product.md §9–11](../../01-product/product.md#9-monetization-roadmap)

## Tasks

### Go live
- [ ] **P10-T01** Connect the domain (if D-1 = buy) to Cloudflare Pages; set `NEXT_PUBLIC_SITE_URL`; HTTPS verified; redirect `*.pages.dev` production host to the domain.
  - *Not needed at launch (2026-11-08):* owner decided to stay on the free `offlinebench.pages.dev` for now and buy `offlinebench.app` later (D-1 unchanged). Do this task when the domain is bought.
- [ ] **P10-T02** Production deploy from `main`; smoke test every tool on production.
- [ ] ~~**P10-T03** Enable analytics~~: skipped, no analytics at launch (P9-T19, [analytics-monitoring.md](../analytics-monitoring.md)). Set up Search Console and Bing instead (P10-T04, P10-T05).

### Search engines
- [ ] **P10-T04** Google Search Console: verify property, submit sitemap, URL-inspect homepage + 5 key tool pages, request indexing.
  - *Progress:* URL-prefix property for `https://offlinebench.pages.dev/`, verified by `public/google4624aa71a897255e.html`. Keep that file: removing it can undo the verification. When a domain is bought, add a new property and use Change of Address.
  - *Progress (2026-11-08):* the sitemap submitted on 2026-11-06 showed "Couldn't fetch" and had never been read; `/sitemap.xml` serves valid XML (200, `application/xml`) to Googlebot, so it was resubmitted. Indexing requested for the homepage; the 5 tool pages (merge-pdf, jpg-to-pdf, pdf-to-jpg, compress-image, json-formatter) are "URL is not on Google" and hit the daily request quota. Still to do: request those 5 on later days and confirm the sitemap reads "Success".
- [x] **P10-T05** Bing Webmaster Tools: verify, submit sitemap.
  - *Done (2026-11-08):* site imported from Search Console (verification and sitemap). `jpg-to-pdf` already "Indexed successfully"; indexing requested for the others. Two pages, one of them `pdf-to-jpg`, were not indexed: one "Blocked" ("known to Bing but has some issues"), and `pdf-to-jpg`'s live test "not able to fetch this page". Both serve 200 with no `noindex` to the bingbot user agent, as `jpg-to-pdf` does. Re-check in about 2 weeks; if still blocked, contact Bing Webmaster support.
- [ ] **P10-T06** Check rendered HTML in URL Inspection matches expectations (content present without JS interaction).

### Community launch (honest, following each community's rules)
- [ ] **P10-T07** Prepare launch materials: short description, screenshots/GIF of the tool in action, the privacy claim and how to verify it.
- [ ] **P10-T08** "Show HN" post (developer tools + privacy angle); be present to answer questions.
- [ ] **P10-T09** Relevant subreddits only where self-promotion is allowed (read rules first); dev.to/Hashnode write-up of how local processing works.
- [ ] **P10-T10** Submit to reputable tool directories and "awesome" lists where OfflineBench genuinely fits.
- [ ] **P10-T11** Open-source a useful part (e.g. a detector library or the image pipeline) if decided, with a link back.
- [ ] **P10-T12** Add donation link (GitHub Sponsors or similar).

### Follow-up (first 2 weeks)
- [ ] **P10-T13** Triage feedback and bug reports daily; fix P0/P1 quickly.
- [ ] **P10-T14** Monitor Search Console coverage and errors; fix indexing issues.

## Exit criteria
- [ ] Production live on final URL; all tools working.
- [ ] Sitemaps submitted to Google and Bing; homepage indexed.
- [ ] Launch posts published; feedback triaged.

## Risks & fallbacks
| Risk | Fallback |
|---|---|
| Launch post gets little attention | Normal; focus on steady channels (search, directories, guides). Don't repost spam-style |
| Traffic spike | Static assets on Cloudflare: no action needed; watch for client errors |
| Bug found by early users | Rollback via Cloudflare (instant) while fixing |
