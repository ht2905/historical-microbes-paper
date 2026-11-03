# Microbes as Agents of Change: Historical, Cultural, and Astrobiological Perspectives

This repository contains the Quarto source code, reference database, and supporting assets for an academic review paper prepared for the Microbiology (BT321IU) course at the School of Biotechnology, International University - Vietnam National University Ho Chi Minh City (VNU-HCM).

The manuscript was typeset using the Elsevier Quarto Journal template for publication-grade formatting, two-column layout, figure integration, and reference management.

---

## Quick Access: Reading the Paper

If your primary goal is to read the paper rather than recompile it, you do not need to install any programming tools:

- [historical_microbes.pdf](historical_microbes.pdf): The complete, pre-rendered 17-page manuscript in Elsevier double-column layout.
- [cover_page_for_assignments.pdf](cover_page_for_assignments.pdf): The official university submission cover sheet.

---

## Project Overview

Microorganisms are conventionally introduced in wet-lab curricula primarily as laboratory tools (such as *Escherichia coli* cloning hosts) or as causative agents of disease. This review argues for microbial agency—the perspective that biological properties of microbes (such as transmission kinetics, metabolic versatility, and extreme environmental tolerance) actively shape human demographic history, cultural materials, and scientific boundaries.

### Manuscript Content

