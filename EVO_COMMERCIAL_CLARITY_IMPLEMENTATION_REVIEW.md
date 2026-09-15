# Evo Engineering Commercial Clarity Implementation Review

## Release Status Addendum — September 15, 2026

After this implementation review was completed, Christopher and Clarity manually configured and independently verified the Finance retirement layer. The following production responses were reported and accepted as the coordinated release prerequisite:

- `https://www.evo.engineering/finance.html` returns HTTP 410 Gone.
- `https://www.evo.engineering/finance.html?clarity=test` returns HTTP 410 Gone.
- `https://evo.engineering/finance.html` returns HTTP 410 Gone.
- `/`, `/energy.html`, `/manufacturing.html`, `/software.html`, and `/projects.html` remain unaffected and return HTTP 200.

The Worker is intentionally scoped to Finance. Codex did not configure, modify, or inspect Cloudflare. The historical references below to the then-pending Cloudflare handoff describe the state at the time of implementation review; that release gate is now satisfied, subject to post-deployment verification.

## 1. Executive Summary

The local revision implements the approved commercial-clarity architecture without redesigning the site or changing its technical foundation.

The homepage now answers five questions in five restrained beats:

1. Evo can be hired to understand and improve complicated operational systems.
2. Evo understands systems, builds operational software, improves workflows, and modernizes for resilience.
3. Evo applies that discipline in Energy, Manufacturing, and Software.
4. Current systems and the SSI lineage provide evidence.
5. A visitor can begin with a problem rather than a finished specification.

Finance has been removed from active public presentation and from the local sitemap. `finance.html`, its page content, its canonical, and all Finance image assets remain in the repository for rollback and monitoring. No redirect or HTTP 410 has been implemented locally. Cloudflare remains untouched.

The site remains static HTML/CSS/JavaScript, uses the existing imagery and visual system, adds no third-party dependencies, and retains the accepted Lighthouse scores of 100 for Performance, Accessibility, Best Practices, and SEO on every required mobile and desktop audit.

**Review recommendation: APPROVE the local revision for a coordinated release window. Do not deploy it independently of the Cloudflare retirement handoff.**

## 2. Files Changed

### Production files

- `index.html`
- `projects.html`
- `about.html`
- `energy.html`
- `finance.html`
- `manufacturing.html`
- `software.html`
- `ssi.html`
- `contact.html`
- `sitemap.xml`
- `css/cards.css`
- `css/hero.css`
- `css/sections.css`
- `css/responsive.css`

### Review artifact

- `EVO_COMMERCIAL_CLARITY_IMPLEMENTATION_REVIEW.md`

### Approved planning artifact already present before implementation

- `EVO_COMMERCIAL_CLARITY_PLAN.md`

### Intentionally unchanged

- `nav.js`
- `robots.txt`
- `favicon.ico`
- `CNAME`
- `.nojekyll`
- `.gitignore`
- `DEPLOYMENT_NOTES.md`
- `css/main.css`
- `css/nav.css`
- `css/footer.css`
- `css/utilities.css`
- All images and social assets
- All page filenames and surviving canonical URLs

## 3. Homepage Changes

The homepage now uses the approved five-beat sequence.

### Hero

- Preserves the existing home photograph, overlay, height behavior, typography, and responsive image preload.
- Replaces the philosophical-only H1 with `Engineering Clarity for Complex Systems`.
- States in the first viewport that Evo helps organizations understand complicated operational systems, improve how they work, and build what the operation needs.
- Adds two restrained links: `Bring us a problem` to Contact and `See what we're building` to Projects.

### What Evo Does

A compact editorial section presents four recognizable capability entrances without using a generic feature-card grid:

- Understand the operating system.
- Build operational software.
- Improve processes and workflows.
- Modernize for resilience.

The section names equipment, software, data, operators, workflows, handoffs, dependencies, and judgment as parts of the system. It also states that Evo does not begin with a predetermined product and that a finished specification is not required.

### Where Evo Works

