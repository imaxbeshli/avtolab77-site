# Publishing and archives

`gh-pages` serves one self-contained current `index.html` (~7 MB). `preview-r18.html` redirects to it. Other preview routes open lightweight version loaders. These fetch immutable self-contained HTML from the pinned `site-archives` snapshot and verify SHA-256 before rendering.

All originals through v18, including complete ZIP packages, are preserved in `site-archives` at dfd535a1bfd280bf44dcb5b25a2582248e1b448f. Never rewrite that snapshot or historical version tags. `versions/manifest.json` contains original checksums and pinned archive URLs. Old `/versions/AVTOLAB77-vN.zip` paths are redirect directories; the catalogue links directly to the archived ZIP.

For future versions, generate and validate the standalone page and source ZIP, commit/push originals to the archive branch first, verify its remote SHA, then publish only the current index plus lightweight redirects/loaders and manifest records pinned to the new immutable commit. Do not copy historical HTML/ZIP payloads back into gh-pages. Keep its tracked published payload under 12 MB. `scripts/archive-version.py` in source creates full packages; it must be followed by archive storage and slimming before publication.

The prior 208 MB Pages artifact timed out during deploy after 10 minutes. The lightweight artifact is approximately 6.9 MB. This addresses packaging overhead; GitHub's timeout message did not establish a precise backend root cause.
