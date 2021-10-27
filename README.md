# Time-Series-Forecast-Farm-Climate


### 3 DIFFERENT PYTHON CODE FILES (NOTEBOOKS) HAVE BEEN PROVIDED. PLEASE READ ABOUT EACH ONE OF THEM.

* Appropriate Model And Parameter Research
* Trainer
* Predictor

---
#### PREDICTOR
---
The _Predictor_ File is a pipeline for sending in new data points on which predictions will be returned according to our needs.

**It is necessary to run this file from the directory where the _Trainer_ file is placed**

This is because the _Trainer_ file saves the model weights and supplementary data which are then used by the _Predictor_ file.

The _Predictor_ file includes many options for providing your input:

* **no.ofDays** :    you input a number and the model would output predictions for those many dates from the current date.
                Given that the data stretches until Dec 2019 only, using this option would output predictions starting from **(Jan 2020) to (Present Date + given no.ofDays)**


* **no.ofSteps**:    Another number input. The model would output predictions for those many steps into the future from the latest date available in the data.
Eg : If no.ofSteps = 120, The model would output predictions from **Jan 1st 2020 00:00** to **Jan 5th 2020 00:00**. Each step corresponds to 1 hour.

* **datestring** :   Enter a date in the string format, the predictions would correspond to that date.

* **Jsonfile** :     Enter the path of a folder that contains input in the form of JSON files. It is necessary that each JSON file contains an element named 'datetime'.
Present work allows only one row of input data per json file. This can be scaled up later.

* **Jsonstring** : Enter a JSONstring input.


Options for Output formats:

* **Precise**: outputs predictions precisely for that timestamp

* **Until** : outputs predictions starting from most recent data until the provided timestamp

* **json** : outputs the predictions in json format

* **df** : outputs the predictions in df object

---
#### TRAINER
---

* The _Trainer_ file is a refactoring of the important steps involved in training the model from the _Appropriate Model and Parameter Research_ file.

* The training steps have been automated. They can be run at scheduled intervals when new data is available.

* This involves pre-processing and feature engineering steps and the model fitting steps.

* **This file also saves the supplementary datasets that are prepared into the current working directory** 

* These supplementary datasets and the saved model are called upon from the _Predictor_ file.


* **NOTE** : The trained model removes non-stationary components (trend and seasonality) from the data before making predictions. 
The supplementary datasets are used to re-introduce these components


---
#### APPROPRIATE MODEL AND PARAMETER RESEARCH
---

The _Appropriate Model and Parameter Research_ file was sued to figure out the best model as well as the best parameters. It is more of an exploratory undertaking.
The findings were used to write the crisper and cleaner _Trainer_ and _Predictor_ files.