- Preserves the existing domain-card vocabulary and existing Energy, Manufacturing, and Software imagery.
- Removes the Finance card.
- Keeps the surviving destination URLs unchanged.
- Uses a balanced three-column desktop layout, a two-plus-centered-one tablet layout, and a one-column mobile layout.

### Proof and lineage

- Adds a compact current-systems statement using Maven, NexusGrid Systems, and Helix Compute, based only on existing repository claims.
- Adds a restrained SSI lineage statement grounded in equipment, controls, operators, deadlines, and field constraints.
- Routes deeper evidence to Projects and SSI rather than reproducing either page.

### Invitation

The final section asks the visitor to begin with what is difficult to operate, maintain, understand, or trust. It makes clear that Evo can help determine the appropriate intervention.

The final homepage contains exactly five top-level sections and measures approximately 2.9 desktop viewport heights at 1440 × 1000. It remains an editorial company homepage rather than a long services landing page.

## 4. Supporting-Page Changes

### Projects

- Preserves every project, project description, link, claim, and structural block.
- Removes Finance from page description, Open Graph description, Twitter description, and shared Organization/WebSite schema language.
- Does not add a grid, sales treatment, or new project claim.

### About

- Preserves field-integration roots, the equipment/software/capital/workflow/human-judgment boundary, SSI link, and tone.
- Removes Finance as a current operating domain.
- Retains Energy, Manufacturing, and Software as the three active operating environments.
- Retains capital as a legitimate system boundary rather than removing the term mechanically.

### Energy

- Editorial body, title, description, H1, canonical, hero, and contextual links are unchanged.
- Only the shared navigation and Organization/WebSite descriptions changed.
- The existing reference to capital as one grid-coordination constraint remains.

### Manufacturing

- Editorial body, title, description, H1, canonical, hero, and SSI connection are unchanged.
- Only the shared navigation and Organization/WebSite descriptions changed.

### Software

- Preserves operational software, modeling, simulation, state, lineage, auditability, decision support, secure platforms, and context preservation.
- Changes the introductory phrase to `custom operational software` so the capability is easier to recognize.
- Reframes the modeling bullet from `energy, finance, and manufacturing constraints` to `energy, manufacturing, and operational constraints`.
- Preserves title, canonical, schema type, hero, and page structure.

### SSI / Legacy

- Editorial body, named clients, history, integration claims, H1, canonical, and hero are unchanged.
- Only the shared navigation and Organization/WebSite descriptions changed.

### Contact

- Preserves direct email, website link, static architecture, title, canonical, schema type, hero, and existing contact details.
- Reorients the first section around `Start With What Is Not Working`.
- States that a finished specification or predetermined solution is unnecessary.
- Adds systems analysis, custom operational software, and workflow/integration improvement to the existing engagement areas.
- Adds no form, widget, scheduling tool, tracker, external script, or dependency.

## 5. Finance Deactivation Changes

Completed locally:

- Finance removed from primary navigation on all nine HTML pages.
- Finance homepage card removed.
- Finance removed from homepage hero positioning, metadata, social descriptions, keywords, and page schema description.
- Finance removed from Projects metadata and social descriptions.
- Finance removed as a current About domain.
- Finance removed from the Software modeling reference.
- Shared Organization and WebSite descriptions on all nine source pages now describe work across Energy, Manufacturing, and Software.
- `finance.html` removed from `sitemap.xml`.

Search verification found `Finance`/`financial` references only inside the intentionally retained `finance.html`. There is no surviving internal link to `finance.html`.

The retained Finance page was changed only where necessary to remove Finance from its own global navigation and to align shared Organization/WebSite descriptions. Its Finance-specific title, metadata, canonical, page schema, hero, and editorial body remain intact for rollback.

Not implemented:

- No HTTP 410.
- No redirect.
- No `noindex`.
- No `robots.txt` block.
- No Cloudflare, DNS, certificate, proxy, redirect, cache, or edge-rule change.

## 6. Sitemap State

