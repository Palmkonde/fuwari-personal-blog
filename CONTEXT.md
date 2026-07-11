# Fuwari Personal Blog

A personal blog built on the Fuwari Astro theme, deployed as a static site to Cloudflare Pages.

## Language

**Post**:
A single article, stored as a content entry in the `posts` collection (`src/content/config.ts`).

**Draft**:
A **Post** with `draft: true`. Visible during local dev (`pnpm dev`), excluded from the production build (`pnpm build`) — see `src/utils/content-utils.ts`.
_Avoid_: "unpublished" (the schema's actual field is `draft`, not a publish-state flag).

**Category**:
The single broad bucket a **Post** belongs to (e.g. "Tech", "Life"). One per post, optional.
_Avoid_: using it interchangeably with Tags.

**Tags**:
The specific keywords attached to a **Post**, any number per post. Drives search/related-post surfacing.
_Avoid_: using it interchangeably with Category.

**Site language**:
`siteConfig.lang` in `src/config.ts` — controls the UI chrome (nav labels, "Tags", "Archive", etc). Set to `en`.
_Avoid_: confusing with Post language below — these are independent settings.

**Post language**:
The per-post frontmatter `lang` field. Overrides the site language for that post's content when it differs from the site default (this blog is bilingual: EN default, individual Thai posts set `lang: "th"`).

## Relationships

- A **Post** belongs to at most one **Category**, and any number of **Tags**
- A **Draft** is a **Post** state, not a separate content type
- **Site language** is one global setting; **Post language** is an optional per-post override

## Flagged ambiguities

- "category" vs "tags" were initially unclear as interchangeable groupings — resolved: Category is a single broad bucket per post, Tags are the specific/multiple keywords.
- "language" was ambiguous between UI chrome and content — resolved: Site language (UI chrome, global) and Post language (per-post content override) are separate settings.
