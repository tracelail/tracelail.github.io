---
layout: post
title: "Managing Large Files in Bioinformatics Projects"
date: 2025-02-20
category: blog
---

# Managing Large Data Files in Bioinformatics Projects


## The Challenge: Large Data Files in Version Control

GitHub has strict file size limitations:
- Individual files must be under 100MB
- Repositories have a strict size limit of 100GB
- Recommended repository size is under 5GB for optimal performance

In bioinformatics, we frequently work with large data files such as:
- FASTQ sequencing files (often multiple GB each)
- BAM/SAM alignment files
- Reference genomes

Attempting to commit these files directly to Git will likely result in errors.<br> 
<br>
Even commiting large files to you local repository before pushing to Git can create a large headache. I personally found this out by making multiple commits with the GRCh38 in one of my files.

## Your options

1. Delete large files before you commit
    - example: keeping all large files in a `tmp` folder and then clearing it before you commit
<br> or <br>
2. Completely ignore certain types of files from being commited
    - example: using a config file like `.gitignore` to prevent certain files or folders from being commited

## My Solution: gitignore

I create a `.gitignore` file to simply ignore the large files (like fastq files) form being commited and pushed to Git. <br>
<br>
I find writing in a segment of code to clear my `tmp` folder or manually deleting files makes me prone to error. Creating a `.gitignore` when setting up my project allows me to make adjustments as I need but I also don't have to go back and clean old commits if I forgot to run a Jupyter cell or delete a file that accidentally got placed in a forgotten folder.


## Setting Up a .gitignore

The `.gitignore` file tells Git which files to ignore. 

Here's an example (don't copy paste this) `.gitignore` file for a bioinformatics project:


```
# Temporary files
*.tmp
*~
.DS_Store

# Large Data files
*.fastq
*.bam
*.vcf
*.bed

# Python-specific
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
env/
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
*.egg-info/
.installed.cfg
*.egg

# Jupyter Notebook
.ipynb_checkpoints

# R-specific
.Rhistory
.Rapp.history
.RData
.Ruserdata
```

# But I already have large files commited and have an error
If you are someone whom accidentally commited a large file or too many large files over multiple commits, like me, and now you're getting an error, check out [BFG repo cleaner](https://rtyley.github.io/bfg-repo-cleaner/)

# Considerations for your future self and others
Don't forget that one of the main benefits of creating a GitHub project is so that you and others can look back at the project and have a clear reference of what happened. Additionally you will likely need to have reproducible results.

## Document the data
It is important that document where you got your data and where it's located. I create a data `README.md` inside my data folder. Provide as much detail as possible, accession numbers, versions, file paths, screen shots, etc. No detail is too small. Trust me, you will thank yourself later.
- local data
    - example: your computer hard drive
    - provide a file path
    - make sure it is backed up
- Cloud server
    - example: AWS
    - Provide the S3 path
- Public data
    - example: ENSEMBL
    - List the organization as well as a web address


## Organization is your friend
If your project is organized you are setting yourself up for success. If you have an organized project directory, you likely have a plan, and you are more likely to document. Take the time to set up directory template that works for you if you or your team don't already have one.<br>
<br>
Here is the one I use (feel free to copy):

```
project/
├── README.md         # Project documentation
├── data/
│   ├── raw/          # Raw FASTQ files
│   ├── processed/    # Processed data
│   └── README.md     # Data documentation
├── code/
├── results/
|   ├── tables/       # csv files   
|   ├── figures/      # plots   
└── .gitignore        # Git ignore file
```

```
mkdir -p data/raw data/processed code results/tables results/figures && 
touch README.md data/README.md &&
touch .gitignore
```

# Conclusion
If you got this far, I hope this has helped. Hopefully I can help prevent the pain of errors that come with commiting large files and teach you that Git is for code... not data.