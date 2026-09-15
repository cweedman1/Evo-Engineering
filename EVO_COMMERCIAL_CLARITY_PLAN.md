# Evo Engineering Commercial Clarity Plan

## 1. Executive Assessment

Evo Engineering already communicates a coherent identity. The site is disciplined, technically credible, visually distinctive, and unusually consistent about the ideas that define the company: systems, context, resilience, maintainability, integration, operational reality, and trust. The black-and-gold visual system, industrial photography, restrained editorial layouts, SSI lineage, and current-project evidence all support the same position. The site does not look improvised, generic, or unsure of itself.

The unresolved commercial question is simpler: **what can a visitor ask Evo to do?** The current homepage identifies four domains and says that Evo builds “resilient, understandable, maintainable systems,” but it does not translate that promise into recognizable situations such as custom operational software, a brittle inherited system, a workflow with too many handoffs, an unclear process, or a cross-disciplinary modernization problem. A visitor can understand Evo's worldview before knowing whether their own problem belongs here.

That makes the next revision a reorientation, not a redesign. The present design and technical system should remain the frame. The missing layer is an early, compact bridge between Evo's philosophy and a buyer's problem:

1. What kinds of problems can I bring?
2. What does Evo do with them?
3. Where has Evo applied that discipline?
4. What is the easiest way to start?

The smallest effective revision is to make that bridge on the homepage, remove Finance from the active commercial presentation, lightly align a few supporting pages, and preserve the rest.

## 2. Current Site Architecture

### Repository and deployment model

- Branch at inventory time: `main`, aligned with `origin/main` at commit `936f3ac`.
- Working tree at inventory time: clean before this report was created.
- Hosting model: static HTML/CSS/JavaScript with `CNAME` set to `www.evo.engineering`, `.nojekyll`, and no build step.
- `DEPLOYMENT_NOTES.md` explicitly preserves GitHub Pages compatibility and describes CDN cache policy as an edge concern.
- There are no framework, package-manager, build-tool, CMS, form-service, or runtime dependencies in the repository.
- There are no repository-defined redirects, response headers, CSP rules, DNS records, certificates, or Cloudflare configuration files.

### Production pages

| File | Canonical role | H1 | Primary body structure | Schema page type |
|---|---|---|---|---|
| `index.html` | Homepage | Building Sovereign Systems | Hero plus four domain feature cards | `WebPage` |
| `projects.html` | Current proof | Systems We're Building | Eight editorial project/proof blocks | `CollectionPage` |
| `about.html` | Company perspective and lineage bridge | About Evo Engineering | Roots, operating discipline, domains | `AboutPage` |
| `energy.html` | Energy application domain | Energy & Grid Renewal | Domain overview, deliverables, value | `WebPage` |
| `finance.html` | Retiring Finance domain | Finance & Capital Renewal | Domain overview, deliverables, value | `WebPage` |
| `manufacturing.html` | Manufacturing application domain | Manufacturing & Systems | Domain overview, deliverables, value | `WebPage` |
| `software.html` | Software application domain and partial capability page | Software & Intelligence | Domain overview, deliverables, value | `WebPage` |
| `ssi.html` | SSI lineage and credibility | Southwest Systems Integrators Legacy | History, clients, continuity, relevance | `WebPage` |
| `contact.html` | Engagement entrance | Contact | Fit, direct contact, engagement areas | `ContactPage` |

There are no additional production HTML pages.

### Navigation and internal links

Every page repeats the same semantic primary navigation: Home, Projects, About, Energy, Finance, Manufacturing, Software, Legacy, Contact. The current page receives both `class="active"` and `aria-current="page"`. The brand also links to `index.html`.

The global navigation supplies the majority of internal links. A smaller contextual graph adds useful semantic connections:

- Energy links to About and Software.
- Manufacturing links to SSI.
- SSI links back to Manufacturing.
- About links to SSI.
- Projects links to Energy, Software, and Contact.
- The homepage links to each current domain.

This graph is small but intentional. It connects lineage to manufacturing, systems thinking to applications, and proof to engagement. It should not be replaced with a large generated cross-link mesh.

### CSS

Eight small stylesheets total approximately 8 KB uncompressed:

- `css/main.css`: tokens, global defaults, focus behavior, base animation.
- `css/nav.css`: sticky header, brand, desktop navigation, active state, mobile toggle.
- `css/hero.css`: home and interior hero geometry, overlays, media behavior, typography.
- `css/cards.css`: homepage domain grid and feature-card treatment.
- `css/sections.css`: content width, editorial blocks, project treatments, links.
- `css/footer.css`: restrained two-line footer.
- `css/utilities.css`: screen-reader-only and small utility classes.
- `css/responsive.css`: breakpoints at 980, 900/721, 720, and 420 pixels plus reduced-motion handling.

The organization is comprehensible and responsibility-based. No Finance-specific selector exists. The stylesheets are shared by all nine pages.

### JavaScript

`nav.js` is the only script and is 944 bytes. It is loaded with `defer` on every page. It performs only mobile-navigation behavior: toggle state, body scroll state, `aria-expanded`, dynamic open/close label, close on link activation, and close on Escape. It has no dependencies, analytics, tracking, animation library, or page-specific branch. It contains no Finance dependency.

### Assets

The repository contains 50 image files in `images/` (approximately 2.95 MB in aggregate), plus a PNG and SVG master social card in `assets/social/`.

