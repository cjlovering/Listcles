# Listcles

This is a dataset, on the order of 300k items, consists of claims ("milk good for you") and reasons ("milk is rich in calcium").

## Purpose

This dataset can be used for weakly-supervised natural language inference. The labels would be `supports` and `neutral`, however the annotations and generation of the language is derived from an entirely natural setting. This means that it does not contain the same artifacts that plague other such datasets.

## Format

This dataset is currently in a csv with the following columns. Default settings with any csv-reader (e.g. pandas) should allow one to parse it properly.

| Header | Content |
| ------ | ------- |
| query  | The query originally issued to find the web page. |
| claim  | The claim implicit in the title of the page. |
| reason | One of the enumerated reasons supporting the claim. |
| evidence | (Optional). Information that supports the reason. |

## Collection

The root idea is that listicles (websites that present # reasons for X) contain useful structured information. This information is not as *direct* as mechanical turk annotations, but is relatively cheap, generated without the framing of a crowdsourced tasks, and is scalable.

First, we need to find links to such pages. This is done by recursively querying the Bing API: first seed queries are issued ("* reasons * is good"), and then results are used to find more similar and  branching results. Pages are then parsed to find the claim and the reasons. ~60% of the reasons provide evidence; sometimes this evidence is not distinct from the reason itself.

The source for the collection is part of a different repository.

## Contact

This dataset is part of an ongoing project at the Brown NLU Lab. If you have any questions, please contact charles_lovering@brown.edu.
