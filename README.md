# ratmath.com

The RatMath landing page: what RatMath is, and which address serves what
(rix.ratmath.com, docs.rix.ratmath.com, calc.ratmath.com, core.ratmath.com,
worlds.ratmath.com). One static `index.html`, no build step.

Served by GitHub Pages from the `main` branch root of `ratmath/ratmath.github.io`,
with the custom domain in `CNAME`.

## Shared assets

`assets/katex/<version>/` holds one pinned copy of [KaTeX](https://katex.org)
(MIT, license alongside) for every library docs site under ratmath.com
(`/core`, `/analytic`, `/linalg`, `/algebraic`, ...). The sites render their
math to HTML when they are built, so a page loads only
`/assets/katex/0.19.1/katex.min.css` and the fonts it names. `katex.min.js`
and `katex.mjs` are there for pages that typeset at run time (the runnable
code boxes load them only when a result asks for math).

Never change files in a published version folder: browsers cache them. To
upgrade, add a new version folder, point the docs builds at it, and keep the
old folder until no page uses it. The landing page prefetches the stylesheet
and two fonts so the docs open with them cached.

## The RatMath Shelf page

`shelf/index.html` (ratmath.com/shelf) lists the subject libraries built on
Core. "On the shelf" has one `<article class="pkg">` per library and one
`<li>` per topic, each linking to that topic's documentation page. "Planned"
mirrors the roadmap in `ratmath/ratmath` (`docs/design/library-roadmap.md`).

When a planned topic is built and its documentation page exists, move it: add
its `<li>` with the link under "On the shelf" (adding the library's article if
it is the library's first topic), and remove it from "Planned" here and from
the roadmap. A topic is never listed as available before its page is live.
The page carries its own copy of the landing page's styles; there is still no
build step.
