# Rasa Chatbot Hackathon
Here are the files for creating the chatbot model.  

## Installation Instructions
[Rasa open source installation instructions](https://rasa.com/docs/rasa/installation/)

'''
# activate environment
$ python3 -m venv ./venv
$ pip3 install -U pip
# install Rasa open source
$ pip3 install rasa
# create new project
$ rasa init
'''

## Starting Rasa server
'''
$ source ./venv/bin/activate
$ rasa run --enable-api --model ./models --endpoints ./endpoints.yml --cors "*"
'''
