# Transkryptomika — Bulk RNA-seq Secondary Analysis

**Author:** Lena Borowiecka

---

## Overview

This project presents a secondary analysis of bulk RNA-seq data comparing two biological groups: **WT** (wild type) and **MUT** (mutant). The goal was to identify differentially expressed genes (DEGs) between the two conditions and interpret their biological significance through statistical testing and functional enrichment analysis.

The full analysis — including code, visualizations, and narrative interpretation — is available in the accompanying PDF file.

---

## What You Will Find in the PDF

- **Count matrix preparation** — loading featureCounts output, constructing a gene-by-sample count matrix, and building a `DESeqDataSet` object
- **Gene annotation** — mapping ENSEMBL identifiers to HGNC gene symbols, genomic information, and functional descriptions using `biomaRt`
- **Differential expression analysis** — Wald test via `DESeq2`, identification of 296 significantly differentially expressed genes (padj < 0.05)
- **Data exploration** — histograms of p-value, adjusted p-value, and log2FoldChange distributions; log-transformed normalized counts
- **Volcano plots** — standard and enhanced volcano plots (using `EnhancedVolcano`), highlighting the most significantly changed genes (e.g., SSC5D, ZNF845, C3)
- **PCA** — principal component analysis after rlog variance-stabilizing transformation, demonstrating clear separation of MUT and WT groups along PC1
- **GO enrichment analysis** — overrepresentation analysis for Biological Process (BP) and Cellular Component (CC) terms; key enriched pathways include complement receptor signaling, amyloid-beta clearance, and HDL particle assembly
- **Gene Set Enrichment Analysis (GSEA)** — identification of activated biological pathways in the MUT group, including complement signaling (GO:0002430), amyloid-beta clearance (GO:0097242), and GPCR-mediated phospholipase C activation (GO:0007200)

---

## Tools & Technologies

| Tool / Package | Purpose |
|---|---|
| R | Primary analysis environment |
| DESeq2 | Differential expression analysis |
| biomaRt | Gene annotation (ENSEMBL → HGNC) |
| EnhancedVolcano | Publication-quality volcano plots |
| clusterProfiler | GO and GSEA functional enrichment |
| ggplot2 | Data visualization |
| featureCounts | Raw read counting (upstream step) |

---

## Data

- **Source:** featureCounts output (RNA-seq read counts per gene)
- **Samples:** 6 biological samples — 3 WT (wild type) and 3 MUT (mutant)
- **Genes:** 2,992 genes after initial filtering
- **Gene identifiers:** ENSEMBL IDs, mapped to HGNC symbols for interpretation
- **Key finding:** 296 genes were significantly differentially expressed (padj < 0.05), with biological signal concentrated in immune response, lipid metabolism, and intracellular transport pathways
