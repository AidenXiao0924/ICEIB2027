# ICEIB2027 — DietSense

IEEE conference draft: **A Data-Grounded Conversational AI Agent for Integrated Home Environment Assessment and Outdoor Activity Recommendations**.

The manuscript proposes a single-room ESP32/MQTT sensing system, SQLite records, Python analysis, CWA forecasts and evidence-grounded conversational advice. The two-week pilot and classifier comparisons are planned, not completed.

## Layout

- `main.tex`: IEEEtran preamble, author fields and section inputs.
- `sections/`: abstract, introduction, related work, proposed scheme, planned experiments and conclusion.
- `references.bib`: bibliography transcribed from the prior draft.
- `figures/`: original TikZ architecture and query-flow drawings.
- `tables/`: prior-work comparison and planned metrics.
- `../openspec/`: proposed research-system requirements and evaluation change.

## Build

In Overleaf upload the contents of this directory (not the repository root), select main.tex and pdfLaTeX, and recompile. Locally use `latexmk -pdf main.tex` with IEEEtran, TikZ, algorithm and other preamble packages installed. BibTeX is required. Replace author placeholders and verify references before final submission.

## OpenSpec

The change `define-evidence-grounded-agent` records the proposed system and pilot requirements. With the official OpenSpec CLI installed, from the repository root run `openspec validate define-evidence-grounded-agent --strict`. CLI validation and implementation are pending; the documents do not establish experimental results.

## Version control

The local Antigravity Git MCP was tested with git_status and git_log. Review changes before committing and pushing. Overleaf free-plan synchronization is manual. Do not commit credentials.

Conference: https://www.iceib.asia/  
IEEE templates: https://www.ieee.org/conferences/publishing/templates.html
