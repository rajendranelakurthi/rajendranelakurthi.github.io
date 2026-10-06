---
name: portfolio-maintainer
description: Maintain and extend Rajendra Nelakurthi's static GitHub Pages portfolio. Use for changes to this repository's UI, résumé content, company job-duty popups, contact form, social profiles, responsive behavior, or visual design. Do not use for unrelated websites.
---

# Portfolio Maintainer

Maintain this portfolio as a polished, portable static site for a Lead DevOps Engineer. Preserve the established visual language and reusable components unless Rajendra explicitly requests a different direction.

## Project map

- `index.html` owns all page content, experience records, company-specific duty lists, modal behavior, contact form, and social links.
- `css/style.css` contains the legacy theme followed by the authoritative `2026 portfolio visual refresh` overrides. Make new visual refinements in or after that override section unless changing a legacy rule is clearly safer.
- `img/` contains the site's local imagery. Prefer existing local assets over introducing runtime dependencies.
- The site is plain HTML, CSS, and JavaScript with Bootstrap 3 and Font Awesome 4. It has no package installation or build step.

Resolve paths relative to the repository root. Do not depend on a specific username, home directory, editor, or operating system.

## Established design system

Keep the site professional, modern, and DevOps-focused:

- Deep navy surfaces, electric cyan primary accents, restrained amber highlights, light neutral content backgrounds.
- Manrope for body copy and Space Grotesk for headings and navigation.
- Glass-style top navigation, high-contrast hero, responsive experience cards, compact skill chips, and softly elevated content surfaces.
- Smooth but restrained transitions. Respect `prefers-reduced-motion` and avoid animation that delays access to content.
- Use rounded corners consistently. Maintain readable contrast, visible keyboard focus, responsive layouts, and touch-friendly controls.
- Avoid model-generated SVG decoration, heavy UI frameworks, or new dependencies for small visual changes.

When adjusting styling, verify both existing legacy rules and later overrides. A later override is usually preferable because it lowers regression risk.

## Experience and job duties

Each company owns independent hidden duties and tech-stack lists after its `View job duties` button:

```html
<button class="job-duties-trigger" data-duties="duties-company" data-stack="stack-company">...</button>
<ul id="duties-company" class="job-duties-source" hidden>
    <li>Company-specific responsibility or achievement.</li>
</ul>
<ul id="stack-company" class="job-duties-source" hidden>
    <li><span class="tech-logo" aria-hidden="true"><img src="img/tools/tool.svg" alt="" width="32" height="32"></span><span>Tool name</span></li>
</ul>
```

The shared popup copies the selected duties into `#jobDutiesList` and tools into `#jobTechStackList`. Show roles and responsibilities on the left and the tech stack on the right; stack these sections on smaller screens. Never put company content directly into the shared modal or reuse one company's lists for another.

When editing duties:

- Preserve the user's technical meaning while improving grammar, capitalization, and résumé readability.
- Start bullets with strong past-tense action verbs for previous roles and appropriate present tense for the current role.
- Keep named technologies accurate and consistently capitalized.
- Preserve quantified outcomes and consolidate only true duplicates.
- Allow any number of list items; long lists must remain comfortably scrollable in the popup.

## Company tech-stack updates

- Whenever Rajendra adds a technology to any company/project tech stack, include its logo in the same change without requiring a separate logo request.
- Reuse local assets in `img/tools/` first. For missing logos, obtain authentic product logos from official sources or established collections such as Devicon, Simple Icons, or Dashboard Icons; save them locally and record the source in `img/tools/SOURCES.md`.
- Keep visible tool names beside decorative logos (`alt=""` within `aria-hidden="true"`), preserve logo proportions, and verify each new image reference and SVG/PNG file.
- For generic categories such as LLM, use an appropriate neutral icon from the existing icon library. Do not imply use of a specific vendor. If a product logo cannot be obtained, use a readable fallback and disclose the limitation.
- Add tools only to the requested company's hidden stack list; preserve existing tools and duties unless instructed otherwise.

## Social and contact behavior

- Keep GitHub, Devfolio, LinkedIn, and Twitter together in `.social-list` with matching circular sizing, visual weight, spacing, and vertical alignment.
- Devfolio uses `https://devfolio.co/@rajendranelakur`. Its supplied avatar requires the existing color normalization and alignment rules in `.devfolio-social`.
- LinkedIn uses `https://www.linkedin.com/in/rajendranelakurthi/` and should remain available both in the social row and as the prominent contact action.
- External links open in a new tab and should include `rel="noopener noreferrer"` when touched.
- Keep explicit, visible form labels, readable placeholder contrast, clear focus states, and the existing Formspree submission behavior.
- Preserve enough of the contact background image to remain recognizable; do not use an opaque or near-opaque overlay.

## Interaction requirements

The job-duty popup must continue to support:

- Company-specific title, role, dates, and duties.
- Smooth open and close transitions.
- Close button, backdrop click, and Escape key.
- Initial focus, keyboard focus containment, and focus restoration to the triggering button.
- Body scroll lock while open and reduced-motion behavior.

Do not replace the reusable popup with six duplicated modals.

## Safe editing workflow

1. Inspect the smallest relevant portion of `index.html` and `css/style.css` before editing.
2. Preserve existing company duties and user-authored content unless the request explicitly changes them.
3. Make focused changes without introducing a build system or dependency installation.
4. Run `git diff --check` and parse `index.html` after edits. Also inspect the changed selectors and markup with `rg`.
5. Do not publish, push, or deploy unless Rajendra explicitly asks.

Use this portable HTML validation command from the repository root:

```sh
python3 -c "from html.parser import HTMLParser; HTMLParser().feed(open('index.html', encoding='utf-8').read()); print('HTML parsed successfully')"
```

If Python is unavailable, use another installed HTML-aware validator or document the skipped check; do not install tooling solely for this validation.

## Portability and fresh-machine use

This skill travels with the repository under `.agents/skills/portfolio-maintainer`. On another machine:

1. Clone the repository and open its root folder in Codex.
2. The repository-scoped skill should be discovered automatically. Invoke `$portfolio-maintainer` explicitly if needed.
3. Open `index.html` directly or serve the repository root with any simple static HTTP server for local preview.

Do not encode machine-specific absolute paths in site code or future skill instructions. Git-tracked site assets and this skill are the complete project handoff.
