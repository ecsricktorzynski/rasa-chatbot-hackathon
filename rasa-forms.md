## Rasa Forms

rasa-forms branch

Add a custom action to give the current time

1. nlu.yml
   - add intent with examples
   
2. stories.yml  
   - add story with the steps

3. actions.py
   - add custom function
     - class added is called ActionHelloWorld but 
	   the reference is to "action_show_time"
	   
4. domain.yml  
   - add give_time intent
   - add actions action_show_time
   
5. endpoints.yml  
   - uncomment the action_endpoint lines
   
6. Save these files

7. In terminal retrain the model since intents, stories and actions have changed
   $ rasa train

8. In terminal start up Rasa Actions Server
   $ rasa run actions
 
9. In separate terminal start up Rasa shell
   $ rasa shell