The local `sitemap.xml` no longer contains `https://www.evo.engineering/finance.html`. Every surviving canonical URL remains present and unchanged.

`robots.txt` remains unchanged and continues to allow all crawling, so Google will be able to observe the eventual 410 response.

**Do not deploy this repository state until the Cloudflare 410 rule is ready to activate at the same release window.**

Sitemap `lastmod` dates were not changed because no deployment occurred and the actual release date is not yet known. If the release operator updates `lastmod`, it should use the real deployment date only for pages with substantive content changes.

## 7. Search-Preservation Verification

Verified unchanged:

- `https://www.evo.engineering/`
- `https://www.evo.engineering/projects.html`
- `https://www.evo.engineering/about.html`
- `https://www.evo.engineering/energy.html`
- `https://www.evo.engineering/manufacturing.html`
- `https://www.evo.engineering/software.html`
- `https://www.evo.engineering/ssi.html`
- `https://www.evo.engineering/contact.html`

Also verified:

- Homepage canonical remains `/`, not `/index.html`.
- Interior canonical family remains explicit `.html`.
- `www` host remains unchanged.
- Page titles remain unchanged.
- Domain-page descriptions remain unchanged where still accurate.
- Stable Organization and WebSite `@id` values remain unchanged.
- Page-specific schema types remain unchanged.
- Open Graph and Twitter image metadata remain unchanged.
- The existing internal links among Projects, Energy, Software, About, Manufacturing, SSI, and Contact remain intact.
- No new URL, redirect, directory, alias, capability page, or canonical was introduced.

Metadata edits were limited to Finance retirement and homepage commercial clarity.

## 8. Visual-Preservation Verification

The local visual review confirms:

- The site remains unmistakably Evo: black background, gold accents, industrial photography, square-edged restrained controls, existing typography, and the same sticky header/footer vocabulary.
- The homepage did not become a SaaS or consulting template. Capabilities are editorial rows separated by lines, not rounded feature cards or an icon grid.
- The existing hero photograph remains the visual center of the first viewport.
- The commercial position is understandable in the first viewport and early scroll.
- The three domain cards are balanced at desktop, tablet, and mobile widths.
- The homepage remains restrained at five top-level sections and approximately 2.9 desktop screens.
- Projects and SSI remain the destinations for proof and provenance rather than being duplicated on Home.
- Contact, Software, and Energy preserve their established hero and editorial layouts.

Local screenshots are stored outside the repository at:

`C:\Users\cweed\AppData\Local\Temp\evo-commercial-clarity-review-20260915`

Files:

- `home-desktop.png`
- `home-tablet.png`
- `home-mobile.png`
- `contact-desktop.png`
- `contact-mobile.png`
- `software-desktop.png`
- `software-mobile.png`
- `energy-desktop.png`
- `energy-mobile.png`

The persisted mobile captures use a 500 × 844 headless-Chrome viewport because that executable enforces a minimum window width. The responsive implementation was additionally inspected interactively at a true 390 × 844 viewport; it rendered without horizontal overflow and with the expected collapsed navigation.

Screenshots are temporary local review artifacts and are not tracked by Git.

## 9. Lighthouse Results

### Pre-change baseline

| Page | Mode | Performance | Accessibility | Best Practices | SEO |
|---|---:|---:|---:|---:|---:|
| Home | Mobile | 100 | 100 | 100 | 100 |

### Final validation

| Page | Mode | Performance | Accessibility | Best Practices | SEO |
|---|---:|---:|---:|---:|---:|
| Home | Mobile | 100 | 100 | 100 | 100 |
| Home | Desktop | 100 | 100 | 100 | 100 |
| Contact | Mobile | 100 | 100 | 100 | 100 |
| Contact | Desktop | 100 | 100 | 100 | 100 |
| Software | Mobile | 100 | 100 | 100 | 100 |
| Software | Desktop | 100 | 100 | 100 | 100 |
| Energy | Mobile | 100 | 100 | 100 | 100 |
| Energy | Desktop | 100 | 100 | 100 | 100 |

