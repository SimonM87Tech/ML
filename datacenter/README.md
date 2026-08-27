# Data Center

One shared dataset store for all missions.

**Why shared, not per-mission:** datasets get reused (the churn data will come back in the MLOps mission; pet images can serve future vision experiments), large files should never be duplicated, and one `.gitignore` here keeps every dataset out of git. Missions reference datasets by relative path, e.g. `../../datacenter/telco-churn/`.

## Conventions

- One subfolder per dataset, kebab-case: `datacenter/<dataset-name>/`
- Raw downloads go in `<dataset-name>/raw/` — **never modify raw files**. Cleaned/processed versions go in `<dataset-name>/processed/`.
- Every dataset gets a row in the registry below when added: where it came from, size, license, which mission uses it.
- Data files are gitignored; this README and any small metadata files are tracked.

## Registry

| Dataset | Source | Size | Used by | Status |
|---------|--------|------|---------|--------|
| `telco-churn` | [IBM sample data (GitHub raw CSV)](https://raw.githubusercontent.com/IBM/telco-customer-churn-on-icp4d/master/data/Telco-Customer-Churn.csv) | ~1 MB, 7,043 rows | Mission 01 | downloaded → `telco-churn/raw/telco-churn.csv` |
| `oxford-pets` | [Oxford-IIIT Pet](https://www.robots.ox.ac.uk/~vgg/data/pets/) (`thor.robots.ox.ac.uk/pets/*.tar.gz`) | ~800 MB, 7,349 images, 37 breeds | Mission 02 | downloaded + extracted → `oxford-pets/oxford-iiit-pet/{images,annotations}`; `OxfordIIITPet(root="datacenter/oxford-pets", download=True)` detects it and skips re-download |
