# Kinesin Motor Proteins Phylogenetic Analysis Repository

> A comparative phylogenetic analysis workflow for the Kinesin Superfamily and Kinesin-14 Family, utilizing advanced alignment and tree-building tools to map evolutionary relationships.

### Project A: Kinesin Superfamily
![Sequences](https://img.shields.io/badge/Sequences-30-informational)
![Families](https://img.shields.io/badge/Families-10-darkgreen)
![Species](https://img.shields.io/badge/Species-6-blueviolet)
![Tools](https://img.shields.io/badge/Tools-MAFFT%20%7C%20IQ--TREE2%20%7C%20Biopython-brightgreen)

**Outputs:**
* Maximum Likelihood (ML) tree
* Heatmap generation
* Motif table
* Bootstrap plots

---

### Project B: Kinesin-14 Family
![Sequences](https://img.shields.io/badge/Sequences-16-informational)
![Subfamilies](https://img.shields.io/badge/Subfamilies-8-darkgreen)
![Species](https://img.shields.io/badge/Species-17-blueviolet)
![Tools](https://img.shields.io/badge/Tools-MAFFT%20%7C%20MUSCLE%20%7C%20RAxML%20%7C%20IQ--TREE2%20%7C%20ETE3-brightgreen)

**Outputs:**
* Annotated tree
* Auspice JSON
* Bootstrap analysis
# **1\.  Repository Structure**

The repository contains two independent analysis notebooks. Each notebook creates its own working directory structure at runtime inside Google Colab. All outputs are packaged into a downloadable ZIP archive at the end of each analysis.

| Path / File | Description |
| :---- | :---- |
| kinesis\_motorproteins\_phyl.ipynb | Project A — Kinesin superfamily analysis (13 cells) |
| kinesis14\_fam\_phylo.ipynb | Project B — Kinesin-14 family deep analysis (12 cells) |
| kinesin\_phylo/sequences/ | Individual FASTA files per protein, relabeled (Project A) |
| kinesin\_phylo/alignment/ | Raw aligned and gap-trimmed FASTA files (Project A) |
| kinesin\_phylo/trees/ | IQ-TREE2 outputs: .treefile, .log, .iqtree, .contree (Project A) |
| kinesin\_phylo/figures/ | All PNG plots: lengths, conservation, tree, bootstrap, heatmap (Project A) |
| kinesin14\_phylo/ | Mirrored directory structure for Project B |
| results/kinesin14\_tree.nwk | Best ML tree in Newick format (Project B) |
| results/kinesin14\_auspice.json | NextStrain-compatible JSON for web visualization (Project B) |
| kinesin\_phylo\_results.zip | Downloadable results archive — Project A |
| kinesin14\_results.zip | Downloadable results archive — Project B |
| kinesin\_motifs.csv | Per-protein motif detection table (Project A) |
| kinesin14\_motifs.csv | Per-protein motif detection table (Project B) |

# **2\.  Biological Background**

## **2.1  What are Kinesin Motor Proteins?**

Kinesins are a superfamily of ATP-dependent molecular motors that move along microtubules. They are essential for mitotic and meiotic cell division, intracellular organelle and vesicle transport, axonal cargo delivery in neurons, and assembly of cilia and flagella. The human genome encodes 45 kinesin genes unified by a conserved approximately 340 amino acid motor domain that binds both ATP and microtubules simultaneously.

All kinesins share three universally conserved ATP-binding motifs within the motor domain:

* **P-loop  (GxxxxGKT/S)**  — coordinates the alpha and beta phosphates of ATP; the most invariant motif across all kinesin families

* **Switch I  (NxxSSR)**  — senses the gamma-phosphate of ATP; conformational change upon microtubule contact triggers ATPase activity

* **Switch II  (DxxG)**  — transmits the hydrolysis event into the mechanical power stroke that drives movement

## **2.2  Kinesin-14 — The Minus-End Directed Family**

Kinesin-14 members carry their motor domain at the C-terminus of the protein, unlike all other kinesin families where the motor domain is at the N-terminus. This structural inversion is the molecular basis for minus-end directionality — these motors walk toward the slow-growing minus end of microtubules, which is opposite to the direction of nearly all other kinesin families. Kinesin-14 members are found across all major eukaryotic kingdoms, indicating this family arose before the last common eukaryotic ancestor.

| Organism Group | Key Members | Primary Function |
| :---- | :---- | :---- |
| Vertebrates — Human, Mouse, Zebrafish | KIFC1 (HSET), KIFC2, KIFC3 | Spindle pole focusing; KIFC1 is a cancer drug target |
| Insects — Drosophila | Ncd (Non-claret disjunctional) | Meiotic and mitotic spindle organization |
| Nematodes — C. elegans | KLP-18, KLP-15 | Meiotic spindle assembly |
| Plants — Arabidopsis thaliana | ATK1, ATK2, ATK5, KP1 | Pollen tube growth; plastid division |
| Rice — Oryza sativa | OsKCH1, OsKCH2 | Pollen development |
| Budding Yeast — S. cerevisiae | Kar3 (with Cik1 light chain) | Karyogamy; kinetochore-microtubule attachment |
| Fission Yeast — S. pombe | Pkl1, Klp2 | Spindle pole body; chromosome segregation |
| Filamentous Fungi — Aspergillus | KlpA | Nuclear migration along microtubules |
| Green Algae — Chlamydomonas | KLP1 | Flagellar and chloroplast-associated functions |

# **3\.  Tools and Software**

| Tool | Version Used | Purpose in This Analysis | Citation |
| :---- | :---- | :---- | :---- |
| MAFFT | 7.490 | Multiple sequence alignment — \--auto mode selects L-INS-i or FFT-NS-i based on input size | Katoh & Standley 2013 |
| IQ-TREE2 | 2.3.6 | Maximum-likelihood tree inference; ModelFinder selects substitution model; UFBoot bootstrap | Minh et al. 2020 |
| RAxML | 8.x | Alternative ML inference in Project B using PROTGAMMALG model with rapid bootstrap | Stamatakis 2014 |
| Biopython | 1.87+ | NCBI Entrez API for sequence fetching; AlignIO, Phylo modules for I/O and visualization | Cock et al. 2009 |
| trimAl / Python fallback | 1.4.1 / built-in | Alignment column trimming — removes columns exceeding 50% gap content | Capella-Gutierrez et al. 2009 |
| ETE3 | 3.x | Advanced annotated tree rendering with node styling and clade boxes (Project B) | Huerta-Cepas et al. 2016 |
| MUSCLE | 5.x | Alternative aligner attempted before MAFFT fallback in Project B | Edgar 2004 |
| FastTree | 2.x | Rapid approximate ML tree option available as fallback | Price et al. 2010 |
| matplotlib / seaborn | latest | All figures: heatmaps, histograms, conservation plots, bar charts | Hunter 2007 |
| pandas / numpy | latest | Sequence statistics, identity matrix computation, data manipulation |  |
| plotly | latest | Interactive visualization of sequence statistics (Project B) |  |
| Google Colab | — | Cloud compute platform — no local installation required; free GPU/CPU access |  |

# **4\.  Inputs**

## **4.1  Project A — Kinesin Superfamily**

**Sequence source:**  NCBI Protein database, fetched via Biopython Entrez.efetch with registered email

**Total sequences:**  30 curated protein accessions spanning 10 kinesin families

**Species covered:**  Homo sapiens, Mus musculus, Danio rerio, Drosophila melanogaster, Caenorhabditis elegans, Saccharomyces cerevisiae

**Format:**  Full-length protein FASTA, relabeled as GeneName\_SpeciesAbbrev (e.g., KIF5A\_Hs, KHC\_Dm)

| Family | Motor Direction | Human Members | Orthologues Included |
| :---- | :---- | :---- | :---- |
| Kinesin-1 | Plus-end | KIF5A, KIF5B, KIF5C | KHC (D. melanogaster), UNC-116 (C. elegans), KIF5B (M. musculus) |
| Kinesin-2 | Plus-end | KIF3A, KIF3B | — |
| Kinesin-3 | Plus-end | KIF1A, KIF1B | UNC-104 (C. elegans) |
| Kinesin-4 | Plus-end | KIF4A, KIF4B | — |
| Kinesin-5 (Eg5/BimC) | Plus-end | KIF11 | KLP61F (Drosophila), Cin8, Kip1 (Yeast) |
| Kinesin-6 | Plus-end | KIF20A (MKLP2), KIF23 (MKLP1) | — |
| Kinesin-7 | Plus-end | CENP-E | — |
| Kinesin-8 | Plus-end | KIF18A, KIF18B | — |
| Kinesin-13 | Non-motile (depolymerizing) | KIF2A, KIF2B, KIF2C (MCAK) | KLP10A (Drosophila) |
| Kinesin-14 | Minus-end | KIFC1 (HSET), KIFC3 | Ncd (Drosophila), Kar3 (Yeast) |

## **4.2  Project B — Kinesin-14 Family**

**Sequence source:**  NCBI Protein database via Entrez batch fetch with exponential backoff retry logic

**Total sequences:**  16 confirmed Kinesin-14 members, each tagged with directionality annotation

**Directionality annotation:**  Each sequence labeled minus (experimentally confirmed) or unknown based on published biochemical data

**Species coverage:**  17 species across animals, fungi, plants, green algae, and amoebozoa

| Accession | Label | Organism | Subfamily | Direction |
| :---- | :---- | :---- | :---- | :---- |
| NP\_477177 | Dm\_NCD | Drosophila melanogaster | Ncd — Insect | minus |
| NP\_013491 | Sc\_KAR3 | Saccharomyces cerevisiae | Kar3/Pkl1 — Yeast | minus |
| NP\_198067 | At\_KCBP | Arabidopsis thaliana | ATK/KP — Plant | minus |
| AAA35501 | Cg\_CHO2 | Cricetulus griseus | KIFC — Vertebrate | minus |
| NP\_003147 | Hs\_KIFC1 | Homo sapiens | KIFC — Vertebrate | minus |
| NP\_055854 | Hs\_KIFC2 | Homo sapiens | KIFC — Vertebrate | minus |
| NP\_006550 | Hs\_KIFC3 | Homo sapiens | KIFC — Vertebrate | minus |
| NP\_595802 | Sp\_PKL1 | Schizosaccharomyces pombe | Kar3/Pkl1 — Yeast | minus |
| NP\_177108 | At\_ATK1 | Arabidopsis thaliana | ATK/KP — Plant | minus |
| NP\_177109 | At\_ATK2 | Arabidopsis thaliana | ATK/KP — Plant | minus |
| NP\_013491 | Ce\_KLP18 | Caenorhabditis elegans | KLP — Nematode | unknown |
| ... (5 more) | — | Various | Various | minus/unknown |

# **5\.  Steps to Perform**

## **5.1  Setup — Google Colab**

1. **Open Google Colab:**  Go to colab.research.google.com and sign into your Google account

2. **Start a new notebook:**  Click "New notebook" — this gives you a fresh runtime environment

3. **Change your email:**  In Cell 2 of each notebook, replace the placeholder email with your own — NCBI requires this for API access

4. **Run cells in order:**  Copy each cell, paste into Colab, and press Shift+Enter before proceeding to the next cell

5. **Runtime environment:**  Each Colab session is isolated — if the session disconnects, re-run all cells from Cell 1

**Important time estimates:**  Cell 1 (installation) \= 3-5 minutes.  Cell 7 (IQ-TREE2) \= 5-15 minutes.  All other cells \= under 1 minute each.

## **5.2  Project A — Step by Step (13 Cells)**

| Cell \# | Step Name | What It Does | Success Indicator |
| :---- | :---- | :---- | :---- |
| 1 | Install tools | Installs MAFFT, IQ-TREE2, Biopython, matplotlib, seaborn, pandas via apt and pip | Version numbers printed for all tools |
| 2 | Imports and setup | Loads Python libraries; sets NCBI email; creates 5 working subdirectories | Directory listing: kinesin\_phylo/sequences/, alignment/, trees/, figures/ |
| 3 | Define accessions | Defines 30 NCBI accession numbers across 10 families with family color map | Family membership counts printed |
| 4 | Fetch sequences | Downloads protein FASTA from NCBI one-by-one with 0.4s delay; labels sequences; writes combined FASTA | OK (xxx aa) printed per sequence; combined FASTA confirmed |
| 5 | MAFFT alignment | Runs MAFFT \--auto \--reorder \--thread \-1 on combined FASTA | Alignment dimensions: N sequences x M columns |
| 6 | Trim alignment | Pure Python: removes columns with \>50% gaps; plots conservation and gap fraction per column | Conservation plot displayed; trimmed FASTA written |
| 7 | IQ-TREE2 ML tree | Runs ModelFinder, 1000 UFBoot, 1000 SH-aLRT, NNI; writes treefile | Best-fit model name, log-likelihood, and wall-clock time printed |
| 8 | Tree visualization | Reads treefile; draws rectangular tree with Biopython; colors tips by family; adds legend | Phylogeny figure displayed and saved as PNG |
| 9 | Bootstrap analysis | Extracts internal node support values; plots histogram and pie chart by confidence category | Bootstrap distribution figure with weak/moderate/strong breakdown |
| 10 | Identity heatmap | Computes pairwise sequence identity from trimmed alignment; renders RdYlGn heatmap | Heatmap with color scale displayed |
| 11 | Motif analysis | Searches each sequence for P-loop, Switch I, Switch II using regular expressions | Styled DataFrame: missing motifs highlighted red |
| 12 | Export ZIP | Packages alignment, trees, figures, and CSV into archive; triggers Colab download | kinesin\_phylo\_results.zip downloaded to local computer |
| 13 | Empty cell | Reserved scratch space | — |

## **5.3  Project B — Step by Step (12 Cells)**

| Cell \# | Step Name | What It Does | Success Indicator |
| :---- | :---- | :---- | :---- |
| 1 | Install packages | pip installs biopython, ete3, matplotlib, seaborn, numpy, pandas, plotly, scipy; apt installs muscle, raxml, mafft, fasttree | All packages confirmed; "ready" message printed |
| 2 | Imports and config | Loads all libraries; sets Entrez email; configures matplotlib DPI and font; creates directory structure | Setup confirmed |
| 3 | Define sequences | Defines 16+ Kinesin-14 entries with accession, species code, gene, directionality tag, and full organism name | Sequence list displayed |
| 4 | Fetch sequences | Fetches from NCBI with 0.4s delay per sequence; labels as Species\_Gene\_Direction; writes combined FASTA | Per-sequence status with directionality tag; FASTA path printed |
| 5 | Sequence statistics | Computes per-sequence length, percent charged residues, percent hydrophobic residues; plots distributions | Stats DataFrame and scatter/bar plots displayed |
| 6 | Alignment | Tries MUSCLE first; falls back to MAFFT if MUSCLE unavailable; saves aligned FASTA | Tool used and alignment dimensions printed |
| 7 | Alignment visualization | Renders per-residue color-coded alignment matrix (first 120 columns, ClustalX color scheme) | Colored MSA heatmap displayed |
| 8 | Tree inference | Tries RAxML (PROTGAMMALG \+ rapid bootstrap); falls back to IQ-TREE2; saves Newick | Tree file written at results/kinesin14\_tree.nwk |
| 9 | Two-panel tree (A+B) | Panel A: tips colored by directionality (red=minus). Panel B: tips colored by species. Bootstrap on branches. | Two-panel 18-inch wide figure displayed |
| 10 | Annotated tree | Single tree with clade boxes marking vertebrate, fungal, and plant groups; bootstrap labels on branches | Annotated tree with labeled group boxes displayed |
| 11 | Auspice JSON | Builds NextStrain-compatible JSON encoding branch lengths, species, gene, directionality metadata | results/kinesin14\_auspice.json written |
| 12 | Bootstrap analysis | Histograms bootstrap values; draws radial pie chart; prints mean support and node count | Bootstrap figure with mean support line displayed |

# **6\.  Outputs**

## **6.1  Project A Output Files**

| File | Format | Description |
| :---- | :---- | :---- |
| kinesin\_phylo/sequences/\*.fasta | FASTA | One file per protein; header replaced with short GeneFamily\_Species label |
| kinesin\_phylo/alignment/kinesin\_all.fasta | FASTA | All 30 sequences concatenated before alignment |
| kinesin\_phylo/alignment/kinesin\_aligned.fasta | FASTA | MAFFT multiple sequence alignment (unfiltered) |
| kinesin\_phylo/alignment/kinesin\_trimmed.fasta | FASTA | Gap-filtered alignment used as IQ-TREE2 input (columns \<=50% gaps retained) |
| kinesin\_phylo/trees/kinesin.treefile | Newick | Best ML tree; internal node labels \= bootstrap support values |
| kinesin\_phylo/trees/kinesin.iqtree | Text | Full IQ-TREE2 report: model parameters, AIC, BIC, tree topology |
| kinesin\_phylo/trees/kinesin.log | Text | Complete run log including model selection table and timing |
| kinesin\_phylo/trees/kinesin.contree | Newick | Consensus tree derived from 1000 bootstrap replicates |
| kinesin\_phylo/figures/sequence\_lengths.png | PNG | Horizontal bar chart of all 30 sequence lengths colored by family |
| kinesin\_phylo/figures/conservation.png | PNG | Dual-panel plot: conservation score and gap fraction per alignment column |
| kinesin\_phylo/figures/tree\_biopython.png | PNG | Rectangular ML phylogeny with family color legend |
| kinesin\_phylo/figures/bootstrap.png | PNG | Histogram of bootstrap values and pie chart by support category |
| kinesin\_phylo/figures/identity\_heatmap.png | PNG | Pairwise sequence identity matrix (RdYlGn scale; values in percent) |
| kinesin\_motifs.csv | CSV | Table: protein, family, length, P-loop match, Switch I match, Switch II match |
| kinesin\_phylo\_results.zip | ZIP | Archive of all above files for local download |

## **6.2  Project B Output Files**

| File | Format | Description |
| :---- | :---- | :---- |
| data/alignments/kinesin14\_aligned.fasta | FASTA | MUSCLE or MAFFT alignment of all Kinesin-14 sequences |
| results/kinesin14\_tree.nwk | Newick | Best ML tree with bootstrap support at internal nodes |
| results/raxml\_kinesin14/ | Directory | Full RAxML output when RAxML is used as the tree inference tool |
| results/kinesin14\_auspice.json | JSON | NextStrain-compatible node-link JSON with species, gene, directionality metadata |
| figures/sequence\_stats.png | PNG | Sequence length distributions and amino acid composition plots by subfamily |
| figures/alignment\_viz.png | PNG | ClustalX-style residue-colored alignment heatmap (120 columns shown) |
| figures/tree\_directionality.png | PNG | Two-panel tree: Panel A colored by directionality; Panel B colored by species |
| figures/tree\_annotated.png | PNG | Single annotated tree with vertebrate, fungal, and plant clade boxes |
| figures/bootstrap\_analysis.png | PNG | Bootstrap distribution histogram and radial pie chart |
| kinesin14\_motifs.csv | CSV | Kinesin-14 motif detection: P-loop, Switch I, Switch II, DLAGSE, neck helix |
| kinesin14\_results.zip | ZIP | Complete output archive downloaded from Colab |

# **7\.  Biological Interpretations**

## **7.1  Project A — Kinesin Superfamily Tree**

### **Family Monophyly**

A correctly inferred kinesin superfamily tree should recover each of the 10 families as a monophyletic group — all members of a given family cluster together to the exclusion of other families. Bootstrap support values above 95% at the base of each family clade indicate that the grouping is statistically robust and reflects genuine shared ancestry. Values below 70% at critical nodes may indicate insufficient sequence diversity in the dataset or incomplete lineage sorting.

### **Kinesin-13 as Structural Outlier**

Kinesin-13 members (KIF2A, KIF2B, KIF2C/MCAK; KLP10A in Drosophila) are non-motile depolymerizing motors with an M-type (internal) motor domain. Their sequences may show longer branch lengths and potentially diverge more in position within the tree compared to motile kinesins, reflecting the different selective pressures acting on a motor domain adapted for microtubule catastrophe rather than translocation. This is biologically expected and does not indicate a data quality problem.

### **Kinesin-14 as Natural Root Indicator**

Kinesin-14 members carry a C-terminal motor domain, making them structurally the most divergent from the ancestral N-terminal motor configuration. They may form a long-branch outgroup clade relative to all other families, and their position can be informative for rooting the tree. Including Kar3 (yeast) and Ncd (Drosophila) alongside human KIFC proteins allows evaluation of whether this family is monophyletic across highly diverged species.

### **Motif Conservation Across Species**

The P-loop motif (GxxxxGKT/S) should be present in virtually every sequence analyzed. Its absence from a full-length protein sequence is strong evidence of either a sequencing error, an incorrect accession, or a non-motor domain fragment. Switch I and Switch II may show conservative substitutions in divergent organisms (fungi, nematodes) while maintaining the catalytic residues. The presence of all three motifs in distantly related species such as Saccharomyces cerevisiae and Caenorhabditis elegans demonstrates the extreme conservation of the kinesin catalytic mechanism across 1.5 billion years of evolution.

### **Pairwise Identity Block Structure**

The identity heatmap should display visible block structure corresponding to kinesin family clusters. Within-family identity for vertebrate paralogues typically ranges from 50-90%. Cross-species orthologues (human vs. mouse KIF5B) show 85-95% identity. Distantly related families show 25-40% identity, which still exceeds the typical threshold for fold recognition. Pairs with identity below 20% across the full sequence length may be aligned primarily on their motor domain; these represent legitimate kinesin relationships despite low global similarity.

## **7.2  Project B — Kinesin-14 Deep Phylogeny**

### **Four Major Subfamilial Clades Expected**

The Kinesin-14 tree should resolve into at least four well-supported clades: (1) the vertebrate KIFC clade containing KIFC1, KIFC2, and KIFC3 from human, mouse, and zebrafish; (2) the insect Ncd clade; (3) the fungal clade uniting Kar3 (S. cerevisiae), Pkl1, and Klp2 (S. pombe), and KlpA (A. nidulans); and (4) the plant clade containing ATK1, ATK2, ATK5, and KCBP from Arabidopsis. Strong bootstrap support (\>85%) at the base of each clade is expected given the deep divergence between these lineages.

### **Minus-End Directionality is Monophyletic**

All experimentally confirmed minus-end motors should cluster together with high bootstrap support. If any sequence annotated as "unknown" directionality falls within the confirmed minus-end clade with strong bootstrap support, this constitutes phylogenetic evidence for its likely minus-end directionality. Such predictions can guide future in vitro motility assays. Conversely, any confirmed minus-end motor that falls outside the main clade would indicate convergent evolution of this motor polarity, which would be a significant biological finding.

### **Tree Congruence with Species Phylogeny**

The Kinesin-14 gene tree should broadly match the known species tree: animals and fungi (Opisthokonta) grouping together, plants (Viridiplantae) as an outgroup to Opisthokonta, and early-branching eukaryotes such as Giardia forming a deep outgroup to all crown eukaryotes. Significant incongruence between the gene tree and species tree may indicate horizontal gene transfer, incomplete lineage sorting, or long-branch attraction artifacts in the alignment. Examining branch lengths in the .iqtree output file helps distinguish these scenarios.

### **KIFC1 (HSET) and Cancer Biology**

KIFC1 is synthetically lethal with centrosome amplification, a hallmark of many aggressive cancers. Normal diploid cells tolerate KIFC1 loss without consequence, making it an attractive therapeutic target. Its position in the vertebrate KIFC clade at a short branch length relative to KIFC2 and KIFC3 indicates strong purifying selection, consistent with its non-redundant role in centrosome clustering. Structural comparisons enabled by the alignment (Cell 7 visualization) identify conserved residues within the motor domain that are under active investigation as drug binding sites.

### **Plant Kinesin-14 — Unique Features**

Plant ATK kinesins lack functional orthologues of KIFC1 and operate in a different cellular context, as plant cells lack centrosomes and build an anastral spindle from chromatin-nucleated microtubules. The clustering of ATK1, ATK2, and ATK5 in a plant-specific clade with KCBP reflects a common origin for these plant-specific adaptations. The longer branch lengths for plant sequences relative to animal sequences are expected and reflect the rapid diversification of motor proteins in the land plant lineage following the Cambrian explosion.

## **7.3  Bootstrap Support — Interpretation Reference**

| Bootstrap Value | Interpretation | Recommended Action |
| :---- | :---- | :---- |
| 95 \- 100% | Strong support — clade is statistically well-resolved | Accept grouping with high confidence; cite in discussion |
| 70 \- 94% | Moderate support — probable but some uncertainty remains | Note uncertainty; consider adding more taxa or longer alignment |
| 50 \- 69% | Weak support — topology at this node may be stochastic | Treat with caution; collapse to polytomy if below 50% |
| Below 50% | Unsupported — topology is essentially unresolved | Do not interpret this node; use polytomy representation |

# **8\.  References**

**Sequence Databases and Nomenclature**

* Lawrence, C.J. et al. (2004). A standardized kinesin nomenclature. *Journal of Cell Biology* 167, 19-22.

* Hirokawa, N. et al. (2009). Kinesin superfamily motor proteins and intracellular transport. *Nature Reviews Molecular Cell Biology* 10, 682-696.

* She, Z.Y. & Yang, W.X. (2017). Molecular mechanisms of kinesin-14 motors in spindle assembly and chromosome segregation. *Journal of Cell Science* 130, 2097-2110.

**Sequence Alignment**

* Katoh, K. & Standley, D.M. (2013). MAFFT multiple sequence alignment software version 7: improvements in performance and usability. *Molecular Biology and Evolution* 30, 772-780.

* Edgar, R.C. (2004). MUSCLE: multiple sequence alignment with high accuracy and high throughput. *Nucleic Acids Research* 32, 1792-1797.

* Capella-Gutierrez, S. et al. (2009). trimAl: a tool for automated alignment trimming in large-scale phylogenetic analysis. *Bioinformatics* 25, 1972-1973.

**Phylogenetic Inference**

* Minh, B.Q. et al. (2020). IQ-TREE 2: New models and methods for phylogenetic inference. *Molecular Biology and Evolution* 37, 1530-1534.

* Stamatakis, A. (2014). RAxML version 8: a tool for phylogenetic analysis and post-analysis of large phylogenies. *Bioinformatics* 30, 1312-1313.

* Hoang, D.T. et al. (2018). UFBoot2: Improving the ultrafast bootstrap approximation. *Molecular Biology and Evolution* 35, 518-522.

* Kalyaanamoorthy, S. et al. (2017). ModelFinder: fast model selection for accurate phylogenetic estimates. *Nature Methods* 14, 587-589.

**Visualization and Software**

* Huerta-Cepas, J. et al. (2016). ETE 3: Reconstruction, analysis, and visualization of phylogenomic data. *Molecular Biology and Evolution* 33, 1635-1638.

* Hunter, J.D. (2007). Matplotlib: A 2D graphics environment. *Computing in Science & Engineering* 9, 90-95.

* Cock, P.J.A. et al. (2009). Biopython: freely available Python tools for computational molecular biology and bioinformatics. *Bioinformatics* 25, 1422-1423.

**Kinesin-14 Biology**

* Dagenbach, E.M. & Bhatt, S.A. (2004). A new kinesin tree. *Journal of Cell Science* 117, 3-7.

* Endow, S.A. & Waligora, K.W. (1998). Determinants of kinesin motor polarity. *Science* 281, 1200-1202.

* Cai, S. et al. (2009). Kinesin-14 family proteins HSET/XCTK2 control spindle length by cross-linking and sliding microtubules. *Molecular Biology of the Cell* 20, 1348-1359.

* Wu, J. et al. (2006). Kinesin-14 and kinesin-5: key motors required for anaphase chromosome segregation. *Cell Division* 1, 17\.

| Kinesin Phylogenetics Repository  |  Project A: Superfamily  |  Project B: Kinesin-14  |  Google Colab  |  2024-2026 |
| :---: |

