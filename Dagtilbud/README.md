**Dagtilbud**

This sensors will retrieve data about dagtilbud from Aarhus Kommune.

**Configuration:**

1: Go to this url https://admin.opendata.dk/api/3/action/datastore_search?q=BYNAVN&resource_id=c29f6d4b-7d0c-48af-bb23-93f54c0b49bc# and make sure you replace BYNAVN with the name of the city you are interested in finding a dagtilbud in.

This could look like this https://admin.opendata.dk/api/3/action/datastore_search?q=aarhus&resource_id=c29f6d4b-7d0c-48af-bb23-93f54c0b49bc#

2: Now find the name of the dagtilbud and insert it in the url like this NAME_CITY https://admin.opendata.dk/api/3/action/datastore_search?q=NAME_CITY&resource_id=c29f6d4b-7d0c-48af-bb23-93f54c0b49bc# and could look like this for Solen in Aarhus https://admin.opendata.dk/api/3/action/datastore_search?q=solen_aarhus&resource_id=c29f6d4b-7d0c-48af-bb23-93f54c0b49bc#

3: Visit the url in your browser and make sure under records only 1 entry is listed, if more are listed make sure the value in value_template points to the correct one.

Example for the antal sensor:

value_template: '{{ value_json.result.records[0].Antal }}' is pointing to the first entry under records.

value_template: '{{ value_json.result.records[1].Antal }}' is pointing to the second entry under records.

value_template: '{{ value_json.result.records[2].Antal }}' is pointing to the third entry under records.

**Data:**

The following data points are available:
```
_id
instid
Periode
Insttype
Dagtilbud
Instnavn
Antal
Adresse
Postnr
Postdist
lat
lng
Ledernavn
LINK
rank
```

Origin data source: https://www.opendata.dk/city-of-aarhus/born-i-dagtilbud

For data sources from other kommuner visit https://www.opendata.dk and search for available datasets for your kommune.

**Note:**

This is my first try with use of rest api, so this sensors can be make more smooth and with better quality!
