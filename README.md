
This small project demonstrates:

Training a tiny text classifier.
Saving the model artifact.
Serving predictions via a Flask API (/predict).
Quick start (local)

Create a virtualenv and install: 
$ python3 -m venv .venv source .venv/bin/activate pip install -r requirements.txt

Train the model: python model/train.py This will create model/artifacts/intent_model.pkl.

Run the API: 
$ gunicorn --worers 3 --bind 127.0.0.1:6000 wsgi:app - it brings the parallelism then server can run parallel tasks

Example request: 
$ curl -X POST http://127.0.0.1:6000/predict -H "Content-Type: application/json" -d '{"text":"I want to cancel my subscription"}'

Response: { "intent": "complaint", "probabilities": {"complaint": 0.85, "question": 0.05, ...} }

======

It runs as a foreground process either we need to run it as a background process or run with a systemd process