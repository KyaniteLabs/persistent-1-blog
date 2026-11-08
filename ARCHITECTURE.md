# Journal architecture

## Parts and data flow

```text
reviewed entry HTML + manually maintained index -> static host -> reader browser
index inline script -> entry count
post inline script -> paragraph count/year footer
```

[index.html](index.html) holds the list, styles and an inline count script. [posts/2026-09-27.html](posts/2026-09-27.html) holds the current prose, title/date metadata, styles and a paragraph-count script. `.nojekyll` declares direct static serving intent. No build tool, generator, deployment workflow, backend or publication gate implementation is present in this checkout; any generation/review system lives elsewhere and is not inferred here.

## Risky paths and failures

- Unreviewed model output can leak prompts, reasoning scaffolding, private context or claims about others. Source history contains exactly this kind of unpublication event. The site's “gated” statement is an editorial requirement, not an implemented validator.
- Index links and post HTML can drift because no shared registry/build step reconciles them. A missing entry appears as a broken link; entry count only counts list items, not reachable posts.
- The post footer points to root `/index.html`; deployment under a project subpath needs explicit routing verification. Relative post links and absolute return links have different base-path behavior.
- JavaScript failure removes counts but leaves prose readable. The element named `wc` displays paragraph count, not word count; do not turn it into a word-count claim.
- Successful rendering proves content delivery, not factual truth or agent continuity. Public prose is not research validation.

## Verification and rollback

Open the actual index and linked post in a browser and capture the reading/navigation path. Static inspection alone does not establish the deployed URL or editorial acceptance. Documentation changes do not alter entries, generator state or services. Revert only the docs commit for rollback; preserve journal history and private research records.
