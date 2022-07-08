# InteraksiObat (Drug Interaction)

DRUG INTERACTION API USING THE NATIONAL LIBRARY OF MEDICINE USA DRUG BANK API

License : Free

Db Source : ONCHigh and DrugBank

Doc : https://lhncbc.nlm.nih.gov/RxNav/APIs/InteractionAPIs.html

To be able to look for drug interactions, there are two stages, namely:
1. Search for Drug Codes by using keywords Main Composition and not brand.
2. Testing Interactions Using the findInteractionsFromList REST API.
3. List of Drug Compositions is in the Item Composition Table of Infos in the composes column

Sample:

._____________________________________________________________________.

| Brand   | Type of Drug   | Main Composition  | Drug Code / rxnormId |

+---------+----------------+-------------------+----------------------+

| Mylanta | Ulcer Medicine | Aluminum Hydroxide| 612                  |

| Vitalex | Vitamin D3     | Cholecalciferol   | 2418                 |

+---------+----------------+-------------------+----------------------+

1. FIND DRUG CODES
2. TESTING INTERACTIONS

[ERP]
