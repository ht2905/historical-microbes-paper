# Microbes as Agents of Change: Historical, Cultural, and Astrobiological Perspectives

This repository contains the manuscript source code, bibliographic database, and figure assets for an academic review paper prepared for the Microbiology (BT321IU) course at the School of Biotechnology, International University - Vietnam National University Ho Chi Minh City (VNU-HCM).

The manuscript is typeset using Quarto and the Elsevier Journal format (`elsarticle`), producing a two-column, 17-page review with complete bibliographic citations and high-resolution figures.

---

## Quick Access: Reading the Paper

If your primary goal is to read the paper rather than recompile it from source, no software installation is required:

| Deliverable | Format | File Link | Description |
|---|---|---|---|
| Complete Manuscript | PDF (17 pages) | [historical-microbes_manuscript.pdf](historical-microbes_manuscript.pdf) | Complete pre-rendered manuscript in Elsevier double-column layout. |
| Assignment Cover Sheet | PDF (1 page) | [course-submission_cover-page.pdf](course-submission_cover-page.pdf) | Official university assignment submission cover page. |

---

## Scientific Framework and Conceptual Overview

Microbiology curricula conventionally introduce microorganisms primarily as pathogenic threats or as passive laboratory tools (such as *Escherichia coli* cloning hosts or *Saccharomyces cerevisiae* expression systems). This review argues for microbial agency—the perspective that biological properties of microbes (such as transmission kinetics, metabolic versatility, stress tolerance, and extreme environmental resilience) actively constrain, redirect, and transform human societal institutions, material culture, and scientific paradigms.

```mermaid
flowchart TD
    subgraph Core["Microbial Agency Framework"]
        A["Microorganisms as Active Historical and Biological Agents"]
    end

    subgraph D1["1. Demographic and Historical Pandemics"]
        B1["Yersinia pestis (Black Death)"] --> C1["Feudal labor shifts and socioeconomic restructuring"]
        B2["Variola major (Smallpox)"] --> C2["Indigenous demographic collapse and Jennerian vaccination"]
    end

    subgraph D2["2. Foundational Microbiological Methodologies"]
        B3["Louis Pasteur"] --> C3["Spontaneous generation refuted, pasteurization, rabies immunization"]
        B4["Robert Koch"] --> C4["Koch's postulates, solid media, pathogen causal isolation"]
        B5["Alexander Fleming"] --> C5["Penicillin discovery and the dawn of antimicrobial chemotherapy"]
    end

    subgraph D3["3. Cultural and Material Biotechnology"]
        B6["Living Bacterial Agar Art"] --> C6["Prodigiosin and violacein chromoprotein visual readouts"]
        B7["Fungal Pigment Fermentation"] --> C7["Sustainable bio-dyes replacing toxic chemical colorants"]
    end

    subgraph D4["4. Astromicrobiology and Planetary Boundaries"]
        B8["Extremophile Stress Physiology"] --> C8["Deinococcus and Bacillus endospore survival mechanisms"]
        B9["ISS EXPOSE-E Orbital Platform"] --> C9["Lithopanspermia viability and COSPAR planetary protection"]
    end

    A --> D1
    A --> D2
    A --> D3
    A --> D4
```

### Manuscript Summary

| Section | Topic | Primary Focus |
|---|---|---|
| Section 1 | Introduction | Establishes microbial biomass dominance and formalizes the microbial agency analytical framework. |
| Section 2 | Microbes that Changed History | Analyzes how *Yersinia pestis* (Black Death) forced feudal labor restructuring through zoonotic transmission kinetics, and how *Variola major* (smallpox) catalyzed Jennerian immunology and global disease eradication. |
| Section 3 | Famous Microbiologists and Groundbreaking Discoveries | Synthesizes the transition of microbes from ambiguous environmental phenomena into identifiable, controllable entities via Pasteur (germ theory, pasteurization, attenuation), Koch (postulates and pure cultures), and Fleming (penicillin and early warnings of antimicrobial resistance). |
| Section 4 | Microbes in Art and Culture | Documents microbial pigment synthesis (prodigiosin, violacein) in agar art, eukaryotic chromoprotein expression in *E. coli*, and industrial filamentous fungal fermentation for sustainable textile dyeing. |
| Section 5 | Bacteria in Space (Astromicrobiology) | Details extremophile physiological mechanisms, 559-day Low Earth Orbit survival on the ISS EXPOSE-E facility (ADAPT project), empirical support for lithopanspermia, and COSPAR planetary protection protocols against forward contamination. |
| Appendix A | Supplementary Figures and Tables | Provides industrial scale-up fermentation schematics, textile pigment swatch assays, and comprehensive fungal dye catalogs. |

---

## Media & Figure Architecture

