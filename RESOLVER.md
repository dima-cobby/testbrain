# Brain Resolver — Master Decision Tree

Before creating any new page, walk this decision tree. Every piece of knowledge has exactly one home.

## Decision Tree

**Start here: what is the primary subject?**

1. **A specific named person** → `people/`
2. **A specific organization** (company, fund, nonprofit, government body) → `companies/`
3. **A financial transaction** with terms and a decision to make → `deals/`
4. **A record of a specific meeting/call** that happened at a specific time → `meetings/`
5. **Something being actively built** (has a repo, spec, team, or active work) → `projects/`
6. **A raw possibility** that nobody is building yet → `ideas/`
7. **A reusable mental model or thesis** about how the world works → `concepts/`
8. **A piece of prose** that could be published as a standalone work → `writing/`
9. **Your institution's strategy, org, processes, internal dynamics** → `org/`
10. **Political or civic landscape** — policy, legislation, elections, government → `civic/`
11. **Public narrative or content operations** — social monitoring, content pipeline → `media/`
12. **A major life program** — an enduring domain of commitment → `programs/`
13. **Domestic operations** — properties, logistics, household management → `household/`
14. **Private notes** — health, personal reflections, inner life → `personal/`
15. **A hiring pipeline** — candidate evaluations, role specs → `hiring/`
16. **A reusable LLM prompt** → `prompts/`
17. **A raw data import or snapshot** → `sources/`
18. **Agent deliverables** — briefings, digests, research → `agent/`
19. **Unsorted / quick capture** → `inbox/`
20. **Dead / no longer relevant** → `archive/`

## Disambiguation Rules

- **Person vs. Company:** About *them as a human* → people/. About *the organization* → companies/.
- **Concept vs. Idea:** Could you *teach* it? → concept. Could you *build* it? → idea.
- **Concept vs. Personal:** Would you share it professionally? → concept. Private reflection? → personal.
- **Idea vs. Project:** Is anyone working on it? Yes → project. No → idea.
- **Writing vs. Concepts:** Distilled framework (200 words) → concept. Developed prose → writing.
- **Writing vs. Media:** The *artifact* → writing. The *distribution infrastructure* → media.
- **Household vs. Personal:** PA would execute on it → household. Private reflection → personal.
- **Sources vs. .raw/ sidecars:** Per-entity enrichment → .raw/. Bulk imports → sources/.
