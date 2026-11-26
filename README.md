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

ratmath.com/shelf is served by its own repository,
[ratmath/shelf](https://github.com/ratmath/shelf) (GitHub Pages from `main`,
`/docs`), which also holds the `ratmath` npm package. Edit the Shelf page there.