- Each of the nine pages has a four-size WebP hero family at 600, 800, 1200, and 1600 pixels.
- The homepage has three-size WebP domain-card families at 400, 600, and 800 pixels for Energy, Finance, Manufacturing, and Software.
- `images/evo_logo-128.jpg` is used in visible navigation.
- `images/evo_logo.jpg` is referenced by absolute URL from structured data and by the source social SVG.
- `assets/social/social-template.png` is the shared Open Graph and Twitter image on all pages.
- `assets/social/social-template.svg` is a source/master asset rather than a file linked directly from production HTML.
- `favicon.ico` is linked from every page.

All referenced local HTML, CSS, JavaScript, image, and favicon paths resolved during this inventory.

### Metadata, SEO, and structured data

Every page includes:

- UTF-8 and responsive viewport declarations.
- `index, follow` robots metadata.
- A unique title and description.
- Keywords, author, and theme color.
- Open Graph title, description, canonical URL, type, image, image dimensions, and image alt text.
- Twitter card, title, description, image, and image alt text.
- A self-referencing canonical.
- A favicon.
- Hero-image preload with `imagesrcset`, `imagesizes`, and high fetch priority.
- Valid JSON-LD using an `@graph` with stable Organization and WebSite IDs plus the page-specific entity.

The homepage canonical is `https://www.evo.engineering/`; interior canonicals retain explicit `.html` URLs. The sitemap uses the same canonical URL family. Internal Home links use `index.html`, meaning `/` and `/index.html` are navigational aliases in practice while `/` is the declared canonical. There is no repository-defined redirect between them. This arrangement is currently coherent and should not be changed merely for aesthetic URL normalization.

`robots.txt` allows all crawling and points to `https://www.evo.engineering/sitemap.xml`. The sitemap contains all nine canonical pages, with the homepage at priority 1.0, Projects and Energy at 0.9, About/Finance/Manufacturing/Software at 0.8, and SSI/Contact at 0.6.

### Responsive, semantic, and accessibility architecture

- The desktop navigation collapses to an explicit button-driven menu below 980 pixels.
- Homepage cards move from four columns to two and then one.
- Content widths use `min()` and stable maximum-width tokens.
- Hero heights and type scale down at narrower breakpoints.
- All pages contain exactly one H1 and logical H2 sequences.
- Primary navigation is labeled; the toggle has an accessible name and state.
- Decorative hero media uses empty alt text inside an `aria-hidden` picture.
- Meaningful homepage card images have descriptive alt text.
- Visible keyboard focus is defined globally.
- `prefers-reduced-motion` reduces animation and transition duration.
- Image width/height attributes reserve layout space.
- External project links opened in a new tab use `rel="noopener"`.

## 3. Current Visitor Journey

A first-time homepage visitor currently learns the following sequence:

1. **Identity:** the logo, black/gold system, industrial photograph, and “Building Sovereign Systems” establish a serious technical identity immediately.
2. **Philosophy:** the hero explains that Evo values resilience, understandability, maintainability, context preservation, and reduced unnecessary work.
3. **Domains:** four large feature cards present Energy, Finance, Manufacturing, and Software.
4. **Choice:** the visitor must select a domain or use the top navigation to continue.

Capability becomes clearer only after that choice. Energy, Manufacturing, and Software each contain a “What We Deliver” list. Software gets closest to a general capability explanation with modeling and simulation, decision support, secure platforms, and context preservation. Manufacturing demonstrates concrete integration and modernization work. Contact lists engagement areas. Projects proves that Evo builds real systems and finally offers “Start a conversation.” SSI establishes provenance.

The key moments are therefore:

- Identity: immediate.
- Systems philosophy: immediate.
- Application domains: immediate.
- Concrete capabilities: one click later and fragmented by domain.
- Proof: available through a separate primary-navigation choice.
- Engagement: available through Contact, or at the end of Projects.

The visitor is never blocked, but the site makes them perform the translation from “Evo's systems philosophy” to “my operational problem is something Evo can take on.”

## 4. Commercial Clarity Gap

The current copy is strong but mostly declarative and inward-out. The homepage says:

> Building Sovereign Systems

and:

> We build resilient, understandable, maintainable systems for operators working across energy, manufacturing, finance, and software—preserving context and reducing unnecessary work.

This explains the desired properties of Evo's work and names the operating domains. It does not yet name the buyer's recognizable starting conditions. The only subsequent homepage labels are Energy, Finance, Manufacturing, and Software. Those labels answer “where?” rather than “what can I bring?”

The supporting pages contain the missing commercial material, but it is distributed:

- Manufacturing says Evo handles line modernization, material handling, packaging/palletizing, and full-service integration.
- Software says Evo develops operator-facing tools, simulations, decision-support systems, secure platforms, and context-preserving systems.
- Energy says Evo coordinates assets, controls, weather, operators, recovery, and infrastructure renewal.
- Contact says Evo is a fit for inherited systems, real constraints, and human operators.
- Projects asks, “How do we reduce unnecessary work while improving trust in complex systems?” and shows real systems built from that question.

The gap is not lack of substance. It is lack of an early commercial synthesis. The site currently asks visitors to infer that Evo can be hired to diagnose and improve a tangled system, determine whether software is appropriate, build custom operational software, redesign a workflow, or modernize a brittle interface across people and technology.

## 5. What Evo Actually Offers

### Capabilities: what Evo can help a client do

