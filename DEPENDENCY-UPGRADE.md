# Dependency upgrade and staging plan

Production branch: master. Test branch: staging/dependency-upgrade.

## Baseline

This documentation-only commit establishes a Netlify Deploy Preview with the existing site and dependency versions. Do not merge until testing is complete.

- Hugo: 0.75.1 in netlify.toml.
- Node: 12.18.0 in Netlify settings.
- Wowchemy and netlify-cms-academic: October 2020 revision be0fa17ac006.
- go.mod declares Go 1.15; verify the actual build toolchain in logs.

## Sequence

1. Build the baseline preview. Record build errors and representative page screenshots.
2. Test supported Node LTS in preview only, keeping Hugo and theme fixed.
3. Migrate theme and Hugo together, pinning compatible versions. Preserve publication URLs and citation files.
4. Check whether the legacy CMS is used before replacing or removing it.
5. Apply the October 2026 CV content updates after the dependency build is stable.

## Acceptance checks

- Clean build and repeat build pass.
- Home, biography, publications, talks, contact, and CV download work.
- Navigation, search, citations, images, CSS, and JavaScript load.
- Desktop and mobile layouts reviewed; browser console checked.
- Internal links and canonical URLs use the intended deployment hostname.
- Preview remains excluded from search indexing.
- Production is published only after review and merge to master.