Figures located in [`figures/`](figures/) follow the standardized faceted naming convention (`{entity}_{descriptor}.{ext}`) across four thematic areas:
- **Pathogen Transmission & History:** Vector-host transmission dynamics of *Yersinia pestis* (Section 2) and Pasteur's swan-necked flask experiment disproving spontaneous generation (Section 3).
- **Industrial Biotechnology & Bio-Art:** Eukaryotic chromoprotein palettes in *E. coli*, solid-phase to bioreactor scale-up for fungal pigments (*Penicillium purpurogenum*), and microbial art installations (Section 4).
- **Extreme Environments & Astromicrobiology:** Terrestrial crust cross-sections of polyextremophiles, ESA EXPOSE-E spaceflight exposure payloads, and spaceflight medical risk interactions (Section 5, Appendix A).

---

## Repository Structure

The repository follows a standardized faceted naming convention:

```text
historical-microbes-paper/
├── figures/                                  # High-resolution scientific figures and schematics
├── renv/                                     # R environment reproducibility manifests
├── _quarto.yml                               # Quarto project configuration
├── bibliography.bib                          # BibTeX literature database (Elsevier citations)
├── historical-microbes_manuscript.pdf        # Pre-compiled 17-page publication-grade PDF
├── historical-microbes_manuscript.qmd        # Primary manuscript source document
└── renv.lock                                 # Exact lockfile recording reproducible R dependencies
```

---

## Step-by-Step Reproduction Guide

If you wish to recompile the PDF from source on your personal computer, follow the instructions below.

### Prerequisites

| Tool | Recommended Version | Purpose |
|---|---|---|
| Quarto CLI | 1.4 or later | Scientific document processing and publishing system |
| TinyTeX or TeX Live | Latest | Lightweight LaTeX distribution to render the PDF |
| R | 4.2 or later (Optional) | Runtime environment if working via RStudio |
| RStudio Desktop | Latest (Optional) | Integrated GUI editor for one-click rendering |

### Step 1: Clone the Repository

Clone this repository using Git:

```bash
git clone https://github.com/ht2905/historical-microbes.git
cd historical-microbes
```

### Step 2: Install the Elsevier Journal Extension

The Elsevier layout definitions are managed via Quarto extensions. Install the extension in the project directory:

```bash
quarto add quarto-journals/elsevier --no-prompt
```

### Step 3: Render the Manuscript

Compile the Quarto Markdown source into the publication-grade PDF:

```bash
quarto render historical-microbes_manuscript.qmd --to elsevier-pdf
```

Quarto compiles the text, formats the BibTeX citations, includes the figures from `figures/`, and outputs `historical-microbes_manuscript.pdf`.

### Optional: Restore R Environment (`renv`)

Because the manuscript text, tables, and figures do not execute dynamic code chunks, R is not required to render the paper. However, if you are developing in RStudio and wish to restore the exact environment recorded during project creation:

```bash
Rscript -e "renv::restore()"
```

Or open `historical-microbes.Rproj` in RStudio and run `renv::restore()` in the console.

---

## Troubleshooting & Common Pitfalls

| Symptom | Root Cause | Solution |
|---|---|---|
| `LaTeX Error: File 'elsarticle.cls' not found` | The Elsevier Quarto journal extension is missing. | Run `quarto add quarto-journals/elsevier --no-prompt` in the project root directory. |
| `pdflatex not found` or `xelatex not found` | No LaTeX distribution is detected on your system path. | Run `quarto install tinytex` in your terminal. |
| Figure layout or file missing warning | Figure paths referencing outdated directory names. | Ensure all figure paths reference `figures/<file>` as cataloged in the figure atlas above. |

---

## Academic Information

- **Course:** Microbiology (BT321IU)
- **Host Institution:** School of Biotechnology, International University - Vietnam National University Ho Chi Minh City (VNU-HCM)
- **Academic Term:** Semester 1, Academic Year 2025–2026
- **Submission Date:** December 2025

### Author Contributions (CRediT Taxonomy)

| Contributor | CRediT Roles | Specific Responsibilities |
|---|---|---|
| **Tran Quoc Hoang** | Conceptualization, Methodology, Project Administration, Software, Investigation, Writing – Original Draft, Writing – Review & Editing | Conceived the study, structured the Quarto pipeline, wrote Section 2 (*Pandemics*) and Section 3 (*Foundational Microbiologists*). |
| **Nguyen Hoang Tuong Vy** | Writing – Original Draft, Writing – Review & Editing | Wrote Section 5 (*Astromicrobiology*) and the Conclusion; contributed to manuscript review. |
| **Nguyen Vy Van** | Investigation, Writing – Original Draft, Writing – Review & Editing | Conducted background research and wrote Section 1 (*Introduction*) and Section 4 (*Microbial Art and Culture*). |
| **Nguyen Le Ngoc Vy** | Data Curation, Visualization, Writing – Review & Editing | Co-authored Abstract, curated visual presentation materials, and participated in editorial review. |
| **Nguyen Hoang Quynh Anh** | Data Curation, Visualization, Writing – Review & Editing | Co-authored Abstract, curated visual presentation materials, and participated in editorial review. |

---

## Declarations

### Competing Interests

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

### Data and Code Availability

All source files, bibliographic databases, and figure assets are available in this repository:
[https://github.com/ht2905/historical-microbes](https://github.com/ht2905/historical-microbes)