The repository evidence and the intended direction support four capability families. These should be treated as a commercial model, not necessarily as final labels or separate pages.

1. **Understand a complicated operating system.** Map the actual system across equipment, software, state, information, operators, decisions, constraints, dependencies, and handoffs. Identify where context is lost and where the documented process differs from operational reality.
2. **Build operational software.** Create custom tools, models, simulations, decision support, integrations, and platforms where state, lineage, auditability, and operator context matter.
3. **Improve processes and workflows.** Reduce repeated work, unnecessary handoffs, ambiguous ownership, weak interfaces, spreadsheet fragmentation, and avoidable dependence on institutional memory.
4. **Modernize for resilience and maintainability.** Bridge inherited and new systems, make failure and state visible, strengthen dependencies, preserve useful context, and improve the system without assuming wholesale replacement is necessary.

These capabilities share one method: understand the operating system before prescribing a product. That principle differentiates Evo from a software agency that begins with an app, an automation vendor that begins with a tool, or a consultancy that ends with a slide deck.

### Domains: where Evo applies those capabilities

- **Energy:** grid renewal, infrastructure resilience, orchestration, recovery, and operator coordination.
- **Manufacturing:** equipment, controls, material flow, automation, commissioning, and production workflows.
- **Software:** operational software, simulations, decision support, secure platforms, state, context, and auditability.

Finance is no longer an active public commercial domain. Capital, cost, asset condition, timing, and deployment constraints can remain part of systems analysis when relevant; that is different from selling financial engineering or Finance as an Evo service line.

The services/domains distinction can be stated simply:

> Evo understands, improves, modernizes, and builds complex operating systems. Energy, manufacturing, and software are the active domains in which that discipline is visibly applied.

This is a positioning model, not proposed final homepage copy.

## 6. Proposed Homepage Information Architecture

The homepage should remain visually recognizable and use the existing static primitives. The smallest useful architecture is:

1. **Header and primary navigation.** Preserve the current component and styling; remove Finance only when the retirement implementation is approved.
2. **Commercial hero.** Preserve the current photograph, overlay, scale, typography, and restrained tone. Refine the H1/supporting sentence so the first viewport contains both the systems position and a recognizable invitation. Add one plain primary path to Contact and, at most, one secondary path to Projects.
3. **Problems Evo can take on.** Add a compact editorial section naming three or four starting situations: custom operational software, a tangled workflow/process, a brittle inherited system, or a cross-boundary problem whose solution is not yet known. Do not turn this into generic SaaS product cards.
4. **How Evo works.** In a short paragraph or compact sequence, establish that Evo begins by understanding the actual system, then determines whether the right intervention is software, automation, integration, process redesign, modernization, or something simpler.
5. **Where Evo applies it.** Retain the existing feature-card visual treatment and imagery for Energy, Manufacturing, and Software. Move this domain layer after the capability layer. Remove the Finance card.
6. **Selected proof.** Add a restrained bridge to Projects using two or three short examples that demonstrate range, such as operational software, infrastructure coordination, and deterministic computation. Projects remains the full proof page.
7. **Field lineage.** Add one short SSI credibility statement and link. It should explain why Evo's cross-boundary view is grounded in operating environments, not present Legacy as nostalgia.
8. **Low-friction invitation.** End with a short Contact entrance that makes clear a finished specification is not required.
9. **Footer.** Preserve unchanged.

### What stays

- Home hero image and visual treatment.
- Black/gold palette, typography behavior, spacing discipline, and restrained tone.
- Existing domain-card component for the three active domains.
- Existing Projects, SSI, and Contact destinations.
- Static architecture and all technical performance patterns.

### What moves

- Active domains move from the only homepage body content to a later “where we work” layer.
- Some of the commercial meaning currently distributed across Software, Manufacturing, Projects, and Contact is synthesized near the top of Home; the source pages retain their depth.

### What is added

- An immediate problem/capability bridge.
- A concise “understand before prescribing” method statement.
- A visible but restrained engagement path.
- Small proof and lineage entrances.

### What is removed

- Finance as a homepage feature and active domain.
- Finance references that imply a current public offering.
- No visual system, active domain page, proof page, lineage page, or technical foundation is removed.

The homepage should not become a long-form services catalog. Its job is recognition and routing, not exhaustive explanation.

## 7. Navigation Analysis

### Option A: preserve the current navigation except Finance removal

Result: Home, Projects, About, Energy, Manufacturing, Software, Legacy, Contact.

Advantages:

- Smallest change and lowest regression risk.
- Preserves known page labels, URL prominence, keyboard behavior, active states, and internal-link equity.
- Keeps Energy, Manufacturing, and Software visible as legitimate commercial domains.
- Avoids creating capability pages before the architecture has evidence that they are needed.
- Reduces the mobile menu from nine choices to eight without inventing new interaction patterns.

Limitation: capabilities are not global-navigation items. The revised homepage must therefore make them unmistakable.

### Option B: introduce capability-oriented navigation

Possible labels might be Services, Systems Analysis, Software, or Modernization. This would make “what Evo does” globally visible, but it would require new pages or stable anchors, introduce label overlap with Software, increase maintenance, and risk presenting tentative categories as a mature service taxonomy. It would also alter the sitewide internal-link graph on every page.

This option is premature.

### Option C: hybrid navigation

