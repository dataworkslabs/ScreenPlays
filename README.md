# Screenplay Structure Analysis

An exploratory data analysis of eleven critically acclaimed screenplays spanning 1952 to 2025. The goal is to find out whether great screenplays share measurable structural and narrative patterns — and whether those patterns hold across genre, era, culture, and authorship.

## Screenplays

| Title | Writer(s) | Year | Original / Adapted |
|-------|-----------|------|--------------------|
| Ikiru | Hashimoto, Kurosawa, Oguni | 1952 | Original |
| Thelma & Louise | Callie Khouri | 1991 | Original |
| Boogie Nights | Paul Thomas Anderson | 1997 | Original |
| Eyes Wide Shut | Stanley Kubrick | 1999 | Adapted |
| Moonlight | Barry Jenkins | 2016 | Adapted |
| Get Out | Jordan Peele | 2017 | Original |
| Parasite | Bong Joon-ho & Han Jin-won | 2019 | Original |
| Portrait of a Lady on Fire | Céline Sciamma | 2019 | Original |
| Aftersun | Charlotte Wells | 2022 | Original |
| Sentimental Value | Joachim Trier & Eskil Vogt | 2025 | Original |
| Sinners | Ryan Coogler | 2025 | Original |

## Project Structure

```
├── data/
│   ├── screenplays/          # PDF screenplay files
│   ├── screenplays.html      # Metadata table (hand-built)
│   ├── screenplays.json      # Metadata (hand-built)
│   └── script_structure_dataset.csv  # Hand-coded story beat sheet
├── Project_2_Approach.Rmd    # Approach document
├── Project_2.qmd             # Final analysis (Quarto)
└── README.md
```

## Datasets

**Metadata** — title, writers, year, genre, runtime, page count, Rotten Tomatoes score, awards, and original vs. adapted. Built by hand in both HTML and JSON, loaded and compared in R.

**Structural features** — scene count, scene density, dialogue ratio, action line ratio, unique character count, and unique location count. Extracted programmatically from PDF screenplays using `pdftools` and `stringr`.

**Story beat sheet** — six structural moments coded by hand for each screenplay: inciting incident, Act 1 climax, midpoint, Act 2 climax, climax, and resolution. All positions recorded as page numbers and converted to percentages of total script length for cross-film comparison.

## Tools

- **R** — data loading, cleaning, extraction, and analysis
- **ggplot2** — visualizations
- **Tableau** — dashboard and exploratory visuals
- **Quarto** — final report, published to RPubs

## Packages

```r
pdftools     # PDF text extraction
stringr      # regex and string parsing
tidytext     # sentiment and lexical analysis
rvest        # loading HTML data
jsonlite     # loading JSON data
tidyr        # reshaping data
dplyr        # data manipulation
ggplot2      # visualization
ggrepel      # non-overlapping labels
```

## Notes

Four screenplays — Boogie Nights, Portrait of a Lady on Fire, Ikiru, and Thelma & Louise — had OCR or formatting issues that made automated scene counting unreliable. Those values are recorded as `NA` and excluded from scene-specific comparisons. Ikiru is also written in a Japanese screenplay tradition that doesn't map cleanly onto Hollywood three-act structure, which is noted wherever it affects the analysis.
