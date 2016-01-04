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

The goal of the analysis is to explore the diseases or syndromes that co-occur with obesity. To measure comorbidity using the PubMed database, articles published between 2000 and 2012 were retrieved with 'obesity' as a MeSH Major Topic. Biopython's Entrez package allows interactions with NCBI's E-utilities and their databases. PubMed article ID, article titles, author names, MeSH descriptors and publication year were extracted from the articles matching the query. MeSH descriptors include, among other things, diseases and syndromes that are also contained in the article as a major topic. To select only the Diseases and Syndromes from the MeSH descriptors, a mapping of the MeSH descriptors to the Unified Medical Language System Semantic Types was created. The MeSH vocabulary file contains, among other things, theMeSH descriptor and a semantic type ID that the descriptor belongs to (in the format `T011`). The UMLS semantic type file contains the same ID and the corresponding semantic type. Using the ID as key the files may be mapped. Articles were then counted for each MeSH descriptor with corresponding semantic type `Disease or Syndrome`.
See the [source code](https://github.com/fernandogelin/comorbidity-analysis/blob/master/comorbidity-analysis.ipynb) or the [notebook on nbviewer](http://nbviewer.ipython.org/github/fernandogelin/comorbidity-analysis/blob/master/comorbidity-analysis.ipynb) for detailed analysis.


### Results

The results of the analysis are unsurprising. The disease that most co-occurs with obesity is Diabetes Mellitus, Type 2. As shown in the figure below, Diabetes Mellitus, Type 2 is almost twice more frequently associated to obesity than the next most common comorbidity. Meaning that in many cases obesity can be associated to a preventable disease.

![Figure 1. Fifteen most common obesity comorbidities](images/comorbidities.png)

To further explore the dataset and see if that pattern changes for different age groups, the MaSH descriptors for age groups were extracted. The figure below shows the proportion of articles for each of the top 15 comorbidities divided by age group. The figure shows that Pregnancy Complications are possibly related to obesity in newborns, Asthma is a common comorbidity for children, Diabetes Mellitus Type 2 is related to obesity in great proportions during adulthood, which is also when more diseases appear.

![Figure 2. Fifteen most common obesity comorbidities](images/comorbidities_by_age.png)
