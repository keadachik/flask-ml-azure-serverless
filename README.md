# Flask ML app with CI/CD to Azure App Service

Course project for the Udacity **Cloud DevOps using Microsoft Azure Nanodegree** (2021). A Flask API serves a scikit-learn model (Boston housing price prediction), and Azure Pipelines builds and deploys it to Azure App Service on every push to `main`.

## What is here

| File | Contents |
|---|---|
| [`app.py`](app.py) | Flask app. `GET /` health page, `POST /predict` returns a price prediction from a JSON payload |
| `boston_housing_prediction.joblib` | Trained model |
| [`azure-pipelines.yml`](azure-pipelines.yml) | Build stage (venv, install, package) and deploy stage to an Azure Linux Web App |
| [`Makefile`](Makefile) | `install`, `lint`, `test` targets used in CI |
| [`make_predict.sh`](make_predict.sh), [`make_predict_azure_app.sh`](make_predict_azure_app.sh) | Send a sample prediction request to the local app or to the deployed app |

## Run locally

```bash
make install
python app.py
./make_predict.sh
```

## Notes

- The model and the starter app come from the course materials.
- The Azure resources (App Service, service connection) used here were course lab resources and no longer exist.
- `sklearn.externals.joblib` was removed in newer scikit-learn versions; `import joblib` is needed to run this today.
