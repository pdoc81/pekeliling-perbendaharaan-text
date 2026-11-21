# Pekeliling Perbendaharaan — extracted text

Full text of the Arahan Perbendaharaan (AP, Pindaan 2023, with its amendment notices) and of every **current** Pekeliling Perbendaharaan on the [Portal Pekeliling Perbendaharaan](https://ppp.treasury.gov.my/), extracted to searchable Markdown. It is the ready-made database for the **Ijah** agent in [mof-writing-crew](https://github.com/pdoc81/mof-writing-crew), so you don't need to download and OCR everything yourself.

**Snapshot:** 2026-11-21 · 268 documents · 7,656 pages (1,001 of them OCR'd from scans)

| Bidang | Docs |
|---|---|
| AP — Arahan Perbendaharaan | 16 |
| PB — Pengurusan Belanjawan | 16 |
| PK — Perolehan Kerajaan | 93 |
| WP — Pengurusan Wang Awam | 55 |
| AM — Pengurusan Aset | 57 |
| PS — Tadbir Urus Kewangan | 25 |
| PA — Pelaburan Strategik | 5 |
| LB — Syarikat Tersenarai Bumiputera | 1 |

The Arkib (archived circulars) is not included.

## Layout

- `text/<KOD> - <Bidang>/<NN - Topik>/<NN - Tajuk>.md` follows the portal's own bidang → topic order. Topic `00` is Surat Edaran / Makluman Terkini. The AP comes from [mof.gov.my](https://www.mof.gov.my/portal/ms/arahan-perbendaharaan).
- Each file starts with front matter: `bidang`, `topic`, `title`, `source_url` (the official PDF), `pdf` (relative path if you download the PDFs), `sha256` of the source PDF, `pages`, `ocr_pages`, `extracted_at`.
- Each page begins with `<!-- page N (text) -->` or `<!-- page N (ocr) -->`, so you can cite page numbers. Tables from scanned pages are HTML tables.
- `manifest.json` lists every document with its official URL, sha256 and download time.

## Accuracy

- `(text)` pages come from the PDF's own text layer via `pdftotext`.
- `(ocr)` pages were read by PaddleOCR (PP-StructureV3, run locally). Spot checks show figures and dates are reliable, but small typos happen. **Before relying on a number from an `(ocr)` page, check it against the official PDF** at `source_url`. Ijah does this automatically.
- A circular being here does not mean every paragraph is still in force. Later Surat Edaran may amend or cancel parts. Ijah checks this; if you search by hand, check too.

## Use with mof-writing-crew (Ijah)

```bash
git clone https://github.com/pdoc81/pekeliling-perbendaharaan-text.git ~/Pekeliling
```

Then replace `<PEKELILING_FOLDER>` with that path in Ijah and the `pekeliling-perbendaharaan-lookup` skill. See the [mof-writing-crew README](https://github.com/pdoc81/mof-writing-crew#required-one-time-setup-for-ijah-get-the-pekeliling-database). Run `git pull` to get newer snapshots. Ijah keeps its decision log in this folder; it is git-ignored, so it never gets committed.

## Updating

Snapshots are rebuilt with the free, local pipeline in [mof-writing-crew/tools](https://github.com/pdoc81/mof-writing-crew/tree/master/tools) (pdftotext + PaddleOCR). Each refresh is one commit, so `git log -p` / `git diff` shows which circulars were added, amended or withdrawn between snapshots.

## Disclaimer and copyright

- **Unofficial.** This is not affiliated with or endorsed by the Ministry of Finance Malaysia. The official, authoritative versions are the PDFs at ppp.treasury.gov.my and mof.gov.my. Always cite and verify against them.
- The circulars and the Arahan Perbendaharaan are works of the Government of Malaysia and remain its copyright. This text is reproduced from publicly available official sources for reference and search only, with a link to the original for every document. Rights holders who want anything removed can open an issue.
- Extraction errors are possible. No warranty of accuracy or completeness.
