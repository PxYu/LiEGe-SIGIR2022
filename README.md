

In this repo, we release the processed MIMICS dataset used in our SIGIR ‘22 paper [Towards Explainable Search Results: A Listwise Explanation Generator](https://dl.acm.org/doi/abs/10.1145/3477495.3532067). This is a processed version of MIMICS combining aspect annotation from https://github.com/microsoft/MIMICS and SERP information from http://ciir.cs.umass.edu/downloads/mimics-serp/MIMICS-BingAPI-results.zip.

All files are stored with pickle. To read files, use

```python
import pickle

with open("xxx.pkl", 'rb') as fin:
    data = pickle.load(fin)
```

## Descritption of each file

The main thing to note is that SERP snippets in MIMICS are **query-dependent**, meaning that the document from the same URL contains different content for different queries. Therefore, doc-id is named with `*query*-number`.

- `id2doc.pkl` is a `{k: v}` dictionary, where `k` is document id, and `v` the snippet text.
- `aspect2documents.pkl` is a `{k: a: set}` nested dictionary, where `k` is query, `a` an aspect, and `set` a set of document ids relevant to that aspect.
- `train_queries.pkl` and `test_queries.pkl` are two sets, each containing a around 1K queries. This is the train/test split used in our paper.
- `serps.pkl` is a `{k: list}` dictionary, where `k` is query, and `list` the list of document ids retrieved by Bing for the query. 

--- 

