# Change Log

## [2.1] - 2026-05-23

### Added

- Added selectable homepage card styles through `params.homepage.<section>.card_style`:

  ```toml
  [params.homepage.research]
    layout = "cards"
    card_style = "academic" # Options: "badge" or "academic"

  [params.homepage.builds]
    layout = "cards"
    card_style = "badge"
  ```

- Added the `academic` card style for publication-like Research and Builds sections. Academic cards place date/year, collaborators, and links directly under the title as text metadata.
- Kept the original rounded-chip card treatment available as `card_style = "badge"`.
- Documented card style options and coauthor label behavior in `README.md`.
- Added a global color palette toggle through `params.color_palette`:

  ```toml
  [params]
    color_palette = "academic" # Options: "academic" or "morandi"
  ```

- Added the `academic` color palette, which pairs softer watercolor-style news badges with muted clay-rose profile keyword badges in dark mode.

### Changed

- Changed `coauthors_label`/`coauthorsLabel` rendering so labels are output exactly as written. The theme no longer appends a colon automatically, which allows labels like `with`.
- Moved links above the hover-expanded summary in `academic` cards so paper/preprint targets remain stable while summaries expand.
- Darkened academic card metadata in light mode for better readability, including dates, coauthor labels, coauthor names, inline links, and separators.
- Changed news badge styling to follow the global `color_palette` setting instead of a news-only badge palette option.

## [2.0] - 2026-05-22

### Added

- Added configurable homepage news/update item count through `params.homepage.news.limit` in `hugo.toml`.
- Documented the news/update `limit` option in `README.md`.
- Added selectable profile image styles through `data/profile.yaml`:

  ```yaml
  profile_layout: "modern" # Options: "modern" or "classic"
  profile_image_style: "circle" # Options: "circle" or "rectangle"
  ```

- Added `classic` profile layout support, restoring the original Celadon two-column grid hero for users who prefer the earlier rectangle-image layout.
- Added `list` profile highlights for the original bullet-style highlight UI, including coexistence with `keyword_sections`.
- Added support for profile keyword badge sections through `data/profile.yaml`:

  ```yaml
  keyword_sections:
    - title: "Research Areas & Interests"
      rows:
        - ["Behavioral Economics", "Social Networks"]
    - title: "Methods"
      rows:
        - ["Causal Inference", "Machine Learning"]
  ```

- Added fallback rendering for older profile formats:
  - `highlights_title` + `keyword_rows`
  - `keywords`
  - `highlights`

### Changed

- Reworked the profile hero layout so the identity block, portrait, summary, keyword sections, and links render as separate parts instead of one long two-column block.
- Updated the profile image styling for circular portrait images:
  - circular frame
  - stable square aspect ratio
  - alpha-friendly drop shadow
  - desktop float positioning
  - mobile reset behavior
- Tuned profile hero spacing and typography:
  - smaller profile heading
  - tighter title/affiliation spacing
  - more compact spacing before the summary
  - adjustable portrait offset using `transform`
- Changed profile interests from bullet-list style highlights to inline keyword badges.

### Fixed

- Fixed YAML paragraph spacing in `data/profile.yaml` by using a literal multiline summary block.
- Fixed invalid YAML caused by adjacent quoted highlight strings.
- Fixed profile rendering issues with circular transparent PNG portraits.
- Fixed a minified CSS issue caused by `grid-template-columns: minmax(0, 1fr) 240px` being compressed into invalid CSS.
- Fixed Vercel build setup by ensuring `${HOME}/.local` exists before extracting downloaded tools and using `mkdir -p` for the Hugo install directory.

### Notes

- Theme changes were made on the Celadon submodule branch `profile-layout-update`.
- The parent site tracks a specific Celadon submodule commit, so deployment requires that the referenced submodule commit is pushed and fetchable by the deployment environment.
- The homepage update count can be changed with:

  ```toml
  [params.homepage.news]
    limit = 5
  ```
