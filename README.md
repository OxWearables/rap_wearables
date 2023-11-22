# Using wearables data on the RAP

## What is this repository?
This repository provides a **worked example of using wearables data available in UK Biobank for an analysis associating physical activity level with risk of incident cardiovascular disease**. Analyses are based on [this paper](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0169649) and [this paper](https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.1003487).


## What is this repository **not**? 
Analytic decisions should be made in the context of each research project. Choices in this repository reflect choices of the authors in the linked papers and the code authors, and should not be interpreted as definitive or widely generalisable. This repository is associated with the authors alone, and is not endorsed by UK Biobank.

## About this repository

This repository contains one Jupyter notebook for accessing data from the RAP, and three R markdowns for analysing this data with the RAP. These notebooks describe: 

- (1) Accessing data using the RAP
- (2) Preparing data for analysis
- (3) Exploring the wearables component of the data
- (4) Conducting an analysis associating physical activity level with risk of incident cardiovascular disease

Visual inspection of the data is invaluable for understanding what the code is doing. The worked example does not contain much visual inspection, to avoid printing participant data on the internet. Add statements to get a feel for the data as you work through the tutorials (e.g. `head()`, `str()` statements in R). But don't commit or publish results of these!

![image](https://user-images.githubusercontent.com/40437498/190090267-9c080819-73a1-4fa0-a82e-25bbd551d811.png)
*Illustration of the processing pipeline in this repository.*


## Instructions for Oxford CDT Course
These scripts were created for using during Oxford's CDT. If you are on the course, follow the below instructions.

The session on Thursday focuses on **accessing** the data. We will understand some of the non-accelerometer data available in UK Biobank, meet the [UK Biobank Research Analysis Platform](https://www.ukbiobank.ac.uk/enable-your-research/research-analysis-platform) and use it to prepare data for analysis. 

The session on Friday focuses on **running an epidemiological analysis** using data from UK Biobank. 

**Course Tutors:** Alaina Shreves, Adam Sturge, & Charlie Harper

## Information Governance and Security for Oxford CDT Course

When working with participant data, good Information Governance/Security is essential. Work with data **on the Research Analysis Platform only**. Do not download data onto your machine. Watch out for accidental data download e.g. a Jupyter notebook may inadvertently contain data (e.g. from printing parts of the data).  

## Practicalities: getting the notebooks onto the UK Biobank Research Analysis Platform for Oxford CDT Course

The UK Biobank Research Analysis Platform has permanent storage. In particular, you will be using a project called 'cdt-datachallenge-dec23'. Within the 'users' folder, you have an individual folder. Please store your files in that folder. When you first log in to the platform, you may wish to set up folders called 'data' and 'outputs' within this folder (some of the notebooks will assume you have done that). 

When you are running JupyterLab (or RStudio) on the RAP, you are temporarily running a cloud computer that has some temporary storage associated with it. You can transfer things from permanent storage to temporary storage and back again. **Important:** at the end of a session, before terminating your cloud computer, you need to make sure anything you need from the temporary storage is transferred over to permanent storage. If not, it will be gone! 

There are different ways you could get the practical materials from GitHub onto the Research Analysis Platform. Here's one: 

I. Launch JupyterLab + Spark (as you will need for the Thursday practicals)  Read how to set it up [here](https://dnanexus.gitbook.io/uk-biobank-rap/working-on-the-research-analysis-platform/using-spark-to-analyze-tabular-data).

II. Open a Terminal instance from JupyterLab (File > New > Terminal) 

III. Clone the repository by running: 
```shell
$ git clone https://github.com/OxWearables/rap_wearables.git # need to use https clone as ssh clone doesn't seem to be set up
```

IV. Note that this has put the repository into *temporary storage only*. If you want to be able to access it after the session, you'll still need to upload it to permanent storage. 

V. To work with the repository, change the directory into the repository and check out the relevant branch: 

```shell
$ cd rap_wearables
$ git checkout cdt_dec_2022 # This branch has some minor changes relative to main making it more suitable for our work this week 
$ cd .. # We go back up one level just so as to avoid filling the rap_wearables repo with data etc
```

VI. You can now run notebooks from the repository and edit them as you like. 

VII. At the end of the session, you can upload to permanent storage (your user folder!) by running (again in the terminal): 
```shell
$ dx upload -r rap_wearables --dest users/ahshreves/ # Remember to change my username to yours! Also don't miss the trailing slash. 
# dx is a command line client produced by DNANexus
```

Alternatively, if you already have things in permanent storage (e.g. having previously run through the steps above), you can download them to your temporary instance using: 

```shell
$ dx download -r users/ahshreves/rap_wearables # again change the file path as appropriate
```

## Getting files between the VM and the RAP using the command line interface 

This is **not** part of the practical. However, in the data challenge you may find you need to transfer files between the VM and the RAP. These instructions introduce how you can do that with the Command Line Interface. 

### Aim for Oxford CDT Course

These notes are for you if you:
- want to upload a file to the RAP from the VM
- want to download a file from the RAP to the VM


We are going to use the command line interface to transfer the file directly and securely from the VM to the RAP. 

**Reasons you might want to upload a file to the RAP:** You have processed the accelerometer data on BMRC (yay!) and can access a summary file containing the accelerometer phenotypes on your VM. You now want to upload it to the RAP to link it with other participant data.

**Reasons you might want to download a file from the RAP:** PLEASE DO NOT DO THIS IN GENERAL! But, you may want to download a text file containing participant IDs in your cohort from the RAP to your VM so you only process the subset of accelerometer data you need. 



### Steps for Oxford CDT Course

1. Login to the VM and complete all steps below on the VM.

2. Ensure your existing conda environment is activated by running: `conda activate wearables_workshop`. 

3. Run `pip3 install dxpy` ([Downloads - DNAnexus Documentation](https://documentation.dnanexus.com/downloads))). You may find you need to update pip: `pip install --upgrade pip`.

4. Navigate to the directory containing the files you need locally*.

5. Run `dx login` to log you in to the RAP ([Command Line Quickstart - DNAnexus Documentation](https://documentation.dnanexus.com/getting-started/cli-quickstart). You will need to enter your username and password. You may also have to select the project you want. 

6. Run `dx cd users/ahshreves` to navigate between directories on the RAP. [This is just an example - navigate to the folder you want, not to my folder :)] You can read more about the dx command line interface in the links, but you can also run other commands prefaced by dx (e.g. `dx ls`) 

7. To download the file my_eid_list.txt, run `dx download my_eid_list.txt`. 

8. To upload the file accelerometer_summary.csv, run `dx upload accelerometer_summary.csv`. [Note the similarities with how you work with files in the temporary storage on a cloud instance.]

9. Logout using `dx logout`. Your file should now be downloaded/ uploaded. 


*This is not strictly necessary. You can navigate between directories or control it using filepaths later. But this keeps it simple. 

## Troubleshooting and bugs for Oxford CDT Course

If you have a question, speak to any of the tutors (Alaina Shreves, Adam Sturge, & Charlie Harper).

There are probably bugs. If you find them, please let us know!

We'd also love to hear any suggestions for how we could improve these practicals for future students.

## Reading and useful links for Oxford CDT Course

Lots of online resources are available to understand the UK Biobank study and the Research Analysis Platform. Some are linked to within the individual tutorials, but some more general resources are listed here. Please do spend some time exploring them - this will be useful both now and in the Data Challenge! 


- To find out more about particular UK Biobank variables, use the [Data Showcase](https://biobank.ndph.ox.ac.uk/ukb/). It's well worth spending some time exploring this.
- For more about UK Biobank data collection and history, [this](https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.1001779) is a good summary
- To understand some of the potential for selection bias in UK Biobank, perhaps start with [Fry et al, 2017](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5860371/)
- Documentation for the Research Analysis Platform: https://dnanexus.gitbook.io/uk-biobank-rap/
- The DNANexus community is an online collaborative space where researchers can ask questions: https://community.dnanexus.com/s/ (useful for troubleshooting)


## Question? Bugs?

If you have a question, feel free to add an issue on GitHub or email [Alaina Shreves](mailto::alaina.shreves@wadham.ox.ac.uk). 

There are probably bugs. If you find them, please let us know! Again, add an issue on GitHub or email [Alaina Shreves](mailto::alaina.shreves@wadham.ox.ac.uk). 

## Credits

This worked example draws on several earlier examples and tutorials: 

- https://dnanexus.gitbook.io/uk-biobank-rap/working-on-the-research-analysis-platform/using-spark-to-analyze-tabular-data
- https://github.com/dnanexus/OpenBio/blob/master/UKB_notebooks/ukb-rap-pheno-basic.ipynb

It was written by [Rosemary Walmsley](mailto::rosemary.walmsley@bdi.ox.ac.uk) and Junayed Naushad, with contributions and advice from Ondrej Klempir, Aiden Doherty, and Ben Busby.

Changes to this repo have been made for the 2023 CDT cohort by Alaina Shreves and Aidan Acquah.

If you use this repo for a research paper, please cite: 
- Ramakrishnan R, Doherty A, Smith-Byrne K, Rahimi K, Bennett D, Woodward M, Walmsley R, Dwyer T (2021) [Accelerometer measured physical activity and the incidence of cardiovascular disease in the UK: Evidence from the UK Biobank cohort study.](https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.1003487) PLOS Medicine 18(1): e1003487

If you use this repo for a technical report, please cite:
- Walmsley R, Naushad J, Klempir O, Busby B and Doherty A. **rap_wearables** (2022), URL: https://github.com/OxWearables/rap_wearables. 

