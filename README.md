# Characterization and Comparison of Topics and Top Words in the H2-A Job Postings 
This repo contains the final project that I did with two other peers in Dartmouth QSS20: Modern Statistical Computing. This project explored the textual data from the H-2A job postings with the goal of modeling and identifying common themes and topics across the postings, which help to more easily and accurately detect future violations and further ensure the rights of the guest workers. 

# Data 

- `H-2A_Disclosure_Data` is a [public data source of H-2A job postings](https://www.dol.gov/agencies/eta/foreign-labor/performance) from the Department of Labor (DOL). 
- `FOIA_2021-F-05932_raw_data` is the processed data from a Freedom of Information Act (FOIA) request 
- The combined zip includes combined data (across fiscal years) for the Disclosure/H-2A job postings from the DOL. All other combined data is stored in the dropbox below.

All data too large for this repo are stored in the shared Dropbox folder: `qss20_finalproj_rawdata/textasdata/`

# Code

- [00_rowbinddata.ipynb](https://github.com/euniceyliu/TextAnalysis/blob/main/code/00_rowbinddata.ipynb)
  - Takes in following files stored on Github or in Dropbox:
    - `H-2A_Disclosure_Data`: data containing FY 2020 and FY 21 Q1 H2A job clearances
    - `FOIA_2021-F-05932_raw_data.xlsx`: data from FOIA request on addendums; stored in a couple sheets
  - What it does:
    - Reads in the different job disclosure datafiles and rowbinds
    - Rowbinds the different files of the Excel addendums sheet
  - Outputs to Dropbox:
    - `H-2A_Disclosure_Data_FY_combined_202021Q1.csv`: rowbound job disclosures
    - `FOIA_2021-F-05932_raw_data_combined_202021Q1.csv`: rowbound job addendums

- [01_sampledescriptives.ipynb](https://github.com/euniceyliu/TextAnalysis/blob/main/code/01_sampledescriptives.ipynb)

  - Takes in::
    - Rowbound outputs of previous scripts
  - What it does:
    - Concatenates addendums within the same job clearance number (`CASE_NUMBER`) across sections
    - Detects for Spanish phrases and removes aggregated addendums with any Spanish
    - Left joins job disclosures to addendums and creates indicator for disclosures without any text addendum
    - Compares attributes of jobs with and without addendums
    - For text analysis, does inner join of disclosures to addendums (so only retains jobs with English addendums)
  - Outputs to Dropbox:
    - `merged_addendums_jobdisclosures[csv|pkl]`: csv and pkl format of inner join for text analysis

- [02_textpreprocess_topicmod.ipynb](https://github.com/euniceyliu/TextAnalysis/blob/main/code/02_textpreprocess_topicmod.ipynb)

  - Takes in::
    - Merged jobs and addendums from previous script
  - What it does:
    - Calculates top words in each corpus
    - Provides a template to investigate  top words of interest
    - Creates a topic model using Linear Discriminant Analysis (LDA) algorithm
    - Creates visualizations of top words for given topics




