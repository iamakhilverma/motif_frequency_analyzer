# motif_frequency_analyzer

We had 12 genbank files (for gram-positive bacteria) to analyze.  

#### Calculations, Plotting and Packages information
Codes were written to extract information on location (`start position`, `end position`) and desirable qualifiers (`Gene ID`, `Gene name`, `Locus tag`, `strand orientation`) of the feature keys from the feature table of Genbank files for all the genes present in them. All the genes where `Gene ID` or `Gene name` were absent were marked as unavailable in our data. Gene sequences were also extracted along with _upstream_- and _downstream_- flanking regions of length `200 bp` and `203 bp` (to account for 3 positions, i.e., boundary cases, while looking for _motifs_ in the next step where otherwise it’d give zero count for those positions).

The previously found _upstream_- and _downstream_- flanking regions of genes were searched for `GAAG` and `GAAA` _motifs_ and the starting positions for these _motifs_ relative to the gene boundary (In `5'-3'` direction, gene’s first base will have `+1` position, so the _upstream_- flanking region will be from `-200` to `-1` and gene’s last base will have, say `n` is the length of the gene, `+n` position, so the _downstream_- flanking region will be from `n+1` to `n+200`) were stored. The counts of these _motifs_ starting at each position in the flanking regions of `200 bp` length were recorded.
These counts were then used to create line plots showing frequency of the _motifs_ starting at a position relative to the start site, i.e., `+1`, of the gene. For this part, the data analysis and visualizations were done using `Python (v 3.8.12)` and some of its libraries- `pandas (v 1.3.3)`, `BioPython (v 1.79)`, `re module (v 2.2.1)`, and `matplotlib (v 3.4.2)`, in `Jupyter notebooks (v 6.4.3)`.
