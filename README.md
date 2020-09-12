
# Upload-or-Publish

Micro-API to query a COVID-19 preprint's publication status

## UoP API

The micro-API service hosted on PythonEverywhere offers a free, programmatic way for a client to make a query on a COVID-19 preprint's (or a batch of COVID-91 preprints) publication status. The API return a JSON dictionary with CORD-19's enhanced metadata. If the preprint's publication status is positive, then, the API return a JSON containing metadata pertaining to the published article. The UoP API, at least in its current implementation, require no keys/authentication. But please be mindful of the fact that this is an unfunded initiative run by a single person.

This tool is currently in its beta-version. It is in active development.

## Preprint Coverage

The current version (vbeta) covers three preprint servers: arXiv, bioRxiv, and medRxiv. I use Covid-19 Open Research Dataset (CORD-19) to match preprints from those three repositories with their final published counterpart. As we know, there are dozens upon dozens of online preperint repositories. Therefore, one of my first goal is to extend UoP's repo coverage. NIH iSearch COVID-19 publication database is a great first step in that direction since it includes three preprint servers not coverated by the CORD-19 dataset, namely, ChemRxiv, SSRN, and ResearchSquare.

## Institutional User

Adding your preprint server to UoP

If you are the manager/admin/developer in charge of a preprint repository and you would like to see 'your' COVID-19 preprint manuscripts' metadata added to the UoP API please email [me](f.lachapelle@alumni.ubc.ca). In a nutshell, what I would need is a CSV containing all your COVID-19 preprints's metadata (title, authors, doi, etc..) using CORD-19 metadata formatting. I am aware that some preprint repositories have API capabilities, but at this point, I am NOT planning to extend the UoP coverage by scraping websites or building API pipelines. I do not have the ressources nor the time to accomplish that kind of data architecture.

Adding functionalities to UoP

The current querying functions of the API are rather limited (see documentation below). If you have suggestions about a function you would like to use, please feel free to contact [me](f.lachapelle@alumni.ubc.ca).

## Methodology

* for more details on the methodology used to generate preprints' publication status, please see [my medRxiv preprint paper here](https://www.medrxiv.org/content/10.1101/2020.09.04.20188771v1).

## TO-DO

1.
2.


## Context

As the COVID-19 pandemic persists around the world, the scientific community continues to produce and circulate knowledge on the deadly disease at an unprecedented rate. During the early stage of the pandemic, preprints represented nearly 40% of all English-language COVID-19 scientific corpus (6, 000+ preprints | 16, 000+ articles). As of mid-August 2020, that proportion dropped to around 28% (13, 000+ preprints | 49, 000+ articles). Nevertheless, preprint servers remain a key engine in the efficient dissemination of scientific work on this infectious disease. But, giving the ‘uncertified’ nature of the scientific manuscripts curated on preprint repositories, their integration to the global ecosystem of scientific communication is not without creating serious tensions. This is especially the case for biomedical knowledge since the dissemination of bad science can have widespread societal consequences.

## Data Etiquette

In the spirit of open science, and especially in the context of the COVID-19 pandemic, I develop a free API. I am running this out of my own pocket. My current plan with Python Everything allows for 100, 000 API queries per day. I strongly encourage intelligent and mindful users. Don't be stupid. Don't query the same data-point over and over. Don't use over-kill parallel processing that will overload the server. If you notice that your requests are not working anymore, just stop your program, ok! Finally, please use a user-agent header that identify you as a user, including your email. I reserve the right to restrict or block clients that are wont follow this etiquette.

I used "rxvist.org/docs" for this section. Please note that "rxvist" draw from the Crossref API documentation.

## How to cite UoP API

If you use UoP data in your research, please cite:

