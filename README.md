# 🔬📋 PubMedDigest - Medical Literature Summary Generator
Stay up to date on the medical research that matters to you with this AI tool, which creates monthly digests on papers related to any medical topic of your choosing.

## Examples

For instance, here are sample summaries for various topics sourced from June-July 2025:

- [Hip osteoarthritis](examples/07-20-2025_hip%20osteoarthritis_summary.md)
- [Diabetic polyneuropathy](examples/07-20-2025_diabetic%20polyneuropathy_summary.md)
- [Systemic sclerosis](examples/07-20-2025_systemic%20sclerosis_summary.md)
- [Carpal tunnel syndrome](examples/07-20-2025_carpal%20tunnel%20syndrome_summary.md)

## Overview

`PubMedDigest` streamlines medical literature review by automatically generating customized digest documents on any medical topic. Here's how it works:

1. Uses PubMed's API to find recent papers (over a customized timeframe) on your chosen medical topic
2. Leverages an LLM to:
   - Categorize papers (RCTs, observational studies, meta-analyses, etc.)
   - Generate concise summaries from each paper's abstract
3. Creates a structured document with:
   - Papers organized by category
   - Brief summaries of key findings
   - Direct links to PubMed entries

This tool helps medical professionals and researchers:
- Stay current with the latest research in their field
- Quickly identify relevant papers worth reading in depth
- Save time compared to manual PubMed searches
- Get a high-level overview of recent developments

The digest format makes it easy to scan through recent literature and focus on the papers most relevant to your interests.

## How to Use PubMedDigest

This repository shares the notebook for the PubMedDigest tool

Prior to running the program, you will need to:
1. Install the dependencies: `pip install -r requirements.txt`
2. Have an OpenAI API key
2. Create a .env file, and add your OpenAI key: `OPENAI_API_KEY= <your OpenAI key>`
4. Create a PubMed Entrez account and API key.
  > - Entrez accounts are free and can be created at https://account.ncbi.nlm.nih.gov. 
  > - API keys can be generated at https://account.ncbi.nlm.nih.gov/settings/


In the first notebook cell, you will need to provide the following information:

1. Your search topic
    > Choose a specific medical topic to focus your search. For broad topics like "diabetes" or "cancer", consider:
    > - Adding specific qualifiers (e.g., "Type 2 diabetes prevention")
    > - Using a shorter date range to limit results (down to weeks for very broad topics)
    
2. Date range for the search
    > Specify start and end dates to search for papers published within that timeframe
    
3. Maximum number of papers (default: 30)
    > Limits the total papers retrieved. While you can increase this number, larger searches:
    > - Take longer to process
    > - May hit PubMed API rate limits
    > - Could result in higher API costs
    
4. Your PubMed credentials
    > - Entrez account email address
    > - PubMed API key

After entering these details, run all cells in the notebook. The program will generate a digest document named `YYYY-MM-DD_topic_summary.md` in your working directory.

Note: As part of the program process, 2 other documents are created to aid the LLM in making the final digest document.
* `PubMed_results.md` - This is all of the extracted data from PubMed for your search (includes abstracts)
* `YYYY-MM-DD_topic_categorization.md` - This is the paper categorization performed by the LLM