A hybrid could add “What We Do” while retaining selected domain links, or group capability/domain concepts. In this static, restrained site, that either lengthens an already full desktop menu or introduces dropdown behavior and more JavaScript/interaction complexity. It can also obscure the existing direct paths to Energy, Manufacturing, and Software.

### Recommendation

Use **Option A** for the next revision. Put capability orientation in the homepage content, not the global navigation. Preserve current labels and URLs, remove only Finance, and evaluate later whether visitors need a dedicated capability page. This achieves commercial clarity with the least architectural and search disruption.

## 8. Finance Retirement Inventory

### Direct page and URL dependencies

`finance.html` is a complete, indexable production page with:

- Title: `Infrastructure Finance Systems - Evo Engineering`.
- Description, keywords, Open Graph, Twitter, canonical, and robots metadata.
- A four-size preloaded Finance hero.
- Organization, WebSite, and Finance-page JSON-LD entities.
- One H1, three H2 sections, and four deliverable claims.
- Shared navigation, footer, stylesheets, logo, favicon, social image, and `nav.js`.

### Every navigation reference

Each production page contains one Finance item in the primary navigation:

- `index.html:105`
- `projects.html:105`
- `about.html:105`
- `energy.html:105`
- `finance.html:105` (active/current state)
- `manufacturing.html:105`
- `software.html:105`
- `ssi.html:105`
- `contact.html:105`

Total: nine sitewide navigation links.

### Homepage references

- Meta description names Finance (`index.html:8`).
- Keywords include financial systems (`index.html:9`).
- Open Graph and Twitter descriptions name Finance (`index.html:14`, `index.html:26`).
- Organization, WebSite, and WebPage JSON-LD descriptions name Finance (`index.html:43`, `index.html:51`, `index.html:61`).
- Hero body copy names Finance as an active domain (`index.html:123`).
- The Finance feature link, image family, alt text, and H2 occupy `index.html:139-145`.

### References elsewhere in HTML

- **Projects:** page description, Open Graph description, and Twitter description name Finance (`projects.html:8`, `projects.html:14`, `projects.html:26`); shared Organization/WebSite JSON-LD descriptions also name it (`projects.html:43`, `projects.html:51`).
- **About:** description and keywords name Finance (`about.html:8-9`); shared and page-specific JSON-LD descriptions name it (`about.html:43`, `about.html:51`, `about.html:61`); the body presents “Financial Systems” as a carried-forward domain and describes Energy, Finance, Manufacturing, and Software as operating layers (`about.html:145`, `about.html:152`).
- **Software:** “Modeling & Simulation” currently says systems test outcomes across energy, finance, and manufacturing constraints (`software.html:136`).
- **All remaining pages:** Organization and WebSite JSON-LD descriptions name Finance as one of four active domains at lines 43 and 51 of each page.

There are no contextual body links to `finance.html` outside the global navigation and homepage feature card.

### Sitemap and crawler references

- `sitemap.xml:29` contains `https://www.evo.engineering/finance.html` with `lastmod` 2026-07-15 and priority 0.8.
- `robots.txt` does not mention Finance specifically; it allows the URL and advertises the sitemap.
- The Finance page is `index, follow` and self-canonical.
- No redirect, alias, `noindex`, or retirement directive exists in the repository.

### Asset dependencies

Finance-only presentation assets:

- Homepage card: `images/finance1-400.webp`, `images/finance1-600.webp`, `images/finance1-800.webp`.
- Finance hero: `images/finance2-hero-600.webp`, `images/finance2-hero-800.webp`, `images/finance2-hero-1200.webp`, `images/finance2-hero-1600.webp`.

These seven files appear only in the homepage Finance card or `finance.html`. They can eventually become removal candidates, but only after the public URL retirement is verified, the rollback window has passed, and direct image/search dependencies have been considered. They should not be deleted as part of the first implementation.

Shared assets used by Finance are not retirement candidates: logo files, favicon, the social PNG, the social SVG source, and all shared CSS/JavaScript.

The shared social artwork deserves one editorial review: its icon row includes an upward chart motif that can read as Finance. It contains no Finance text and also reads as optimization or system performance. Given the risk and the goal of preserving the established social identity, it should remain unless a later deliberate social-card revision establishes that users actually interpret it as an active Finance service.

### CSS and JavaScript dependencies

- All eight stylesheets are used by Finance but contain no Finance-specific selectors, URLs, or rules. Retiring Finance does not justify any CSS deletion.
- `nav.js` is shared and contains no Finance-specific logic. It should not change for retirement.

### Finance-related concepts that should remain

The following are broader systems concepts, not offers of regulated or standalone financial services:

- Capital as one real-world constraint among assets, controls, weather, timing, operators, and deployment (`energy.html`).
- The boundary between equipment, software, capital, workflows, and human judgment (`about.html`).
- Cost, risk, resource allocation, asset condition, and deployment sequencing when they are part of systems analysis.
- Historical research or project evidence elsewhere when accurately framed as research rather than an active commercial Finance domain.

The phrase “Financial Systems” as a current About-page domain and explicit cross-domain “finance” modeling claims should be retired or reframed. The word “capital” does not need to be purged mechanically.

### External historical dependencies

No Search Console export or Explorer report is stored in this repository. The supplied historical record must therefore be treated as an external measurement dependency, not a file dependency. It records 0 clicks and 113 impressions across the available 16-month period, with the URL currently indexed and sitemap-submitted. That evidence is low-traffic but nonzero and supports a deliberate retirement rather than silent deletion.

