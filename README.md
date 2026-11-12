# Bird species classification practical

Classify 5-second audio recordings into one of three bird species.

## Data

```
data/
  unlabelled/   4800 clips, no labels
  labelled/     100 clips + labels.csv (columns: filename, species)
  test/         100 clips, no labels — these are what you are marked on
```

## Two approaches

- `01_supervised.ipynb`: train a small CNN directly on the 100 labelled clips.
- `02_autoencoder.ipynb`: train a CNN autoencoder on the 4800 unlabelled clips, then fit a linear probe on its embeddings using the 100 labelled clips.

Both notebooks end by predicting the test set and writing `test_results/<group>_<model>.csv`. Set `GROUP_NAME` in the last cell first.

## Setup

Hopefully you can all access this gws space
There is already a .venv in this folder with the packages in the pyproject.toml
Each group should make their own folder here to put their code in
Put your test predictions in /test_results/ - I will grade them