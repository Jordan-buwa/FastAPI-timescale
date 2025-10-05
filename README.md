# Building an analytic API using FastAPI + Time-series Postgres

## Download and Install python [(link)](https://www.python.org/)

## Create a virtual environment 

- `python3 -m venv venv`
- `source venv/bin/activate`

## List all the requirements in a text file: requirements.txt

```txt
fastapi[standard]
uvicorn
gunicorn
pydantic
timescaledb
sqlmodel
sqlalchemy
```

## Run install all the requirements

```bash 
pip install -r requirements.txt
```

## Write the app file (main.py) and some routes

```python
from typing import Union

from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}


@app.get("/items/{item_id}")
def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}
```

## Run the app 
```bash
fastapi dev main.py
uvicorn main:app --reload
```

## Create a docker file and build the docker image to produce a light-weight app
```bash
docker build -t my_container
docker run my_container
```
