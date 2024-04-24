## 19th Plase solution for PII Detect challenge by The Learning Agency Lab 
### Summary
* Model used: [microsoft/deberta-v3-large](https://huggingface.co/microsoft/deberta-v3-large) (6 layers frozen, 5 fold ensemble)
* Performance: F5 = 0.965
* Classes: `['I-URL_PERSONAL', 'I-ID_NUM', 'B-STREET_ADDRESS', 'B-PHONE_NUM', 'B-USERNAME', 'I-PHONE_NUM', 'I-STREET_ADDRESS', 'B-EMAIL', 'B-ID_NUM', 'B-URL_PERSONAL', 'I-NAME_STUDENT', 'B-NAME_STUDENT',  'O']`
* Training time: ~ 15hrs on a single NVidia 4090
* Datasets used:
  - Competition Dataset: https://www.kaggle.com/competitions/pii-detection-removal-from-educational-data
  - Custom Datasets:
    - [PII Detection Dataset (GPT)](https://www.kaggle.com/datasets/pjmathematician/pii-detection-dataset-gpt): 
    - [PII | External Dataset](https://www.kaggle.com/datasets/alejopaullier/pii-external-dataset)
    - [pii-dd-mistral-generated](https://www.kaggle.com/datasets/nbroad/pii-dd-mistral-generated)  
    - [PII - Mixtral8x7B generated essays](https://www.kaggle.com/datasets/mpware/pii-mixtral8x7b-generated-essays)
    - [Mixtral Original Prompt](https://www.kaggle.com/datasets/tonyarobertson/mixtral-original-prompt)

![image](https://github.com/mjdileep/PII-Detect/assets/6938724/7869a88f-12f2-4dd8-a036-ac03190b2a8c)

### Technical Higlights
* Used stratified k-fold
* Used a custom loss function and a trainer with to drop `30% of 'O'` label in loss calculation and allocate `0.01` as the weight for `'O'` class
  ![image](https://github.com/mjdileep/PII-Detect/assets/6938724/2d7acb1a-9cab-4433-8de4-7a8700f00ed8)
  ![image](https://github.com/mjdileep/PII-Detect/assets/6938724/17ad6413-528d-4cc0-a2a3-37fe6f90e76b)

