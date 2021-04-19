# SemValidator

Given a seed ontology and a list of concepts to be added to it, OntoValidator provides an easy-to-use interface for semantic validation of the enriched ontology. Validation is crowdsourced, with Twitter expertise of the validator being used for quality control.

The application has been deployed [here](http://semvalidator.herokuapp.com/).

## Running the Application (Validator)

- Go to the [Heroku web-app](http://semvalidator.herokuapp.com/)
- Sign in with your Twitter account.
- Select one of the ontologies given in the dashboard
- For each of the enriched concepts and relations (highlighted green), select `accept` or `reject` options.


## Running the Application (Developer)

### Directory Structure

- `onto_app`: Contains all relevant scripts used by the Flask application. Also contains `get_verified_ontology.py` which is to be used separately after crowdsourcing is complete. It outputs final ontology based on weighted majority voting algorithm of Twitter expertise scores of validators.
- `WebVOWL`: Code for working of WebVOWL application. For more information on how to modify this check out the [corresponding README](WebVOWL/README.md)
- `experiments`: Contains README files with experimentation details. (Supplementary material to main paper)

### Requirements:
- python3 and pip are used to build this application and are therefore prerequisites

### Installation:
- Go to [src](src/) folder
- Run `pip3 install -r requirements.txt`. In case of any missing modules, please raise an issue.

### Initialization:
- Place the seed ontology (.owl file) in [src/onto_app/data/input](src/onto_app/data/input)
- Place the file containing new concepts and relations in [src/onto_app/data/input](src/onto_app/data/input) as .txt file
- Both the .owl file and .txt file should have same names. For instance, if your seed ontology is `pizza.owl`, name your text file as `pizza.txt`


### Validating the Ontology (Sample)
This section shows how a developer can validate an ontology, for experimentation purposes. A real survey would obviously take place on a deployed app.
- Navigate to the [onto_app](src/onto_app) directory. 
- Run `export FLASK_APP=routes.py` and `export FLASK_ENV=development`
- Run `flask run` to start the server
- Login to the application using your Twitter account 
- Accept/reject concepts and relationships, as appropriate.
- Logout and stop the server.
- Multiple users validate the ontology this way through crowdsourcing

### Saving the decisions in final ontology
- Remove the files in [final](src/onto_app/data/final) if any.
- Pretrained regression models have been provided in the [models](src/models) folder. The path to the model can be changed in `get_verified_ontology.py`
- Run `python3 get_verified_ontology.py <file_name>`
- The decisions made by all the ontologists get evaluated based on their Twitter credibilities. 
- The decision with a higher score is chosen as the final decision, and written to the final ontology.
- Final ontology is stored in [src/data/final](src/onto_app/data/final) as `<file_name>.owl`
