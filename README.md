# Using wearables data on the RAP

## What is this repository?
This repository provides a **worked example of using wearables data available in UK Biobank for an analysis associating physical activity level with risk of incident cardiovascular disease**. Analyses are based on [this paper](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0169649) and [this paper](https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.1003487).

## What is this repository **not**? 
Analytic decisions should be made in the context of each research project. Choices in this repository reflect choices of the authors in the linked papers and the code authors, and should not be interpreted as definitive or widely generalisable. This repository is associated with the authors alone, and is not endorsed by UK Biobank.

## About this repository

This repository contains four Jupyter notebooks for analysing wearables data with the RAP. These notebooks describe: 

- (1) Accessing data using the RAP
- (2) Preparing data for analysis
- (3) Exploring the wearables component of the data
- (4) Conducting an analysis associating physical activity level with risk of incident cardiovascular disease

Code in this repository is a mixture of Python and R. Aside from the first notebook, which is run using a Spark cluster setup on the RAP system where R is not currently available, this reflects personal choice.

Visual inspection of the data is invaluable for understanding what the code is doing. The worked example does not contain much visual inspection, to avoid printing participant data on the internet. Add statements to get a feel for the data as you work through the tutorials (e.g. `head()`, `str()` statements in R). But don't commit or publish results of these!

![image](https://user-images.githubusercontent.com/40437498/190090267-9c080819-73a1-4fa0-a82e-25bbd551d811.png)
*Illustration of the processing pipeline in this repository.*

## Question? Bugs?

If you have a question, feel free to add an issue on GitHub or email [Rosemary Walmsley](mailto::rosemary.walmsley@bdi.ox.ac.uk). 

There are probably bugs. If you find them, please let us know! Again, add an issue on GitHub or email [Rosemary Walmsley](mailto::rosemary.walmsley@bdi.ox.ac.uk). 

## Credits

This worked example draws on several earlier examples and tutorials: 

- https://dnanexus.gitbook.io/uk-biobank-rap/working-on-the-research-analysis-platform/using-spark-to-analyze-tabular-data
- https://github.com/dnanexus/OpenBio/blob/master/UKB_notebooks/ukb-rap-pheno-basic.ipynb

It was written by [Rosemary Walmsley](mailto::rosemary.walmsley@bdi.ox.ac.uk) and Junayed Naushad, with contributions and advice from Ondrej Klempir, Aiden Doherty, and Ben Busby.

If you use this repo for a research paper, please cite: 
- Ramakrishnan R, Doherty A, Smith-Byrne K, Rahimi K, Bennett D, Woodward M, Walmsley R, Dwyer T (2021) [Accelerometer measured physical activity and the incidence of cardiovascular disease in the UK: Evidence from the UK Biobank cohort study.](https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.1003487) PLOS Medicine 18(1): e1003487

If you use this repo for a technical report, please cite:
- Walmsley R, Naushad J, Klempir O, Busby B and Doherty A. **rap_wearables** (2022), URL: https://github.com/OxWearables/rap_wearables. 