## 9. Finance HTTP Retirement Plan

### Equivalent destination assessment

No current surviving page is genuinely equivalent to `finance.html`.

- Home is a company entrance, not a replacement Finance resource.
- Energy mentions capital as one constraint but does not provide the same content or intent.
- About explains Evo's operating perspective.
- Software covers operational software, not infrastructure finance services.

Therefore a blanket 301 to Home, Energy, About, or Software would misrepresent the relationship and create a soft-404-like user experience. A 301 becomes correct only if Evo later publishes a substantially equivalent surviving resource that satisfies the old page's intent.

### Semantically appropriate treatment

If the public Finance offering is permanently withdrawn and no equivalent page exists, **HTTP 410 Gone** is the clearest final response. A normal 404 is also valid and will eventually deindex, but 410 communicates intentional permanent removal more directly. A temporary 302/307 is not appropriate for a permanent retirement. A `200` page with only a “retired” message prolongs index ambiguity and should be used only as a short, explicitly time-bounded transition if stakeholders need it.

### Required Cloudflare behavior, documentation only

Christopher and Clarity should implement and verify an exact-path rule for both expected forms of the URL, accounting for any current normalization behavior:

- `https://www.evo.engineering/finance.html`
- Any confirmed alias that actually resolves to that resource, such as `/finance` only if live verification proves it exists.

The final public response should return 410 without redirecting to Home. The body can be minimal and on-brand, but the status code is authoritative. The rule must not catch unrelated paths, finance-named assets, query variants incorrectly, or other site pages. DNS, certificates, proxy state, cache purge, and rule configuration remain entirely outside Codex scope.

Before activation, capture the current live status/canonical chain. After activation, verify the response at the public hostname, through normal and uncached requests, and confirm that Cloudflare is not returning a branded `200` error page. Coordinate sitemap removal with the 410 change so the sitemap does not continue asserting an intentionally gone URL.

### Search monitoring

Expected consequence: Finance impressions and index presence should decline to zero. That is not a regression if it is the intended retirement.

Monitor:

- URL Inspection status and last crawl.
- Page indexing reports for Not Found/Gone classification.
- Whether `/finance.html` continues receiving impressions or clicks.
- Whether Google selects an unexpected alternate canonical.
- Whether query visibility transfers naturally to a truly relevant surviving page; do not force it with an unrelated redirect.
- Sitewide clicks/impressions for Energy, Manufacturing, Software, Projects, and Home.
- 404/410 request volume and any legitimate referrals still pointing to the retired URL.

## 10. Search Preservation Plan

### URLs that must remain stable

- `https://www.evo.engineering/`
- `https://www.evo.engineering/projects.html`
- `https://www.evo.engineering/about.html`
- `https://www.evo.engineering/energy.html`
- `https://www.evo.engineering/manufacturing.html`
- `https://www.evo.engineering/software.html`
- `https://www.evo.engineering/ssi.html`
- `https://www.evo.engineering/contact.html`

`finance.html` is the one intentional exception and must follow the coordinated retirement plan rather than an incidental URL change.

Do not rename `.html` pages, introduce “clean URL” migrations, change `www`, or reorganize pages into directories for architectural neatness. Preserve the homepage canonical `/`; do not change `/index.html` behavior without live host evidence and a separate migration plan.

### Metadata worth preserving

- Current domain-page titles and high-specificity descriptions, especially Energy, Manufacturing, Software, SSI, Projects, and Contact.
- One unique H1 per page and the existing H2 hierarchy.
- Self-canonicals and matching `og:url` values.
- Stable Organization and WebSite `@id` values.
- Page-specific schema types (`CollectionPage`, `AboutPage`, `ContactPage`, and `WebPage`).
- Social-image dimensions, type, secure URL, and alt metadata.
- `index, follow`, UTF-8, viewport, theme color, author, and favicon declarations.

Sitewide and page metadata that names Finance as active should be edited narrowly. Do not use Finance retirement as permission to rewrite unrelated titles, canonicals, descriptions, schema types, or keyword sets.

### Internal-link structures worth preserving

- Global links to every surviving production page.
- Projects to Energy, Software, and Contact.
- About to SSI.
- Manufacturing to SSI and SSI back to Manufacturing.
- Energy to About and Software.
- Brand/Home access on every page.

Homepage capability language should add useful routing, not dilute domain links or create repetitive keyword anchors.

### Sitemap and canonical implications

- Preserve every surviving canonical exactly.
- Update `lastmod` only for pages whose substantive content changes, using the actual deployment date.
- Remove Finance from the sitemap when its public 410 retirement is activated; do not point the sitemap entry at another URL.
- Do not add capability URLs until real pages exist.
- Keep `robots.txt` open; blocking a retired URL in robots would prevent crawlers from seeing its 410 response.

### Finance-specific search risk

The supplied measurements show limited but real discovery: 0 clicks and 113 impressions over the available 16-month history, with 29 impressions in the latest 90-day window. Retirement sacrifices that visibility intentionally. The low volume limits commercial downside, but the current successful crawl, matching canonical, and sitemap inclusion mean Google has a clear, established URL; response semantics matter.

### Portfolio baseline and rollback

The supplied September checkpoint describes Evo Engineering as improving, including approximately +69 impressions and +2 clicks. Search Analytics indicates movement, not causality. Preserve a pre-change snapshot of page metadata, sitemap, Lighthouse results, crawl status, and relevant Search Console windows. Compare equivalent complete-date windows after deployment and separate the expected Finance loss from unexpected declines on surviving URLs.

