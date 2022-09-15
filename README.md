# G6PDcat
Catalog of G6PD variants, genotype-phenotype associations, and functional information

## Summary

This repository contains data and code associated with Geck et al. 2022, as well as up-to-date tables of G6PD variants and functional information curated from published studies and databases.

## Citation

Please cite: Geck RC, Powell NR, Dunham MJ. 2022. Functional interpretation, cataloging, and analysis of 1,341 known and new glucose-6-phosphate dehydrogenase variants. bioRxiv. doi: 10.1101/2022.09.14.508023

This repository is licensed under CC BY 4.0 for reuse with attribution. See LICENSE file for details.

## Repository overview

The most up-to-date catalog files are in the root directory:

| File | Description | 
|:--------|:------------|
| variant_catalog.txt |	All G6PD variants identified in humans, with summary information on activity, stability, and interpretation |
| variant_names.txt	| Common and alternate / legacy variants names |
| variant_molecular_info.txt	| Summaries of reports on variant function, including clinical phenotypes and average activity by study for each variant |
| variant_interpretation.txt |	Supporting evidence and oddsPath calculations for interpretations made by applying ACMG guidelines |

Versions used in Geck et al. 2022 are in the **published_catalog_2022** directory:

| File | Description | 
|:--------|:------------|
| tableS1_variants.txt	| Published version of variant_catalog |
| tableS2_names.txt	| Published version of variant_names |
| tableS3_info.txt	| Published version of variant_molecular_info |
| tableS4_acmg.txt |	Published version of variant_interpretation |

The R script and tables used to create graphics in Geck et al. 2022 are in the **published_figures_2022** directory.

## Curation

Variants were curated from databases and PubMed searches. Intronic variants were only included if a clinical annotation (listed on ClinVar) or functional annotation (activity or stability) was provided. 

The database versions or last-searched date used for the up-to-date catalog and published version are as follows:

| Database | Link | Geck et al. 2022 | Updated |
|:--------|:------------|:--------|:------------|
| bravo | https://bravo.sph.umich.edu/freeze8/hg38 | TOPmed freeze 8 | TOPmed freeze 8 |
| ClinVar | https://www.ncbi.nlm.nih.gov/clinvar | Aug 12, 2022 | Aug 12, 2022 |
| CPIC | https://cpicpgx.org/guidelines/guideline-for-rasburicase-and-g6pd | Feb 25, 2021 | Feb 25, 2021 |
| dbSNP | https://www.ncbi.nlm.nih.gov/snp | Aug 12, 2022 | Aug 12, 2022 |
| gnomAD | https://gnomad.broadinstitute.org | v2.1.1 and v3.1.1 | v2.1.1 and v3.1.1 |
| HGMD | http://www.hgmd.cf.ac.uk/ac | Aug 12, 2022 | Aug 12, 2022 |
| LOVD | https://databases.lovd.nl/shared/variants/G6PD/unique | v3.0 build 26 | v3.0 build 26 |

The only conflicts of note addressed during curation are:
- ClinVar lists Puerto Limon twice on two different transcripts (variation ID 804134 and 10381) so it is only included once in the catalog with variation ID 10381
- ClinVar lists variant numbers 1237186 and 1280478, but no nucleotide changes are given so they are not included in the catalog
- Arunachalam et al. 2020 (PMID 32425388) erroneously reports variant c.1186C>T, but a previous publication on the same patients reports c.1186C>G, which matches amino acid change reported in both studies. Thus c.1186C>T is not included in the catalog since it has not been reported elsewhere.

## File descriptions

### variant_catalog.txt

| Column | Description |
|--------|:------------|
| name | Name or names given to variant. Some have multiple names preceding molecular characterization. |
| rsID	| rsID used to identify SNP |
| hg19_core	| Genomic location of variant SNP/SNPs in hg19/GRch37 genome assembly |
| cdna |	SNP(s) in G6PD cDNA, on transcript NM_001042351.1 |
| amino_acid	| Effect of SNP(s) on amino acid |
| type	| Type of mutation in the variant (e.g. single missense, synonymous, etc). Splice regions as classified by gnomAD. |
| WHO_class_2022	| WHO classification by 2022 system for variants with activity measured in 3 or more unrelated individuals |
| WHO_class_1985 |	WHO classification from 1985 system; unknown_function if not known. Rare assignments of two levels (e.g. I-II) listed as lower level. |
| class_1985_ref |	PMID for report that assigned WHO classification to variant |
| phenotype	| Most severe clinical phenotype reported for the variant from studies (in variant_molecular_info): deficiency, deficiency with acute hemolytic anemia (AHA), deficiency with chronic anemia (CNSHA). |
| molecular_info	| Number of studies on this variant (in variant_molecular_info) |
| activity_avg	| Fraction of normal activity of the variant from red blood cells of hemizygotes. Calculated as average activity from each study weighted by number of individuals studied. Data in variant_molecular_info. |
| activity_refs	| Number of references used to calculate average activity |
| stability	| Stability of variant. If studies in RBCs, model systems, and prediction, RBC stability is reported. Listed as "conflicting" if differing reports on stability in RBCs. |
| stability_refs	| Number of references used to determine stability |
| ClinVar_class	| Variant classification by ClinVar. For ones with two terms (e.g. "benign / likely benign"), only first term provided. |
| ClinVar_ID	| Variation ID associated with variant on ClinVar |
| ClinVar_stat |	Number of stars associated with variant review on ClinVar. Highest support is 4, lowest 0. NA indicates not on ClinVar. |
| ACMG_class |	Classification assigned to variant by applying ACMG guidelines (PMID 29300386) to available data. Evidence details in acmg_interpretation. |
| gnomAD2_freq |	Frequency of variant in gnomAD v2.1.1 |
| gnomAD3_freq |	Frequency of variant in gnomAD v3.1.1 |
| identified	| PMID of paper(s) that first identified the variant or determined its sequence. DOI or other citation provided for papers not indexed in PubMed. |

### variant_names.txt

Most common name and alternate names with genomic location. Spaces are replaced by an underscore and names separated by a semicolon.

### variant_molecular_info.txt

| Column | Description |
|--------|:------------|
| hg19_core	 | Genomic location of variant SNP/SNPs in hg19/GRch37 genome assembly |
| name	| Name or names given to variant. Some have multiple names preceding molecular characterization. |
| PMID	| PMID of reference. Citation given for papers not on PubMed. |
| phenotype	| Most severe clinical phenotype reported for the variant in the study: deficiency, deficiency with acute hemolytic anemia (AHA), deficiency with chronic anemia (CNSHA). |
| activity |	Determination if activity is increased, decreased, or normal |
| stability	| Determination if abundance or stability is increased, decreased, or normal |
| system	| Experimental or clinical system used to determine activity and abundance |
| info |	Summary of study findings on specified variant |
| activity_avg |	Average activity in RBC of hemizygotes |
| activity_n |	Number of hemizygotes used to determine average activity |

### variant_interpretation.txt

| Column | Description |
|--------|:------------|
| columns A-F	| Variant information from variant_catalog |
| columns G-Z	| Evidence codes from PMID 25741868 with supporting publications summarized for each variant |
| current	| Variant classification by ClinVar. For ones with two terms (e.g. "benign / likely benign"), only first term provided. |
| ACMG_2015	| Interpretation from evidence codes based on PMID 25741868 |
| OddsPath |	Odds of pathogenicity calculated as in PMID 29300386 |
| Post_P	| Calculated as in PMID 29300386, using Prior_P of 0.1 |
| ACMG_OP |	Interpretation from Post_P with cutoffs defined in PMID 29300386 |