| Section | Title | Primary Focus |
|---|---|---|
| Section 1 | Introduction | Ubiquity of microbial life, planetary biomass, and the microbial agency framework. |
| Section 2 | Microbes that Changed History | Demographic and socio-economic collapses driven by *Yersinia pestis* (Black Death) and *Variola major* (smallpox); the foundation of immunology via variolation and Jennerian vaccination. |
| Section 3 | Famous Microbiologists and Groundbreaking Discoveries | Foundational methodologies: Pasteur (germ theory, pasteurization, rabies/anthrax vaccination), Koch (Koch's postulates and pure culture isolation), and Fleming (serendipitous discovery of penicillin and the antibiotic era). |
| Section 4 | Microbes in Art and Culture | Living microbial art (agar bio-art using *Chromobacterium violaceum* and *Serratia marcescens*) and sustainable textile dyeing using microbial and fungal pigments. |
| Section 5 | Bacteria in Space (Astromicrobiology) | Extremophile physiology (*Deinococcus radiodurans*), low Earth orbit exposure facilities (EXPOSE-E, ADAPT), panspermia hypotheses, and COSPAR planetary protection. |
| Appendix A | Supplementary Figures | Additional high-resolution micrographs and textile pigment dye assays. |

---

## Repository Structure

| File or Directory | Purpose | Description |
|---|---|---|
| `historical_microbes.pdf` | Final Document | Ready-to-read pre-compiled PDF manuscript. |
| `historical_microbes.qmd` | Manuscript Source | Main Quarto Markdown file containing the text, frontmatter metadata, and structure. |
| `cover_page_for_assignments.pdf` | Submission Document | Assignment submission cover page for the BT321IU course. |
| `bibliography.bib` | Literature Database | BibTeX bibliography containing all cited academic references. |
| `preamble.tex` | LaTeX Formatting | Custom LaTeX header commands managing URL wrapping, float placement, and table formatting. |
| `_quarto.yml` | Project Settings | Quarto project configuration file. |
| `historical_microbes.Rproj` | RStudio Project | Project definition file for RStudio Desktop. |
| `photos/` | Figures and Assets | High-resolution diagrams, photos, and schematics included in the manuscript. |
| `renv.lock` | Environment Lockfile | Exact dependency manifest recording package versions for reproducible builds. |
| `renv/` | Environment Tools | Scripts (`activate.R`) and settings enabling automatic `renv` restoration. |

---

## Step-by-Step Reproduction Guide

This guide is designed for wet-lab scientists and researchers who want to inspect, modify, or re-render the paper on their own computer.

### Conceptual Prerequisites

Rendering this paper from source requires four components working in harmony:

1. **R (version 4.2 or later):** The computational environment.
2. **Quarto CLI:** The scientific publishing system that translates Quarto Markdown (`.qmd`) into formatted outputs.
3. **Elsevier Quarto Template:** A document extension providing Elsevier's `elsarticle` formatting and citation styles.
4. **TinyTeX (LaTeX Engine):** A lightweight TeX distribution required to assemble the final PDF.

---

### Step 1: Install Required Software

Before working with the repository, install the following standalone tools if they are not already present on your machine:

1. **Install R:** Download from the [Comprehensive R Archive Network (CRAN)](https://cran.r-project.org/).
2. **Install RStudio Desktop (Recommended):** Download from [Posit](https://posit.co/download/rstudio-desktop/).
3. **Install Quarto CLI:** Download the installer for your operating system from the [Quarto Get Started page](https://quarto.org/docs/get-started/).
    - Verify installation in your terminal:
      ```bash
      quarto check install
      ```

---

### Step 2: Set Up the LaTeX Distribution

Quarto relies on a TeX distribution to compile LaTeX documents into PDFs. If you do not already have a full LaTeX distribution (such as TeX Live or MacTeX) installed, install TinyTeX via the Quarto command line:

```bash
quarto install tinytex
```

Alternatively, from an interactive R session:

```r
install.packages("tinytex")
tinytex::install_tinytex()
```

---

### Step 3: Clone or Download the Project

Clone this repository using Git, or download and extract the ZIP archive:

```bash
git clone https://github.com/ht2905/historical-microbes.git
cd historical-microbes
```

---

### Step 4: Restore R Dependencies (`renv`)

This project uses `renv` to record the exact R package versions used during writing. Think of `renv` as an inventory sheet specifying exact lot numbers and supplier details for lab reagents, preventing version conflicts.

#### Using RStudio (Interactive)

1. Double-click `historical_microbes.Rproj` to launch the project in RStudio.
2. RStudio will automatically activate the local `renv` environment.
3. In the R Console, run:
   ```r
   renv::restore()
   ```
4. Confirm when prompted. R will download and cache the recorded package versions (`knitr`, `rmarkdown`, `tinytex`, `ragg`, `yaml`).

#### Using the Terminal

Run the following command from the project root:

```bash
Rscript -e "renv::restore()"
```

---

### Step 5: Install the Elsevier Journal Extension

The journal layout definitions are managed via Quarto extensions and are not tracked directly in Git. Install the official Elsevier format extension inside the project directory:

```bash
quarto add quarto-journals/elsevier --no-prompt
```

This creates an `_extensions/quarto-journals/elsevier` directory containing the `elsarticle.cls` document class and formatting definitions.

---

### Step 6: Render the Manuscript

Once dependencies and extensions are in place, compile the PDF:

#### In RStudio
1. Open `historical_microbes.qmd` from the Files pane.
2. Click the **Render** button (blue arrow icon) in the editor toolbar.

#### In the Terminal
Run:

```bash
quarto render historical_microbes.qmd
```

Quarto processes the text, compiles the BibTeX citations, incorporates the figures in `photos/`, and produces a freshly rendered `historical_microbes.pdf`.

---

## Troubleshooting & Common Pitfalls

| Symptom | Root Cause | Solution |
|---|---|---|
| `LaTeX Error: File 'elsarticle.cls' not found` or `Unknown format elsevier-pdf` | The Elsevier Quarto journal extension is missing. | Run `quarto add quarto-journals/elsevier --no-prompt` in the project root directory. |
| `pdflatex not found` or `xelatex not found` | No LaTeX distribution is detected on your system path. | Run `quarto install tinytex` in your terminal, then restart RStudio or your terminal session. |
| R packages fail to install during `renv::restore()` | Missing system compilation libraries (primarily on Linux distributions). | On Ubuntu/Debian, install system build libraries via `sudo apt install build-essential libharfbuzz-dev libfribidi-dev libpng-dev libtiff5-dev libjpeg-dev`. |
| Figures do not appear or throw missing file warnings | The working directory is set to a subdirectory rather than the project root. | Ensure you are executing commands from the folder containing `historical_microbes.Rproj` and that the `photos/` folder is intact. |

---

## Academic Information

- **Course:** Microbiology (BT321IU)
- **Institution:** School of Biotechnology, International University - Vietnam National University Ho Chi Minh City (VNU-HCM)
- **Submission Date:** December 2025

### Author Contributions (CRediT Taxonomy)

- **Tran Quoc Hoang:** Conceptualization, Methodology, Project Administration, Software, Investigation (Sections 2 and 3), Writing – Original Draft (Sections 2 and 3), Writing – Review & Editing.
- **Nguyen Hoang Tuong Vy:** Writing – Original Draft (Section 5 and Conclusion), Writing – Review & Editing.
- **Nguyen Vy Van:** Investigation (Section 4), Writing – Original Draft (Section 4 and Introduction), Writing – Review & Editing.
- **Nguyen Le Ngoc Vy:** Data Curation, Visualization (Abstract and presentation slides), Writing – Review & Editing.
- **Nguyen Hoang Quynh Anh:** Data Curation, Visualization (Abstract and presentation slides), Writing – Review & Editing.

---

## Declarations

### Competing Interests
The authors declare that they have no competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

### Data and Code Availability
All source files, bibliographic databases, and figure assets are available in this repository:
[https://github.com/ht2905/historical-microbes](https://github.com/ht2905/historical-microbes)
