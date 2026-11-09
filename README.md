# Afnan Mazumder

Final-year computer science student at BRAC University in Dhaka, working on NLP and full-stack software. I'm looking for software and machine learning engineering roles.

## Clausify

Contracts are long, and the clauses that can hurt the signer are easy to miss. [Clausify](https://github.com/afnanmz168/clausify-p3-app) is the app my team of three built for our final-year project. Give it a PDF, a Word file or pasted text, and it lists the clauses it finds by risk, quoting each one with a plain-English note.

We trained it on CUAD (510 expert-annotated contracts, 41 clause types) and kept 102 contracts out for the final test.

| Step | Model | Result on the 102 test contracts |
|---|---|---|
| Which clause types are present? | DistilBERT with a threshold per clause type | Finds 90.3% of high-risk clauses |
| Where is the clause? | DistilBERT-QA | Token F1 of 0.779 on a window holding the clause |
| What does it mean? | FLAN-T5-small | Picks one of 41 template sentences |

Some decisions I'm happy to talk through:

- We ship the setting with the lower F1. The balanced setting reaches micro-F1 0.809 but finds only 54.0% of high-risk clauses. The default scores 0.757 and finds 90.3%, because a missed high-risk clause costs the signer more than a false alarm does.
- Our first span model gave a good quote for only 22.1% of real clauses end to end. Retraining it on the 1,200-character chunks the app feeds it, and tuning how the quote is chosen, raised that to 59.6%.
- The app caps how much of a long contract it reads. Checking only the first 30 windows found 77.3% of high-risk clauses. Letting TF-IDF pick five more windows per clause type raised that to 88.6%, against 90.3% for reading every window.
- The train and test sets are split by contract, so no contract appears in both. A script, `verify_report.py`, checks every number in the report, and 46 automated checks cover the app.

[App code](https://github.com/afnanmz168/clausify-p3-app) | [Research code and report](https://github.com/afnanmz168/clausify-p3) | [Paper](https://github.com/afnanmz168/clausify-p3/blob/main/IEEE_Paper_Clausify.pdf) | [Trained models](https://huggingface.co/af123Af/clausify-models)

## Voyenta

[Voyenta](https://github.com/afnanmazumder-maker/CSE470-project_travelPlaner) is a trip planner from a group project in my software engineering course. A React front end calls a Laravel REST API backed by PostgreSQL. A separate FastAPI service generates recommendations and itineraries, and it never touches the database: Laravel passes data in and stores what comes back.

## What I use

Python, JavaScript and PHP. PyTorch, Hugging Face Transformers, scikit-learn and Streamlit for machine learning. React, Laravel, FastAPI and PostgreSQL for web apps.
