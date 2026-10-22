# TP04 - AutoML et MLOps low-code (projet fraude)

Comparaison de trois approches sur la detection de fraude bancaire :
reference logistique, reglage manuel (TP2) et AutoML local avec FLAML.

## Lancer le projet
1. `python -m venv .venv` puis activer l'environnement
2. `pip install -r requirements.txt`
3. `python donnees.py` (genere data/transactions.csv)
4. Lancer MLflow : `mlflow server --host 127.0.0.1 --port 5000 --workers 1 --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./mlartifacts`
5. `python src/references.py`, puis `python src/automl.py 10` (et 30, 60, 120)
6. `python src/rendement.py`, `python src/inspecter.py reports/flaml_60s.log`, `python src/fuite.py`

## Contenu
- `src/` : scripts
- `reports/` : journaux FLAML, graphique de rendement, tableau comparatif

Environnement : Python 3.13, FLAML 2.7.0.