Method: installed Lighthouse CLI against the local static server, default mobile emulation for mobile and Lighthouse desktop preset for desktop, with Performance, Accessibility, Best Practices, and SEO categories enabled.

Tooling note: on this Windows runtime, Lighthouse emitted an `EPERM` warning while trying to delete its temporary Chrome profile after several audits. Each audit had already completed, written a valid JSON report, and produced the scores above. The warning affected temporary cleanup, not the audit result or repository.

## 10. Accessibility Validation

Passed:

- Exactly one H1 on every production page.
- Logical homepage H1 → H2 → H3 hierarchy.
- Primary navigation retains its accessible label.
- Current-page links retain `aria-current="page"` on surviving pages.
- Mobile toggle retains `aria-expanded`, changes its label between Open/Close, and exposes Expand/Collapse state.
- Escape closes the mobile navigation.
- Visible keyboard focus remains present.
- All eight surviving navigation links remain keyboard-accessible.
- Decorative hero images retain empty alt text inside `aria-hidden` pictures.
- Meaningful linked domain images retain descriptive alt text.
- Existing `prefers-reduced-motion` handling remains unchanged.
- New links use descriptive text rather than repeated generic labels.
- No inaccessible form or third-party widget was added.
- External new-tab links continue to use `rel="noopener"`.

Lighthouse Accessibility remained 100 on all eight required audits.

## 11. Responsive Validation

Interactive review covered:

- 1440 × 1000 desktop.
- 820 × 1000 tablet/navigation-collapse width.
- 500 × 844 persisted mobile screenshots.
- 390 × 844 true responsive browser viewport.

At 390px, Home, Contact, Software, and Energy each reported:

- `innerWidth`: 390.
- One H1.
- Visible mobile navigation toggle.
- No horizontal content overflow (`scrollWidth` remained below the full viewport width after scrollbar accounting).

The tablet review confirmed the navigation collapse below 980px and the intended two-plus-centered-one arrangement for the three domain cards. Mobile review confirmed stacked hero actions, one-column capabilities, one-column proof, and one-column domain cards.

No browser console errors or warnings were recorded during the required-page navigation review.

## 12. JSON-LD Validation

Every `application/ld+json` block on all nine source pages parsed successfully after implementation.

Verified preservation:

- Organization `@id`: `https://www.evo.engineering/#organization`.
- WebSite `@id`: `https://www.evo.engineering/#website`.
- Page-specific IDs and URLs.
- `CollectionPage` on Projects.
- `AboutPage` on About.
- `ContactPage` on Contact.
- `WebPage` on Home and domain/legacy pages.

Only descriptive text presenting Finance as an active organization/site domain was revised.

## 13. Broken-Reference Validation

Passed:

- Every local HTML `href` and `src` reference resolves.
- Every `srcset` and `imagesrcset` candidate resolves.
- Every CSS file reference resolves.
- `nav.js` resolves and passes `node --check` syntax validation.
- Every favicon and image reference resolves.
- All surviving internal page links resolve.
- `git diff --check` passes.

The repository contains no `package.json` and no test files or project-specific test runner. There were therefore no additional repository tests to execute.

## 14. Finance Files and Assets Intentionally Retained

Confirmed present:

- `finance.html`
- `images/finance1-400.webp`
- `images/finance1-600.webp`
- `images/finance1-800.webp`
- `images/finance2-hero-600.webp`
- `images/finance2-hero-800.webp`
- `images/finance2-hero-1200.webp`
- `images/finance2-hero-1600.webp`

No Finance asset, historical file, report, research artifact, or source page was deleted.

## 15. Exact Cloudflare Action Still Required

Christopher and Clarity must perform this manually at the coordinated deployment window:

