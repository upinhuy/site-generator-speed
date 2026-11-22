# Site generator, faster

[![bounty](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/upinhuy/site-generator-speed/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/upinhuy/site-generator-speed/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)

A faster drop-in for make.fun's own makefun-site 1.0.0, for the make.fun
bounty "Build a static site faster, 22 November 2026". One Node 22 program,
`main.ts`, reads every case from `/input/cases.json` and answers each with
`run` from `solve.js`, writing `/output/answers.json`.

`solve.js` re-implements makefun-site's own front matter, template dialect,
Markdown subset, slug rule and report from scratch in one pass, and returns
the same output tree byte for byte: every page's `index.html`, the index and
tag pages, `build-report.txt` and each static file. The speed comes from bulk
escaping instead of per-character work, `indexOf` scans instead of regexes on
the hot paths, direct block rendering without a token array, per-case caches
for slugs and long dates, and one output array per template render joined
once at the end.

Try make.fun: https://make.fun/r/hv9zk8y5
