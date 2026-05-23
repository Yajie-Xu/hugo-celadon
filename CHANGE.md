# Change Log

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
