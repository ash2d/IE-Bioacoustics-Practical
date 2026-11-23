# Bird species classification practical

Classify 5-second audio recordings into one of three bird species, or "Nothing heard" if no bird is calling.

## Setup

SSH into Jasmin
This folder is read-only, apart from `groups/` and `test_results/`. Work in your own group folder:

```bash
cd /gws/ssde/j25b/iecdt/bio_practicals/bioacoustic
mkdir groups/<group_name>
cp 01_supervised.ipynb 02_autoencoder.ipynb groups/<group_name>/
```

Then open the notebooks from your group folder and select the existing `.venv` in this folder as the kernel (`/gws/ssde/j25b/iecdt/bio_practicals/bioacoustic/.venv/bin/python`). It already has the packages in `pyproject.toml`.

The notebooks use absolute paths, so your copies read the shared `data/` and `cache/` and write to the shared `test_results/` without any changes.

Put your test predictions in `test_results/` (the last cell of each notebook does this) — I will grade them. You can only delete or rename your own files in `groups/` and `test_results/`, not other groups'.

## Data

```
data/
  unlabelled/   4800 clips, no labels
  labelled/     200 clips + labels.csv (columns: filename, species)
  test/         200 clips, no labels — these are what you are marked on
```


## Two approaches provided

- `01_supervised.ipynb`: train a small CNN directly on the 200 labelled clips.
- `02_autoencoder.ipynb`: train a CNN autoencoder on the 4800 unlabelled clips, then fit a small MLP probe on its embeddings using the 200 labelled clips.

## Submitting the predictions

Both notebooks end by predicting the test set and writing `test_results/<group>_<model>.csv`. Set `GROUP_NAME` in the last cell first. Submissions should follow the csv format of the notebook - see the `tested_<model>.csv`

By 4pm on Tuesday I will grade all of the submissions in `test_results/`; the winning group gets a chocolate bar - I reserve the right to disqualify submissions if i suspect any funny business.