reanalyze results from the following article:

Brauer, Matthew J., Curtis Huttenhower, Edoardo M. Airoldi, et al. 2008. “Coordination of Growth Rate, Cell Cycle, Stress Response, and Metabolic Activity in Yeast.” Molecular Biology of the Cell 19 (1): 352–67. https://doi.org/10.1091/mbc.E07-08-0779.

Data available from GEO GSE8825 and also on the author's website: http://growthrate.princeton.edu/transcriptome/download.shtml

## Figure 2 reproduction

The Figure 2 analysis starts from the authors' processed 5,537-row raw
expression matrix rather than the GEO series matrix. It validates the companion
CDT file, updates feature annotations through GPL884 and the current
Saccharomyces Genome Database tables, and clusters every row by
pairwise-complete Pearson correlation with average-linkage UPGMA.

Run from the project root:

```sh
Rscript -e 'rmarkdown::render("analysis/20260618-Brauer-2008-reanalysis.Rmd")'
```

The script uses cached files in `input/`, downloading a source only when it is
missing. The rendered HTML has a floating table of contents and code folded by
default. Input provenance and the TXT/CDT comparison are documented in
`input/README.md`. Figure 3 code is retained as a comment pending a separate
SVD implementation.

Primary outputs:

- `analysis/20260618-Brauer-2008-reanalysis.html`
- `output/figure2_hierarchical_clustering.png`
- `output/figure2_gene_annotation.csv`
