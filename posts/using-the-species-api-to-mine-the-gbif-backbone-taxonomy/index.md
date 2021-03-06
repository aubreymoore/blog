<!--
.. title: Using the Species API to Mine the GBIF Backbone Taxonomy
.. slug: using-the-species-api-to-mine-the-gbif-backbone-taxonomy
.. date: 2017-04-22 10:34
.. tags: GBIF, JSON, taxonomy, biodiversity
.. category:
.. link:
.. description:
.. type: text
-->

## Here's how to get tons of info from GBIF.

Check out the [Species API](http://www.gbif.org/developer/species).

First step is to locate the taxon in the GBIF Backbone Taxonomy. The GBIF Backbone Taxonomy, often called the Nub taxonomy, is a single synthetic management classification with the goal of covering all names GBIF is dealing with.

You can search GBIF manually by going to <http://www.gbif.org/species> and entering a scientific name or common name. The magic number you are looking for is the **GBIF ID**.

Alternatively, you can use the Species API: <http://api.gbif.org/v1/species/search?q=lawn%20armyworm&rank=SPECIES>. This will return info encoded as JSON. The magic number in this case is **nubKey**.

Once we have the GBIF ID, which is 5109848 for *Spodoptera mauritia*, we can harvest more data:

| | |
|-|-|
|Name usage:|<http://api.gbif.org/v1/species/5109848>|
|Synonyms:|<http://api.gbif.org/v1/species/5109848/synonyms>|
|Vernacular names:|<http://api.gbif.org/v1/species/5109848/vernacularNames>|
|Media:|<http://api.gbif.org/v1/species/5109848/media>|
|References:|<http://api.gbif/v1/species/5109848/references>|
|Distributions:|<http://api.gbif.org/v1/species/5109848/distributions>|
|Descriptions:|<http://api.gbif.org/v1/species/5109848/descriptions>|
