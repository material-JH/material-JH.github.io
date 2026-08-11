# Website Sync Notes

This is a clone of `github.com/material-JH/material-JH.github.io` (GitHub Pages, served at
https://material-jh.github.io/). Pushes use the machine's authenticated `gh`/`git` (account
`material-JH`, `repo` scope).

## What's maintained here

- `index.html` — the live page. Its `<ol class="pubs">` block should always match the "Under
  review" + "Accepted/in press" + "Published" ordering used in
  `../CV/Jinho_Byun_CV.md` / `../Publications_Master_List.md`.
- `assets/Jinho_Byun_CV.pdf` — generated from `cv_source.html` (NOT hand-edited; it is a plain
  print-styled HTML rebuild of `../CV/Jinho_Byun_CV.md`, not an edit of the original binary
  `CV_JH.doc` — LibreOffice/Word automation isn't available on this machine, so the original
  Word-formatted CV in `C:\Users\woal7\SynologyeM3\Documents\CV_JH.doc` was not touched).
- `cv_source.html` — the print source. Regenerate the PDF after editing it:
  ```
  browser.open(url="file:///.../website/cv_source.html")
  browser.run(code="""
    const buf = await page.pdf({ format: 'A4', printBackground: true,
      margin: { top:'0mm', bottom:'0mm', left:'0mm', right:'0mm' } });
    require('fs').writeFileSync('.../website/assets/Jinho_Byun_CV.pdf', buf);
  """)
  ```
  Then `git add -A && git commit && git push`.

## 2026-08-11 sync (this session)

Updated both `index.html` and `cv_source.html`/`Jinho_Byun_CV.pdf` to add/correct:
- JACS paper → **accepted, in production** (was previously not listed as accepted).
- BTO-FTJ Science Advances (aeh5401) paper → **added** (was missing from the site entirely).
- BST Science Advances (aef1528) paper → wording kept as "under review, major revision" (was
  already "under review" but now explicitly flags the Round-2 status).
- BCFO/Advanced Functional Materials paper (7502704) → **added** ("under review, second round",
  per direct confirmation from the site owner — not independently re-verified against the
  submission portal).
- Nature Physics paper → left as "under review" (status not reverified this session — carried
  forward from the prior CV/site text as-is).
- 2 new 2026 Google Scholar-confirmed papers (IEEE TCAS-I first-author; Advanced Intelligent
  Systems) added to the published list; corrected two year mismatches (Adv. Mater. Interfaces
  2101647 and ACS Nano 894–903 were mislabeled 2021/2018 on the old site — corrected to 2022/2019
  to match the journal-indexed volume/issue year).
- Fixed a pre-existing content error: the old site listed "Highly efficient top-down processed
  blue InGaN nanoscale light-emitting diodes" under venue "Nature" — that title belongs to a
  separate 2021 record with no assigned venue; the actual *Nature* 608, 56–61 (2022) paper has a
  different (shorter) title, now corrected.

See `../Papers_Status_Tracker.md` for full evidence behind every forthcoming-paper status claim.