Rollback should be file-scoped and edge-scoped:

- Keep a clean pre-change Git commit/reference.
- Keep Finance assets and `finance.html` during the initial monitoring window.
- Make the Cloudflare 410 rule independently reversible by Christopher/Clarity.
- If surviving pages regress, revert only the implicated content/navigation changes; do not automatically restore Finance unless the retirement decision itself changes.

## 11. Lighthouse Preservation Plan

The recorded 100/100/100/100 scores are release constraints, not general aspirations. The next implementation should begin by preserving the mechanisms that make them plausible and end with measured confirmation on mobile and desktop.

### Performance 100

Must remain true:

- Static HTML with no framework, hydration, bundle, or runtime dependency.
- No third-party fonts, trackers, form widgets, tag managers, or animation libraries.
- Hero preload remains limited to the actual above-the-fold hero and retains responsive candidates and high fetch priority.
- Hero and content images retain WebP sources, responsive `srcset`/`sizes`, explicit dimensions, and async decoding.
- Below-fold card/proof images remain lazy-loaded.
- CSS remains small, modular, and free of unused component systems.
- JavaScript remains deferred, dependency-free, and limited to navigation.
- New content should prefer HTML and existing styles over new assets or scripts.

Primary risks: adding multiple above-the-fold images, replacing WebP with oversized media, preloading unused images, introducing a web-font request, cumulative layout shift from missing dimensions, increasing DOM/card volume, and adding third-party conversion tooling.

### Accessibility 100

Must remain true:

- One descriptive H1 and a logical heading hierarchy.
- Labeled primary navigation and correct `aria-current` state.
- Toggle state/name updates, Escape close behavior, and keyboard reachability.
- Visible focus styles.
- Appropriate alt text: empty for decorative media, descriptive for meaningful linked images.
- Sufficient black/gold/text contrast.
- Reduced-motion support.
- Links that are understandable from their text and do not rely only on color.
- Contact remains usable without script or an inaccessible embedded form.

Primary risks: heading levels chosen for appearance, vague repeated “Learn more” links, gold text on insufficient backgrounds, focus loss in a redesigned mobile menu, decorative icons exposed to assistive technology, and CTA styling that removes focus visibility.

### Best Practices 100

Must remain true:

- No new console errors or failing resource requests.
- No unsafe third-party script or mixed-content dependency.
- New-tab links retain `noopener`.
- Images retain correct aspect ratios and reasonable resolution.
- HTTPS canonical and asset URLs remain consistent.
- Security headers and live response behavior are checked at the deployed boundary; this repository alone does not prove live Cloudflare/GitHub Pages headers.

Primary risks: embedded vendor code, incorrect redirect/error status behavior, broken external integrations, and assuming a visually rendered retirement page has the correct HTTP status.

### SEO 100

Must remain true:

- Crawlable semantic content, valid titles/descriptions, one H1, self-canonicals, mobile viewport, and descriptive link text.
- Valid JSON-LD with stable entity IDs.
- Accessible image descriptions where images convey meaning.
- Correct `robots.txt` and sitemap agreement.
- No accidental `noindex`, canonical collision, broken internal link, or orphaned active page.

Primary risks: broad metadata rewrites, stale Finance references in schema, sitemap/HTTP disagreement, duplicate capability pages, unrelated redirects, and replacing searchable text with graphical treatments.

### Release gate

For each implementation phase, run:

1. Local reference and JSON-LD validation.
2. HTML/heading/accessibility checks.
3. Mobile and desktop visual checks at key breakpoints.
4. Lighthouse against the same environment and settings used for the accepted baseline.
5. Live response/canonical/header checks after deployment by the authorized operator.

Any category below 100 is a release blocker until the delta is understood and accepted explicitly.

## 12. Page-by-Page Recommendations

| Page | Classification | Recommendation |
|---|---|---|
| Home (`index.html`) | **STRUCTURAL EDIT** | Preserve the hero media, visual system, and domain-card treatment. Add capability/problem recognition, method, proof, lineage, and a low-friction CTA; move the three surviving domains below the capability layer; remove Finance as an active domain. This is the primary commercial-clarity change. |
| Projects (`projects.html`) | **LIGHT EDIT** | Keep every current project and the editorial proof structure. Adjust only Finance-active metadata/schema language and, if useful, add one sentence that connects the breadth of projects to client engagements. Do not turn it into a dense portfolio grid or expand unverified claims. |
| About (`about.html`) | **LIGHT EDIT** | Preserve field-integration roots, the equipment/software/workflow/human-judgment boundary, and SSI link. Remove “Financial Systems” as a current domain and reframe the four-domain paragraph around the three active domains plus cross-boundary systems constraints. Keep this page focused on why Evo sees systems differently. |
| Energy (`energy.html`) | **KEEP AS-IS** | The page already names concrete work and operator outcomes. Apart from the shared Finance navigation/schema cleanup, its editorial body, title, description, canonical, hero, and hierarchy should remain. Keep “capital” as a legitimate infrastructure constraint. |
| Finance (`finance.html`) | **RETIRE** | Remove from active presentation and eventually serve 410 at the public URL through a manually managed Cloudflare rule. Do not delete the file or assets during the first implementation/rollback window. Do not redirect to Home without an equivalent resource. |
| Manufacturing (`manufacturing.html`) | **KEEP AS-IS** | It is the clearest concrete domain page and an important bridge to SSI. Apart from shared Finance navigation/schema cleanup, preserve its content, metadata, hero, and links. |
| Software (`software.html`) | **LIGHT EDIT** | Preserve operational software, state, lineage, auditability, decision support, secure platforms, and context preservation. Remove or reframe “finance” in the modeling bullet, and make custom operational software slightly easier to recognize without recasting Evo as a generic software agency. |
| Legacy / SSI (`ssi.html`) | **KEEP AS-IS** | Preserve the history, named clients, systems-integration evidence, and “What Carries Forward.” Apart from shared Finance navigation/schema cleanup, do not make it nostalgic or expand it into a corporate-history page. A homepage entrance should supply context for why the lineage matters. |
| Contact (`contact.html`) | **LIGHT EDIT** | Preserve direct email, website, and the no-friction static architecture. Broaden the invitation from named engagement areas to recognizable problem states, clarify that a finished specification is unnecessary, and retain the real-constraints/inherited-systems/operator fit statement. Avoid lead-capture machinery. |

