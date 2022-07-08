# InteraksiObat (Drug Interaction)

DRUG INTERACTION API USING THE NATIONAL LIBRARY OF MEDICINE USA DRUG BANK API
License : Free
Db Source : ONCHigh and DrugBank
Doc : https://lhncbc.nlm.nih.gov/RxNav/APIs/InteractionAPIs.html
Demo : https://psbb.id/interaksiobat/
To be able to look for drug interactions, there are two stages, namely:
1. Search for Drug Codes by using keywords Main Composition and not
brand.
2. Testing Interactions Using the findInteractionsFromList REST API.
3. List of Drug Compositions is in the Item Composition Table of Infos in the composes column
Sample Samples:
Market Brand Type of Drug Main Composition Drug Code /
rxnormId
Mylanta Ulcer Medicine Aluminum Hydroxide 612
Vitalex Vitamin D3 Cholecalciferol 2418
1. FIND DRUG CODES
findRxcuiByString
Information returned
Concepts with a specified name
Service domain
https://rxnav.nlm.nih.gov
HTTP requests
GET /REST/rxcui.json?name=medicinename
Parameter
name : Official Name / Main Composition in the drug. It is not case sensitive.
Sample Request
GET https://rxnav.nlm.nih.gov/REST/rxcui.json?name=Aluminum Hydroxide
Response
{
 "idGroup": {
 "rxnormId": [
 "2418"
 ]
 }
}
2. TESTING INTERACTIONS
findInteractionsFromList
Information returned
Interactions between a list of drugs
Service domain
https://rxnav.nlm.nih.gov
HTTP requests
GET /REST/interaction/list.json?rxcuis=medicine1<space>medicine2<space>etc.
Parameter
rxcuis : Drug Code response result from findRxcuiByString. Drug code is separated
use spaces. Maximum 50 items.
Sample Requests:
GET https://rxnav.nlm.nih.gov/REST/interaction/list.json?rxcuis=612 2418
Response:
// 20220610165258
// https://rxnav.nlm.nih.gov/REST/interaction/list.json?rxcuis=612%202418
{
 "nlmDisclaimer": "It is not the intention of NLM to provide specific medical
advice, but rather to provide users with information to better understand their
health and their medications. NLM urges you to consult with a qualified physician
for advice about medications.",
 "fullInteractionTypeGroup": [
 {
 "sourceDisclaimer": "DrugBank is intended for educational and scientific
research purposes only and you expressly acknowledge and agree that use of
DrugBank is at your sole risk. The accuracy of DrugBank information is not
guaranteed and reliance on DrugBank shall be at your sole risk. DrugBank is not
intended as a substitute for professional medical advice, diagnosis or
treatment..[www.drugbank.ca]",
 "sourceName": "DrugBank",
 "fullInteractionType": [
 {
 "comment": "Drug1 (rxcui = 2418, name = cholecalciferol, tty = IN).
Drug2 (rxcui = 612, name = aluminum hydroxide, tty = IN). Drug1 is resolved to
cholecalciferol, Drug2 is resolved to aluminum hydroxide and interaction asserted
in DrugBank between Cholecalciferol and Aluminum hydroxide. Drug1 is resolved to
cholecalciferol, Drug2 is resolved to aluminum hydroxide, dried (USP) and
interaction asserted in DrugBank between Cholecalciferol and Aluminum
hydroxide.",
 "minConcept": [
 {
 "rxcui": "2418",
 "name": "cholecalciferol",
 "tty": "IN"
 },
 {
 "rxcui": "612",
 "name": "aluminum hydroxide",
 "tty": "IN"
 }
 ],
 "interactionPair": [
 {
 "interactionConcept": [
 {
 "minConceptItem": {
 "rxcui": "2418",
"name": "cholecalciferol",
"tty": "IN"
 },
 "sourceConceptItem": {
 "id": "DB00169",
"name": "Cholecalciferol",
"url": "https://go.drugbank.com/drugs/DB00169#interactions"
 }
 },
 {
 "minConceptItem": {
 "rxcui": "612",
"name": "aluminum hydroxide",
"tty": "IN"
 },
 "sourceConceptItem": {
 "id": "DB06723",
"name": "Aluminum hydroxide",
"url": "https://go.drugbank.com/drugs/DB06723#interactions"
 }
 }
 ],
 "severity": "N/A",
 "description": "The serum concentration of Aluminum hydroxide can
be increased when it is combined with Cholecalciferol."
 },
 {
 "interactionConcept": [
 {
 "minConceptItem": {
 "rxcui": "2418",
"name": "cholecalciferol",
"tty": "IN"
 },
 "sourceConceptItem": {
 "id": "DB00169",
"name": "Cholecalciferol",
"url": "https://go.drugbank.com/drugs/DB00169#interactions"
 }
 },
 {
 "minConceptItem": {
 "rxcui": "81948",
"name": "aluminum hydroxide, dried (USP)",
"tty": "PIN"
 },
 "sourceConceptItem": {
 "id": "DB06723",
 "name": "Aluminum hydroxide",
"url": "https://go.drugbank.com/drugs/DB06723#interactions"
 }
 }
 ],
 "severity": "N/A",
 "description": "The serum concentration of Aluminum hydroxide can
be increased when it is combined with Cholecalciferol."
 }
 ]
 }
 ]
 }
 ]
}
[ERP]