[Upload-or-Publish](https://www.medrxiv.org/content/10.1101/2020.09.04.20188771v1), Lachapelle, F. (2020). COVID-19 Preprints and Their Publishing Rate: An Improved Method. medRxiv. 1-34. doi: https://doi.org/10.1101/2020.09.04.20188771.

[CORD-19 Project](https://arxiv.org/abs/2004.10706), Wang, L. L., Lo, K., Chandrasekhar, Y., Reas, R., Yang, J., Eide, D., ... & Mooney, P. (2020). CORD-19:The Covid-19 Open Research Dataset. ArXiv.

## How to use the UoF API {beta}

The current beta-version only allows one route "http://heibufan.pythonanywhere.com/json/pp_meta/doi"

For example, if a client want to determine the publication status of a specific COVID-19 preprint, using the doi, the url should be:
http://heibufan.pythonanywhere.com/json/pp_meta/10.1101/2020.03.19.998179

The returned JSON will look like this:

The most important returned metadata is match_status: True=preprint has a peer-reviewed published counterpart; False=preprint doesnt have one (see documentation below).

```json
{"result": {"indx_pp": 11811,
            "indx_pr": 26,
            "ti_pp": "molecular characterization of sars-cov-2 in the first covid-19 cluster in france reveals an amino-acid deletion in nsp2 (asp268del)",\
            "ti_pr": "molecular characterization of sars-cov-2 in the first covid-19 cluster in france reveals an amino acid deletion in nsp2 (asp268del)",\
            "fuzz\score": 99,\
            "no_fuzz\_test": 1,\
            "no_fuzz\_test\_above": 1,\
            "prop_au\_match": 1.0,\
            "z_fuzzy\_test\_history": [],\
            "au\_pp": "Bal, Antonin; Destras, Gr\u00e9gory; Gaymard, Alexandre; Bouscambert-Duchamp, Maude; Valette, Martine; Escuret, Vanessa; Frobert, Emilie; Billaud, Genevi\u00e8ve; Trouillet-Assant, Sophie; Cheynet, Val\u00e9rie; Brengel-Pesce, Karen; Morfin, Florence; Lina, Bruno; Josset, Laurence",\
            "au\_pr": "Bal, A.; Destras, G.; Gaymard, A.; Bouscambert-Duchamp, M.; Valette, M.; Escuret, V.; Frobert, E.; Billaud, G.; Trouillet-Assant, S.; Cheynet, V.; Brengel-Pesce, K.; Morfin, F.; Lina, B.; Josset, L.",\
            "source\_x\_pp": "biorxiv",\
            "source\_x\_pr": "pmc",\
            "journal\_pp": "bioRxiv",\
            "journal\_pr": "Clin Microbiol Infect",\
            "pub\_time\_pp": "3/21/2020",\
            "pub\_time\_pr": "3/28/2020",\
            "cord\_uid\_pp": "wnh6h9f0",\
            "cord\_uid\_pr": "4c0zwhdh",\
            "sha\_pp": NaN,\
            "sha\_pr": NaN,\
            "pmcid\_pp": NaN,\
            "pmcid\_pr": "PMC7142683",\
            "pubmedid\_pp": NaN,\
            "pubmedid\_pr": 32234449.0,\
            "doi\_pp": "10.1101/2020.03.19.998179",\
            "doi\_pr": "10.1016/j.cmi.2020.03.020",
            "diff\_day": 7,\
            "internal\_method": "fuzzy",\
            "match\_status": true,\
            "cord\_19\_version": "2020_08_12",\
            "fuzzy\_matching\_date": "2020_08_12"}}\
```

## How to use the UoF API {beta} - Simple Code Example in Python

```python

import json
import requests
from bs4 import BeautifulSoup

UoP_url_base = 'http://heibufan.pythonanywhere.com/json/pp_meta/'

l_pp_to_query = ['10.1101/2020.03.19.998179', doi2, doi3, etc]

for pp__doi in l_pp_to_query:

    url_query = f'{UoP_url_base}{pp_doi}'
    raw_data = requests.get(url_query)
    if raw_data.status_code!=200:
        raise Exception("HTTP code " + str(raw_data.status_code))
    json_data = json.loads(raw_data.text)
```

## Documentation

The most important returned metadata is match_status: True=preprint has a peer-reviewed published counterpart; False=preprint doesnt have one.

'pp' stands for preprint\
'pr' stands for peer-review\
'(c)' indicates that the metadate comes from the CORD-19 dataset\


"indx\_pp": internal working id for admin\
"indx\_pr": internal working id for admin\
"ti\_pp": title of preprint (c)\
"ti\_pr": title of published/peer-review counterpart (c)\
"fuzz\_score": fuzzy logic score yields from comparing both titles\
"no\_fuzz\_test": total number (raw) of fuzzy mathing score produced (see methods)\
"no\_fuzz\_test\_above": total number of fuzzy matching produced that were above the cut-off point of 0.60\
"prop\_au\_match": proportion of preprint's authors' last names that was found in the list of authors of the pr article\
"z\_fuzzy\_test\_history": list/array of results of all fuzzy matching tests performed if >1\
"au\_pp": list of authors (preprint) (c)\
"au\_pr": list of authors (published version) (c)\
"source\_x\_pp": bibliometric source where CORD-19 got metadata from (c)\
"source\_x\_pr": ibid.\
"journal\_pp": journal venue (c)\
"journal\_pr": ibid.\
"pub\_time\_pp": date of preprint upload (c); note: a preprint can have multiple uploaded versions. Still need to validate that CORD-19 always use v1 date\
"pub\_time\_pr": date of peer-reviewed article's publication (c)\
"cord\_uid\_pp": preprint's id (c)\
"cord\_uid\_pr": peer-review's id (c)\
"sha\_pp": id and name of pdf json of preprint (c)\
"sha\_pr": id and name of pdf json of article (c)\
"pmcid\_pp": pub med central id (c)\
"pmcid\_pr": ibid.\
"pubmedid\_pp": pub med id (c)\
"pubmedid\_pr": pub med id (c)\
"doi\_pp": digital unique identifier note: arXiv doesnt automatically generate doi for the preprint manuscripts its curated. (see methods)\
"doi\_pr": ibid.\
"diff\_day": difference in day between preprint upload and final publication\
"internal\_method": (see methods)\
"match\_status": True: pp has a pr, False: pp has no pr\
"cord\_19\_version": version of CORD-19 dataset used for matching algo.\
"fuzzy\_matching\_date": date when the fuzzy matching code was performed

## Contributing

Please feel free to email [me](f.lachapelle@alumni.ubc.ca) if you have any questions or if you are interested in contributing.

## Authors

* Francois Lachapelle - subFIELD.lab | PhD Cand. University of British Columbia, Vancouver, Canada

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

At its foundation, this project is a Record Linkage initiative. Therefore, it would not be possible without the great work of researchers at:

[CORD-19 Project](https://arxiv.org/abs/2004.10706), Wang, L. L., Lo, K., Chandrasekhar, Y., Reas, R., Yang, J., Eide, D., ... & Mooney, P. (2020). CORD-19:The Covid-19 Open Research Dataset. ArXiv.

For advisory support:

* Adam Howe - Statistics Canada | UBC

For inspirational support (as in, ah ok, building an API is cool and doable)

* Elian Carsenat - NAMSOR
* Abdill RJ, Blekhman R. - Rxivist

For moral support:

* Heather Thom - Simon Fraser University
* Philippe Lachapelle - Centre Hospitalier Universitaire de Quebec

