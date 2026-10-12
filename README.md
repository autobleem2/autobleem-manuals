# autobleem-manuals

The user manuals of **AutoBleem 2**, the game launcher for the PlayStation Classic, a Raspberry Pi, a PC booted
from a USB stick, and Windows. Each manual covers installing the launcher on every platform, everyday use, and
the tools that come with it. The English manual is the master; the other languages are translations of it.

## Languages

One folder per language under `manuals/`, each with one file, `autobleem-user-manual.md`:

| Folder | Language | Folder | Language |
|---|---|---|---|
| `en` | English | `pl` | Polish |
| `cs` | Czech | `pt-br` | Brazilian Portuguese |
| `da` | Danish | `ro` | Romanian |
| `de` | German | `sk` | Slovak |
| `es` | Spanish | `sv` | Swedish |
| `fi` | Finnish | `tr` | Turkish |
| `fr` | French | `zh-cn` | Simplified Chinese |
| `it` | Italian | `nl` | Dutch |
| `oc` | Occitan | | |

## Layout

- `manuals/<lang>/autobleem-user-manual.md` - the source of each manual.
- `manuals/images/<lang>/*.jpg` - screenshots, referenced as `../images/<lang>/<name>.jpg`. Only `en`, `da`,
  `fi` and `pl` have an images folder.
- `manuals/style.css` - the stylesheet of the HTML/PDF.
- `manuals/CHANGES-alpha1.md` - what changed in the English manual for v2.0.0-alpha1, section by section, for translators.
- `tools/build_manuals.py` - the builder. `.github/workflows/build.yml` - CI.

## Source format and building

The sources are a small Markdown dialect, converted by `tools/build_manuals.py` (standard library only):
`#`/`##`/`###` headings (the table of contents is made from `##` and `###`), paragraphs, `-` and `1.` lists,
`**bold**`, `*italic*`, `` `code` ``, links, a line holding only `![caption](path)` (a figure), tables,
`>` notes, code blocks, `---`, and `<!-- pagebreak -->` for a PDF page break.

```
python tools/build_manuals.py            # every language: HTML and PDF into build_manuals/<lang>/
python tools/build_manuals.py --html     # HTML only, no browser needed
python tools/build_manuals.py --lang pl  # one language
```

Output files are named `autobleem-user-manual-<lang>.html` / `.pdf`. The PDF is printed by headless Chrome or
Edge (searched at the usual Windows and Linux paths); without one the PDF is skipped. The footer shows the
version from `git describe --tags --always`.

## Publishing

CI (`.github/workflows/build.yml`, only when the repository variable `AB_CI_ENABLED` is `true`) builds HTML and
PDF on every push and pull request to `develop` or `master` and uploads them as the `manuals` artifact. A push
to `develop`, a `v*` tag, or a manual run from `develop` with *publish* on then copies the PDFs to the manuals
folder of the AutoBleem download site with `repo_publish.sh` from `autobleem2/autobleem-repo`. The English manual
names the site as https://autobleem.retromenele.pl/.

## Adding or fixing a translation

1. Branch from `develop`.
2. Fix: edit `manuals/<lang>/autobleem-user-manual.md`. Keep the English structure - section numbers stay the
   same in every language so cross-references match - and use the language's launcher terms from the launcher's
   `src/resources/lang/<Language>.txt`.
3. New language: copy `manuals/en/autobleem-user-manual.md` to `manuals/<code>/autobleem-user-manual.md`, translate
   it, and add the code with the word for "Contents" to `TOC_TITLE` in `tools/build_manuals.py` (otherwise the
   table of contents says "Contents"). Folders are picked up automatically.
4. Check with `python tools/build_manuals.py --html --lang <code>` and open the HTML.
5. Open a pull request against `develop`; CI builds it, and merging publishes it.

`LICENSE` is the GNU GPL v3 text.