There are no additional production pages to classify.

## 13. Contact / Conversion Architecture

Evo can become easier to hire without becoming salesy by lowering the visitor's burden of definition rather than increasing promotional pressure.

The Contact page and homepage invitation should communicate:

- A visitor may begin with a symptom, not a solution.
- The system may cross software, equipment, workflows, operators, and organizational boundaries.
- Evo can help determine what kind of intervention is appropriate.
- A finished requirements document, procurement package, or technical specification is not required for an initial conversation.
- Direct email remains the primary action.

A restrained engagement prompt could ask for three optional things: what is not working, who has to operate it, and what constraints cannot be ignored. This is enough to help a prospective client start without creating a qualifying questionnaire.

Conceptual phrases such as “Tell us what's not working,” “Bring us the complicated problem,” and “You don't need a finished specification” are directionally right. Final copy should sound like Evo: precise, calm, and operational. Use one clear CTA per major section, not repeated buttons after every paragraph.

Do not add a chat widget, scheduling embed, CRM form, gated download, pop-up, or third-party analytics merely to create “conversion.” Those would add performance, privacy, accessibility, security, and brand costs without evidence that direct email is insufficient.

## 14. Proof Architecture

Proof should be layered rather than dumped onto the homepage.

### Homepage: recognition-level proof

Use two or three compact examples selected for range, not a complete project list. Each should connect a recognizable system problem to an Evo capability and then link to Projects. For example:

- Maven: operational software and workflow intelligence in a high-accountability environment.
- NexusGrid Systems: coordination across infrastructure, assets, constraints, and operators.
- Helix Compute: deterministic computation that reduces unnecessary work while preserving results.

These demonstrate that “systems clarity” becomes actual software and operational architecture. Avoid reproducing all project descriptions or metric detail on Home.

### Projects: current evidence

Projects should remain the canonical collection of what Evo is building. Its current editorial blocks are better suited to Evo than a logo wall. Maintain the distinction between built systems, public engineering work, concise claims, and outbound destinations. Any quantitative claim must retain its scope and conditions.

### SSI: provenance

SSI supplies evidence that Evo's systems perspective predates current software products and comes from equipment, controls, commissioning, field constraints, deadlines, and operators. A homepage link should frame that lineage as the origin of the method. SSI itself should remain factual and forward-facing.

### Domain pages: applied evidence

Energy, Manufacturing, and Software should explain where the method applies and what deliverables look like. They do not need to become case-study archives. Contextual links to Projects and SSI can connect claims to evidence where useful, but link density should remain restrained.

The resulting proof chain is:

**Commercial recognition on Home → current systems on Projects → applied detail on domain pages → field provenance on SSI.**

## 15. Proposed Implementation Phases

### Phase 0: freeze the accepted baseline

- Record the current commit and clean worktree state.
- Capture comparable mobile/desktop Lighthouse reports for all representative templates: Home, one domain page, Projects, SSI, and Contact.
- Capture screenshots at desktop, tablet/navigation-collapse, and mobile widths.
- Export or record the current Search Console windows and URL Inspection state for all nine canonical URLs.
- Record current public response codes, canonical chains, and relevant headers.

This is evidence collection, not redesign work.

### Phase 1: retire Finance from active commercial presentation

- Remove Finance from the repeated navigation while preserving the component and order of all surviving items.
- Remove the homepage Finance feature and rebalance the existing three-card grid using the current responsive system.
- Remove or narrowly reframe active-Finance claims in homepage, About, Projects, and Software metadata/body copy.
- Update shared Organization/WebSite schema descriptions consistently across all nine source pages so structured data no longer advertises Finance as active.
- Keep `finance.html` and all Finance assets in the repository during the rollback window.
- Coordinate sitemap removal with Christopher/Clarity's exact-path 410 activation. Do not block the URL in `robots.txt` and do not configure Cloudflare from Codex.
- Validate links, JSON-LD, navigation state, responsive layout, and Lighthouse before release.

### Phase 2: add homepage commercial clarity

- Implement the approved homepage information architecture within the existing design language.
- Refine the hero to pair identity with hireability.
- Add compact problem/capability and method sections.
- Place the three active domains after the capability explanation.
- Add restrained Projects, SSI, and Contact entrances.
- Use existing CSS primitives where possible; add only the minimum new CSS required.
- Add no framework, external dependency, or new JavaScript unless a demonstrated accessibility requirement makes it unavoidable.

