# Input data

Source files used to reproduce Figure 2 from Brauer et al. (2008). Files were
retrieved on 2026-06-18 and are cached here so rerunning the analysis does not
depend on the source servers remaining available.

| File | Source | Purpose |
| --- | --- | --- |
| `dilution_rate_00_raw.txt` | http://growthrate.princeton.edu/data/dilution_rate_00_raw.txt | Author-processed raw log2 expression ratios. This is the authoritative numeric source for the 5,537 rows and 36 conditions. |
| `dilution_rate_00_raw.cdt` | http://growthrate.princeton.edu/data/dilution_rate_00_raw.cdt | Author-provided Java TreeView file. Used only to recover and validate the historical gene ID (`YORF`) and Agilent probe ID (`UID`). |
| `GPL884.soft.gz` | https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL884 | Current GEO GPL884 platform annotation, loaded through GEOquery. Despite its `.gz` suffix, the cached file is plain-text SOFT. GEO lists its last update as 2012-12-06. |
| `SGD_features.tab` | https://downloads.yeastgenome.org/curation/chromosomal_feature/SGD_features.tab | Current Saccharomyces Genome Database feature names, standard names, feature types, and annotation qualifiers. |
| `deleted_merged_features.tab` | https://downloads.yeastgenome.org/curation/chromosomal_feature/deleted_merged_features.tab | Current SGD mappings for deleted, merged, or renamed historical features. |
| `GSE8825_series_matrix.txt.gz` | https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE8825 | GEO processed series matrix retained for reference; it is not used by the Figure 2 pipeline. |
| `GSE8825_RAW.tar` | https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE8825&format=file | Official GEO supplementary archive containing all 36 original Agilent Feature Extraction files and the historical GPL884 annotation. Downloaded to investigate probe-level quality flags and exclusions from the authors' processed matrix; it is not used by the Figure 2 pipeline. |
| `GSE8825_RAW/` | Extracted locally from `GSE8825_RAW.tar` | Contains `GSM219267.txt.gz` through `GSM219302.txt.gz` plus `GPL884_old_annotations.txt.gz`. The GSM files remain gzip-compressed. |

## Raw TXT versus CDT

The TXT and CDT contain the same 5,537 rows, row order, probe identities, and
ordered non-missing expression values. However, the CDT omits delimiters for
interior missing values in 359 rows. Those values shift into the wrong sample
columns when the CDT is parsed as a table. Therefore, expression values and
missing-value positions always come from `dilution_rate_00_raw.txt`; the CDT is
used only as an identity cross-check.

The raw TXT contains 866 missing expression values. Figure 2 handles them with
pairwise-complete Pearson correlations and displays them in gray; it does not
perform KNN imputation.
