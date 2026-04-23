# Brain Schema

## Page Structure (Two-Layer)

Every page has two layers separated by `---`:

**Above the line — Compiled Truth.** Always current, rewritten when new info arrives. Starts with executive summary.

**Below the line — Timeline.** Append-only, reverse-chronological evidence log. Each entry: date, source, what happened.

## Canonical Slugs

- People: `first-last.md` (lowercase, hyphens)
- Companies: `company-name.md`
- Disambiguate with context: `david-liu-crustdata.md`

## Frontmatter

Use YAML frontmatter for structured/queryable metadata (role, company, stage, tags, aliases).

## Cross-References

Use `[[slug]]` wiki-links. Every entity mention should link to its page.

## Aliases

```yaml
aliases: ["Name Variant", "email@example.com", "@handle"]
```

## Before Creating Any Page

1. Search existing pages by name (exact + fuzzy)
2. Search aliases across all pages
3. Check .raw/ for matching identifiers
4. Match found → UPDATE existing page
5. No match → CREATE new page via RESOLVER.md
