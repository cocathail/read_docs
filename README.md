# ENA Documentation – Structural Improvements

This branch contains a set of structural improvements to the ENA documentation source.
The only net-new content is the quickstart guide; all other changes are editorial and organisational.

## What changed and why

### Build configuration (`conf.py`)
- Added `numfig = True` so figures are automatically numbered in the built docs
- Added `venv/` and `requirements.txt` to the ignore list so the local Python environment no longer generates spurious build warnings
- Removed several blocks of commented-out legacy code that had accumulated over the years (old sidebar variants, old theme options, an old Markdown parser block)
- Added a comment above the file-format setting clarifying that RST is preferred for new files and Markdown is accepted for externally contributed content

### Housekeeping
- Created empty `_static/` and `_templates/` directories (with `.gitkeep` files) — these are referenced in `conf.py` and their absence was causing build warnings
- Deleted `exp_01.md` — a stray RNA-Seq draft at the project root with no table-of-contents entry and no links pointing to it; its content is superseded by existing guidance under `submit/reads/`

### Anchor labels for internal linking
Added named reference labels (`:ref:`) to 11 section headings across four files so that other pages can link directly to those sections rather than to the top of the page:
- `faq/taxonomy.rst` — labels for the taxonomy selection guide, submittability check, binomial check, environmental taxonomy overview, biome-level taxonomy, and organism-level taxonomy sections
- `submit/samples.rst` — labels for the Checklists, Taxonomy, and Accessions sections
- `submit/reads.rst` — label for the Submission Options section
- `update/metadata.rst` — label for the page title

### Internal link cleanup (~53 files)
All internal links that used raw HTML paths (e.g. `` `Some page <../other/page.html>`_ ``) have been converted to proper Sphinx cross-references:
- Links to whole pages use `` :doc:`Title </path/to/page>` ``
- Links to specific sections (where a label exists) use `` :ref:`Title <label-name>` ``
- Several pre-existing broken or malformed paths were also corrected as part of this pass (wrong number of `../` steps, a link pointing outside the docs root, absolute paths missing the `submit/` prefix)
- Fixed a broken link in `submit/samples.rst` pointing to `sample_checklist_errors.md` — raw `.md` paths are not resolved by Sphinx and produced a 404; converted to a `:doc:` reference

### Admonitions (14 blocks across 8 files)
Pieces of important advice that were buried in regular prose have been promoted to clearly styled callout blocks. Warnings are things that can cause errors or data loss; tips are helpful reminders.

**`update/assembly.rst`**
- Warning — SARS-CoV-2 assembly updates are not versioned and produce new accessions (previously a footnote in italic asterisk notation)
- Warning — Webin-CLI does not validate chromosome names; errors are only caught after submission
- Warning — Annotation cannot be added to a previously unannotated assembly; re-submission and new accessions are required
- Tip — Assembly processing after submission can take up to a week to be visible
- Warning — Submit updates at least 24 hours after the original submission to avoid processing issues

**`submit/assembly.rst`**
- Tip — It is strongly recommended to also submit any raw reads associated with the assembly
- Note — The term "chromosome" covers all complete replicons (prokaryotic, viral, organellar, plasmid)
- Warning — You cannot update to a lower assembly level, and you cannot add annotation if none was present originally

**`submit/sequence.rst`**
- Warning — The ERZ accession assigned at submission is for internal use only and should not be cited in publications

**`submit/samples.rst`**
- Warning — The ENA default sample checklist should only be used if advised to do so; a more specific checklist should always be preferred

**`faq/taxonomy.rst`**
- Tip — New metagenome taxonomic records are rarely added; use the closest available option rather than requesting a new one

**`faq/release.rst`**
- Tip — After release, data can take up to 48 hours to appear in the ENA Browser and four days to appear in GenBank
- Warning — Data that is made public even briefly may be picked up by downstream services outside ENA's control

**`update/metadata.rst`**
- Warning — Not all object attributes can be updated; controlled vocabularies apply to updates just as they do to original submissions

### New page: first-submission quickstart guide (`submit/quickstart.rst`)
The existing documentation is organised around submission object types (study, sample, reads, assembly), which works well as a reference but assumes the reader already knows what they need to submit. A new quickstart page has been added as the first entry in the submission section, aimed at users who have never submitted to ENA before.

The page is structured around four common scenarios:
- **Raw sequencing reads** — the most common case; walks through registering a study and samples then submitting read files
- **Genome assembly** — includes a reminder to also submit the underlying reads and notes that Webin-CLI is required
- **Targeted sequences** (e.g. 16S rRNA, COI, ITS) — clarifies this route is for short annotated sequences only, not whole-genome assemblies
- **Metagenomic data** — outlines the assembly hierarchy and links to the metagenome FAQ

Each scenario lists what is needed, the steps in order, and links through to the relevant existing detail pages. No existing content has been moved or rewritten.

### Retrieval section cleanup (`retrieval/`)
The data retrieval section has been reorganised for clarity:
- Removed two "Downloading Private Files" subsections from `retrieval/file-download.rst` (one under the curl method, one under Aspera) — private data access via datahub is not a supported public workflow
- Removed the ascli private-file configuration example from the Aspera ascli subsection for the same reason
- Added a "which method should I use?" summary table at the top of the download methods page so users can quickly pick the right tool
- Added `curl` as a proper list entry (it was missing from the method index despite having its own section)
- Formatted the bare `curl` command as a proper RST code block
- Fixed a blank-line formatting gap before the "Common Issues" heading in the ascli section
- Fixed a typo (`foraccessing` → `for accessing`) in `retrieval/general-guide.rst`
- Converted a stale raw HTML link in `retrieval/advanced-search.rst` to a proper `:doc:` reference
- Removed the duplicate `retrieval/ena-project` entry from the top-level `index.rst` toctree (the page is already included via `retrieval/general-guide.rst`)

## Note on redirects
One redirect cannot be configured in code and must be set manually in the ReadTheDocs web admin under **Admin → Redirects**:
- `/faq/missing-values` → `/submit/samples/missing-values`