### Phase 3: align supporting pages

- Apply approved light edits to Contact, Software, About, and Projects.
- Preserve Energy, Manufacturing, and SSI editorial content except shared sitewide changes.
- Confirm language does not imply ME/EE/PE/EPC licensure, regulated engineering services, generic consulting, or product-first software delivery.
- Confirm every capability claim is supported by current work or lineage evidence.

### Phase 4: technical and search validation

- Repeat link, asset, heading, JSON-LD, metadata, responsive, keyboard, reduced-motion, and new-tab checks.
- Re-run Lighthouse using the accepted baseline method; require 100 in all four categories unless an explicit exception is approved.
- Verify deployed canonicals, status codes, sitemap, robots, cache behavior, and Cloudflare 410 behavior at the public boundary.
- Monitor Search Console using complete comparable windows, separating expected Finance deindexing from surviving-page performance.
- Keep rollback artifacts until the crawl and performance results are stable.

## 16. Files That Should Not Be Touched

The following do not need modification for commercial clarity or repository-side Finance deactivation:

- `nav.js`
- `favicon.ico`
- `CNAME`
- `.nojekyll`
- `.gitignore`
- `DEPLOYMENT_NOTES.md`
- `images/evo_logo-128.jpg`
- `images/evo_logo.jpg`
- Every non-Finance hero and domain-card image family
- `assets/social/social-template.png`
- `assets/social/social-template.svg`, unless a later separately approved social-identity change establishes a real need

For Phase 1 specifically, all eight CSS files should remain unchanged unless visual testing proves that removing the fourth homepage card creates a real layout defect. The current grid uses `repeat(4, minmax(0, 280px))` with centered justification; three cards can occupy it without a new component. If a CSS adjustment is later necessary, it should be limited to the existing card/grid rules and verified at all breakpoints.

The seven Finance-only WebP assets and `finance.html` should also remain untouched during the first implementation and rollback period even though they are eventual cleanup candidates. Removal is not required to stop presenting Finance publicly.

Do not touch any Cloudflare, DNS, certificate, proxy, cache, redirect, or edge-rule configuration.

## 17. Risk Assessment

| Risk | Level | Failure mode | Control |
|---|---|---|---|
| Visual risk | Medium | New sections make Home look like a generic consulting/SaaS template or dilute the industrial photography and restraint. | Reuse the current editorial vocabulary, feature treatment, spacing, palette, and photography; avoid component proliferation and review at all breakpoints. |
| SEO risk | Medium | Broad metadata changes, broken internal links, sitemap/status disagreement, canonical changes, or an unrelated Finance redirect disturb an improving property. | Preserve surviving URLs/canonicals/titles, make narrow copy changes, coordinate 410 and sitemap, validate deployed responses, and compare complete Search Console windows. |
| Lighthouse risk | Medium | New imagery, fonts, scripts, embeds, or layout shift reduce the accepted 100 scores. | Keep the static dependency-free architecture, reuse assets/styles, preserve responsive image contracts and dimensions, and make Lighthouse a release gate. |
| Accessibility risk | Low to Medium | New sections introduce heading disorder, weak link text, contrast problems, or mobile navigation regressions. | Preserve one-H1 hierarchy, labeled navigation, focus treatment, reduced motion, semantic text links, and keyboard testing. |
| Content risk | Medium | Capability language overclaims licensure, regulated engineering, financial services, turnkey delivery, or expertise not supported by the site. | Use repository-backed claims, describe cross-boundary systems work precisely, and review every claim against active work and SSI provenance. |
| Brand risk | High if overdesigned | Commercial clarity becomes generic agency language, aggressive sales copy, or a visual redesign. | Keep the voice calm and technical; make the buyer's problem explicit without changing Evo's visual or philosophical identity. |
| Scope-creep risk | High | Finance retirement expands into URL cleanup, a services taxonomy, new pages, framework migration, analytics, forms, or Cloudflare work. | Execute the phases separately, retain explicit file boundaries, and require approval before capability pages or infrastructure changes. |
| Retirement risk | Low commercial / Medium technical | The low-traffic Finance URL is redirected incorrectly, remains inconsistently advertised, or is deleted before rollback and edge verification. | Use an exact-path 410 when coordinated, remove active references comprehensively, retain the source/assets initially, and monitor deindexing. |

The dominant risk is not that the site changes too little. It is that “commercial clarity” becomes permission to replace a coherent system with familiar but generic patterns. The plan deliberately keeps the intervention narrow.

## 18. Recommended Next Codex Task

**Implement Phase 1 repository-side Finance deactivation only.**

The task should remove Finance from the repeated navigation and homepage domain grid; narrowly revise active-Finance body, metadata, social-description, and JSON-LD references across the nine HTML files; leave `finance.html`, all assets, CSS, JavaScript, surviving URLs/canonicals, and Cloudflare untouched; and update `sitemap.xml` only within a confirmed change window coordinated with Christopher/Clarity's exact-path 410 activation. It should finish with local link/asset validation, JSON-LD validation, responsive navigation/card checks, and comparable Lighthouse verification.

It should not yet implement the new homepage capability architecture. Separating retirement from homepage reorientation keeps the first production change reviewable, reversible, and easy to attribute.
