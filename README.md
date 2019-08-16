# Gene-Drug-Association
Pipeline for Gene-Drug association for CCLE cancer cell line pharmacogenomic data

Identify significant gene-drug association for an interested gene list with gene cnv, gene expression, drug response and dependency data, and box plot of drug/dep for cnv-status/gene-expression for the interested genes.

Updated August 15th, 2019

@Copyright Zi-Ming Zhao ziming.gt@gmail.com

## Overall summary:
The pipeline is evaluating the drug effects of selected gene’s CNA changes by using the CCLE cell line genomic and drug data (CTRP v2) [Viswanathan et al. (Nature, 2017); Adams et al. (ACS Chem Biol, 2014)]. The CCLE drug response data were downloaded from Cancer Therapeutics Response Portal (www.broadinstitute.org/ctrp), and CCLE gene-level CNA and gene expression data from depMap data portal (‘public_19Q1_gene_cn.csv’ and ‘CCLE_depMap_19Q1_TPM.csv’ https://depmap.org/portal/download/) [citations:
Cancer Cell Line Encyclopedia Consortium, and Genomics of Drug Sensitivity in Cancer Consortium. 2015. Pharmacogenomic Agreement between Two Cancer Cell Line Data Sets. Nature 528 (7580):84–87. https://doi.org/10.1038/nature15736.
Jordi Barretina, Giordano Caponigro, Nicolas Stransky, Kavitha Venkatesan, William R. Sellers, Robert Schlegel, Levi A. Garraway, et. al. 2012. The Cancer Cell Line Encyclopedia Enables Predictive Modelling of Anticancer Drug Sensitivity. Nature 483 (7391):603–7. https://doi.org/10.1038/nature11003.]. 

For CCLE drug data, area-under-concentration-response curve (AUC) sensitivity scores were used for each cancer cell line and each drug. In total, I collected gene-level CNA data from 668 CCLE cell lines, with a total of 545 drugs tested. With the CCLE gene-level CNA and AUC drug sensitivity scores, I performed drug effects functional analyses for selected  genes. Particularly, I took the selected gene list, calculated P-value from the Pearson correlation between each gene’s CNA and each drug across cell lines for the interested tumor types or pan-cancer, and further calculated Q-value by multiple testing Bonferroni correction for the P-values. Significant gene-CNA and drug associations were kept (Q-value > 0.1), and is further evaluated for the gene-expression and drug associations. Final significant genes were presented if the gene-drug association is significant for both CNA and gene expression in the same direction, e.g. drug sensitivity with both high CNA and high gene expression.

### Required input files/data:
CCLE_gene_shared_drug.csv #file with drug response auc for genes CNV for each cell line
CCLE_gene_shared_deps.csv file with dependency for gene CNV for each cell lines;
cnv_drug_sharedCellLines.csv ##file with IDs matching between drug/dependency cell lines and ccle cell lines
drug_target.csv

cnv_ctrpv2_gene_drug_tumortype_correlation.csv
gex_ctrpv2_gene_drug_tumortype_correlation.csv

### Output files:
Gene cnv/gene-expression and drug/dependency association.
Box plot of dep/drugs for cnv-status/gene-expression for the interested genes.
