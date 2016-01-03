## Obesity Comorbidity Analysis


### Objective

Perform comorbidity analysis for obesity based on Medical Subject Headings (MeSH) descriptors that are used to index biomedical literature in PubMed/MEDLINE (http://www.ncbi.nlm.nih.gov/pubmed)


### Materials

- Tools
  - [Python](https://www.python.org)
  - [IPython](http://ipython.org)
  - [Jupyter notebook](http://jupyter.org)
  - [PostgreSQL](http://www.postgresql.org)
- Services
  - [AWS RDS](https://aws.amazon.com/rds/)
- Data
  - PubMed/MEDLINE records via [NCBI E-Utilities](http://www.ncbi.nlm.nih.gov/books/NBK25501/)
  - [MeSH Vocabulary](https://www.nlm.nih.gov/mesh/)
  - [Unified Medical Language System (UMLS) Semantic Types](http://semanticnetwork.nlm.nih.gov/)


### Methods

The goal of the analysis is to explore the diseases or syndromes that co-occur with obesity. To measure comorbidity using the PubMed database, articles published between 2000 and 2012 were retrieved with 'obesity' as a MeSH Major Topic. Biopython's Entrez package allows interactions with NCBI's E-utilities and their databases. PubMed article ID, article titles, author names, MeSH descriptors and publication year were extracted from the articles matching the query. MeSH descriptors include, among other things, diseases and syndromes that are also contained in the article as a major topic. To select only the Diseases and Syndromes from the MeSH descriptors a mapping of the MeSH descriptors and the Unified Medical Language System Semantic Types was created. The MeSH vocabulary file contains, among other things, the MeSH descriptor and a semantic type id that the descriptor belongs to (in the format 'T011'). The UMLS semantic type file contains the same id and the corresponding semantic type. Using that id as key the files can be mapped. After mapping those files, the articles where the MeSH descriptor maps to the semantic type 'Disease or Syndrome' were selected and counted.
See the [source code](https://github.com/fernandogelin/comorbidity-analysis/blob/master/comorbidity-analysis.ipynb) for detailed analysis.


### Results

The results of the analysis are not surprising.  The disease that most co-occur with obesity is Diabetes Mellitus, Type 2. As shown in the figure below, Diabetes Mellitus, Type 2 occurs almost twice as much as the next most common obesity comorbidity. This means, that in most cases, obesity is related to a self-inflicted disease.

![Figure 1. Fifteen most common obesity comorbidities](images/comorbidities.png)

The dataset corresponds to all articles on PubMed between 2000 and 2012, and thus includes studies on subjects of different ages. To further explore the dataset and check if Diabetes Mellitus, Type 2 is more common in older people, as it is expected, the MaSH descriptors age gorups were extracted from the articles. The figure below shows the percentage of articles for each of the top 15 obesity comorbidities divided by age group.

![Figure 2. Fifteen most common obesity comorbidities](images/comorbidities_by_age.png)