1. Configure exact-path handling for `https://www.evo.engineering/finance.html` to return **HTTP 410 Gone**.
2. Do not redirect the URL to Home, Energy, About, or Software.
3. Do not broaden the rule to Finance image paths or unrelated URLs.
4. Handle another path such as `/finance` only if live verification first proves that it is a real resolving alias.
5. Verify the public response status is 410, not a branded error page returning 200.
6. Verify all surviving canonical URLs return 200 and retain their current canonical tags.
7. Check that cache behavior does not preserve the prior 200 response for `finance.html`.

No speculative Cloudflare dashboard instructions are included because the live account/rule interface was not inspected and was outside scope.

## 16. Deployment Sequence

1. Approve the repository diff and this review.
2. Prepare the production revision, but do not expose it yet.
3. Confirm Christopher/Clarity can activate the exact-path 410 in the same release window.
4. Deploy the repository revision containing the navigation, homepage, metadata/schema, supporting-page, and sitemap changes.
5. Activate the Cloudflare 410 for `/finance.html` in that coordinated window.
6. Verify `/finance.html` returns 410 without redirecting.
7. Verify Home, Projects, About, Energy, Manufacturing, Software, SSI, and Contact return 200 with unchanged canonicals.
8. Verify `robots.txt` remains open and the deployed sitemap omits Finance.
9. Check cache behavior and visual/Lighthouse smoke tests at the public boundary.
10. Begin Search Console monitoring, separating expected Finance deindexing from surviving-page performance.

This review does not authorize any of those deployment or Cloudflare actions.

## 17. Rollback Procedure

Repository rollback and Cloudflare rollback should remain independent.

If the release must be reversed:

1. Revert only this implementation's tracked production-file changes to commit `936f3ac7a8af9a139c95cd615bde946a45dc14dc` or to an approved release commit containing the previous production state.
2. Restore the prior sitemap entry and active Finance navigation/presentation only if the Finance retirement decision itself is being reversed.
3. Christopher/Clarity should disable the exact-path 410 separately if `finance.html` is intended to return as a public 200 page.
4. Purge/check affected cache entries through the authorized operational process.
5. Reverify public status codes, canonicals, sitemap, navigation, Lighthouse, and Search Console behavior.

Because `finance.html` and all Finance assets remain in the repository, rollback does not require reconstructing deleted content.

## 18. Git Status

Baseline before implementation:

- Branch: `main`.
- Commit: `936f3ac7a8af9a139c95cd615bde946a45dc14dc` (`Update Helix Compute project evidence and Evo SEO`).
- Only expected uncommitted artifact: `EVO_COMMERCIAL_CLARITY_PLAN.md`.

Final expected local state:

- Modified production files listed in Section 2.
- Untracked approved plan and implementation review.
- No screenshot files inside the repository.
- No commit created.
- No push performed.
- No deployment performed.

## 19. Remaining Risks

1. **Coordination risk:** the repository sitemap is already staged without Finance while the public 410 does not yet exist. This is correct only for a coordinated deployment; deploying the repository alone would create an inconsistent retirement window.
2. **Live-edge risk:** local validation cannot prove Cloudflare's eventual status code, cache behavior, or response body. Those must be checked publicly by the authorized operator.
3. **Search transition risk:** Finance's limited but nonzero impressions are expected to disappear. Monitor surviving URLs separately so intentional deindexing is not confused with a broader regression.
4. **Visual subjectivity:** the local review found the result restrained and unmistakably Evo, but final stakeholder review should still inspect the supplied screenshots before release approval.
5. **Tooling cleanup warning:** Lighthouse's Windows temp-profile cleanup warning is documented in Section 9; it did not affect scores or repository state.

No unresolved implementation defect was found.

## 20. Recommendation

**APPROVE the local implementation for a coordinated repository + Cloudflare release window.**

The revision makes Evo materially easier to hire while preserving the existing design character, static architecture, Search URL family, accessibility behavior, responsive behavior, social identity, project evidence, SSI provenance, and 100/100/100/100 Lighthouse result.

Do not deploy until Christopher/Clarity have the exact-path HTTP 410 action ready for the same release window. Do not redirect `finance.html` to another current page.
