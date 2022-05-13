# Rasa Chatbot Hackathon
Here are the files for creating the chatbot model.  

## Installation Instructions
[Rasa open source installation instructions](https://rasa.com/docs/rasa/installation/)

```
$ python3 -m venv ./venv
$ source ./venv/bin/activate
(venv)$ pip3 install -U pip

(venv)$ pip3 install rasa

(venv)$ rasa init
```

## Starting Rasa server
```
$ source ./venv/bin/activate
$ rasa run --enable-api --model ./models --endpoints ./endpoints.yml --cors "*"
```
