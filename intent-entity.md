## Intent and Entity

intent-entity branch

Add intents and entity to model.

1. nlu.yml
   - Add intent with examples
   - Entities are indicated in the intent examples with 
     brackets and parenthesis.

2. domain.yml
   - Add to list of intents
   - Add responses such as utter_
     - If you add multiple response, Rasa randomly chooses one

3. domain.yml
   - Add stories
     - Steps to follow in the story

3. train rasa
   ```
   (venv)$ rasa train
   ```