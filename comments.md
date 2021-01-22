# 1. Result of the project
- [FACTOR 1 FY2018](https://github.com/ericaosta/alagant/blob/main/F1/factor1_FY2018.xlsx)
- [FACTOR 1 FY2019](https://github.com/ericaosta/alagant/blob/main/F1/factor1_FY2019.xlsx)
- [FACTOR 1 FY2020](https://github.com/ericaosta/alagant/blob/main/F1/factor1_FY2020.xlsx) 
- [FACTOR 1 FY2021](https://github.com/ericaosta/alagant/blob/main/F1/factor1_FY2021.xlsx)
# 2. What steps did you take to achieve this result?
In brief, I scraped [ISACA CMMI Appraisal System](https://cmmiinstitute.com/pars/?StateId=33296d0d-c5c5-4d47-b36b-c692d73a5ab7) and filtered companies with ML3 or greater. This step yielded a [list of companies with CMMI status from the entire world](https://github.com/ericaosta/alagant/blob/main/F1/CMMI_RAW_WORLD.xlsx). Next, I standardized the company names using regular expressions ("regex") and used [the "standarized" list of companies with CMMI status](https://github.com/ericaosta/alagant/blob/main/F1/CMMI.xlsx) to match to a second (similarlily regex-standardized) [list of companies with SAM](https://github.com/ericaosta/alagant/blob/main/F1/company-unique-list.xlsx) in order to match companies with SAM, CMMI status, and DUNS. The joined sets of data yielded a [list of companies with SAM, CMMI status, and DUNS](https://github.com/ericaosta/alagant/blob/main/F1/SAM_CMMI.xlsx), which can then be used to match to other federal databases (e.g., awards, etc.) Next, I mined awards data from multiple fiscal years found in [usaspending.gov](https://www.usaspending.gov/download_center/award_data_archive). I filtered awards from companies that met SAM and CMMI criteria. Next, I cleaned the awards data to search for specific keywords (e.g., CLOUD, AWS, UFMS, MIGRAT, etc.) to meet criteria 3, 4, and 5. And lastly, the companies that met criteria 3-5 were (inner) joined. The select few companies were checked for ISO 9001:2015 certification manually (criterion 2). More details and the corresponding code can be found here: [Factor 1 by Fiscal Year](https://github.com/ericaosta/alagant/blob/main/F1/F1.md).
# 3. What mistakes did you do?
- Problem: I mistakenly assumed that the [ISACA CMMI Appraisal System](https://cmmiinstitute.com/pars/?StateId=33296d0d-c5c5-4d47-b36b-c692d73a5ab7) contained accurate, organized, and up-to-date information. After my first preliminary code, I realized that the SAM status and country categorization from this website were incorrect.
  - Solution: I scraped ALL of the data with no categorization and only focused on CMMI status. Before matching CMMI data to SAM data, I filtered SAM data to only USA-only companies in order to find the companies with CMMI only in the USA. In addition, I developed these regular expressions ("regex") to "standarize" a pattern between company names. It is important to standarize company names because some website that we will scrap may have company names but not DUNS. Therefore, we can use this tool to analyze government data (e.g., [sam.gov](https://www.sam.gov/SAM/), [usaspending.gov](https://www.usaspending.gov) with other sites, such as [cmmiinstitute.com](https://cmmiinstitute.com), where we can find companies and their CMMI Level status).
- Problem: Running "costly" (i.e., takes up much RAM) code. A great example is downloading and processesing award data (14 GB per fiscal year). 
  - Solution: I wrote a more deliberate, step-by-step code that helped me keep track of every single one step in the approach while optimizing my machine's performance. 
# 4. What in your opinion you could have done better?
The success-determining step in my approach is the regex used to standardize company names. I believe that with time, attention-to-detail, and pattern-recognition between company names, I will continue to refine this tool that will allow us to mine and match company information from federal and non-federal sources successfully. 