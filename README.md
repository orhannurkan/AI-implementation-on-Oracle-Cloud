# Instruction on implementing Python AI projects from github on Oracle Cloud

On Oracle Cloud, the projects on Github are incredibly difficult to implement and sometimes take months to overcome. For this reason, I wanted to share this instruction, which I previously prepared for some of my Senior Software Developer colleagues, as I think it may be useful for those who want to implement AI projects on Oracle Cloud. This specification is designed to be a general specification after testing the implementation of almost all kinds of AI projects from github.

Note : Initially, I prepared this instruction for Senior Java Developers who do not know Python. Since these project files, details and all rights belong to a company I worked with before, the files were not shared. This instruction was applied with Tensorflow, Pytorch and even many different technologies and successful results were obtained. Actually, I wrote many more explanations and Wiki pages, but I haven't shared them on github yet. I will continue to share the appropriate ones over time. 

# Application of object detection models to Satellite images on Oracle Cloud

## Implementation steps :

1. Find the Python project you are satisfied with (for example the SpaceBel project has been implemented in this repo)
    - It is recommended to search on github and examine the projects with the most stars among the results.
    - If an online demo is available or the outputs are visualized on the repo, that project is worth a try.



2. Open a Jupyter notebook file in Oracle Cloud 
    - First, enter AI & DataScience from the menu in Oracle cloud and create a new project.
    - Create a new notebook session in this project
    - Open this session and open a new notebook in the desired enviroenment section
    - Different environments can be created or selected at any time 



3. Go to first cell in notebook copy project to oracle cloud with clone
    - eg (! git clone https://github.com/ultralytics/yolov5)
    - If the project is a zipped file on your local computer, upload it to the file browser of Oracle Cloud on the left menu in jupyter notebook session and unzip it (by runing a python code)



4. Find required data set to train ML model
    - The data required for training the pool prediction model I used this dataset : https://www.kaggle.com/kbhartiya83/swimming-pool-and-car-detection



5. Examine, clean, preprocess and prepare the data set to train the model. (Data Science)
    - As a result of this data set, I spent about 100 hours to get satisfactory results.
    - What I do is to check and edit files by opening them (7.500 xml and jpg files)
        - Setting the minimum area outside the pool
        - Deleting non-pool selections
        - Deleting the pool images that are too small from XML        



6. Read and follow project details and create required enviroenments
    - You can review and use the ready environments in the Oracle Cloud
    - or you can create your own conda / python environments



7. Library list is usually in requirements.txt file in the project folder, install Libraries with correct version.
    - If requirements.txt does not exist, when you get an error while executing the file, find the required library and install it.
    - Conda is recommended and if the library is not available in conda then install the library with pip.



8. Apply the steps in the project one by one and find solutions if errors occur (python knowledge)



9. If the predicted results are not satisfactory after evaluating the model, fine tuning is required (ML developer)



10. In AI project, ML model is produced, finally get this model, understand what inputs and outputs are and what should be done (python developer)



11. If you are not satisfied with the results after running the tests, it may be necessary to preprocess the training data set. 
    - If you are pre-processing the training dataset, you must also pre-process inputs for prediction(e.g. applying grayscale)
    - If this is not enough, work on data cleaning and preparation parts and improve the model (Data science knowledgebase).



12. Check model config file if error occurs while doing training
    - If the process killed it means memory is not enough, solution: set the batch size to 8 or 16 in the model config file 
    - If you are training with image files and system resources are insufficient, it may be a solution to reduce the resolution from the model config file.



13. Apply the procedure for adding to the Oracle Model Catalog : https://docs.oracle.com/en-us/iaas/tools/ads-sdk/latest/user_guide/modelcatalog/modelcatalog.html?highlight=model%20catalog
    - Oracle Cloud accepts onnx file format for the model, if you could not find solution in the procedure file, you may need to convert the model to onnx format
    - Examine the functions in the model structure, then make the necessary changes in these function files. 



14. Follow the Oracle model deployment procedure : https://docs.oracle.com/en-us/iaas/tools/ads-sdk/latest/user_guide/fn_deploy/model_deployment_function.html?highlight=model%20deployment
    - Finally you will be given python access and OCI access for the API
    - Send test data to the API (test data format is generally json object and it is in this format: {"col1": [values], ...}
    - The json format in the artifact shows with which key and value pairs the model is used to train. You will use the same format while send data to the API. 
    - Look at the column and value type information from there : schema.json (it is in the model artifact) you can download model artifact from the model catalog,



15. If the project is deployed successfully and the responses given to the requests are correct and there is no estimation problem
    - You can edit the relevant model in the model catalog and enter the project's github information.
    - In this way, when any changes are required, versions of the source code can be accessed and necessary arrangements can be made.
