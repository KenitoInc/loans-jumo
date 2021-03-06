# loans-jumo
## Overview
Every two months we are given a text file from our accounting department detailing all the loans
given out on our networks. This needs to be a validated against our internal systems by the tuple
of (Network, Product, Month). This projects aggregates the loan data by the tuple of (Network, Product, Month) with
sum amounts and counts and outputs into a csv file.

## Installation
`git clone https://github.com/KenitoInc/loans-jumo.git`

Create a virtualenv in the project directory
````
cd loans-jumo

virtualenv venv

source venv/bin/activate
````

#### Installing dependencies
`pip install -r requirements.txt`

#### Configure celery
Edit celery configuration in app/celery.py

#### Start celery
On one terminal  
`celery -A app worker --loglevel=info`

#### Start application
On another terminal  
`python run.py`

## Assumptions
1. RabbitMQ had been configured on the server  
2. CSV has no missing values  
3. CSV is automatically pushed to the data folder  
4. Aggregated outputs are needed on demand  
5. This is just a microservice which is part of a larger system

## Stack
Built on python - multi-paradigm language which supports functional, procedural and object oriented programming styles.  

Key Libraries of this stack include -:  
1. Celery is an asynchronous task queue. Ideal for background computation of expensive queries. This will make it easier to scale our computation capacity e.g. aggregate summaries for the last 10 years will probably be from a csv with several millions rows.  
2. RabbitMQ is a message broker used with Celery.  
3. Logging – Allows logging program’s execution to a file  
4. CSV - library that implements classes to read and write tabular data in CSV format


