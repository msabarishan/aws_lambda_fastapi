Below are the best approach to deploy Fastapi in AWS_Lambda (Serverless deployment)

For Windows:

1. Open a New Folder Using VSCode
2. Create a new Python Environment. Open a new Terminal and type "python -m venv .venv" where .venv is the path and folder name. Usually Vscode ask for interpreter to venv, click yes and ensure that 
in terminal venv is shown in command line, if not try opening a new terminal, or activate the terminal.
3. create a new python file named 'main.py'
4. Below is the Basic code for Fastapi with handler mangum
(This is required for deploying in AWS Lambda)
"
from fastapi import FastAPI
from mangum import Mangum
app = FastAPI()
handler=Mangum(app)
@app.get("/")
async def hello():
    return {"message": "Hi"}
"
5. Install the Packages such as fastapi==0.99.0 and mangum  (Note: pin fastapi==0.99.0)
6. Create a requirements.txt using cmd pip freeze > requirements.txt
7. Create a folder named bin with the dependencies using cmd pip install -t bin -r reqiurements.txt
8. Copy and paste main.py file inside bin folder.
9. Select the files and folders inside bin folder and create a zip file.
10.Open AWS Lambda. Click on create Function.Enter a name. Select Runtime as Python 3.11. Click on advanced settings. Check Enable function URL box. Select Auth type as None. Finally click on create function.
11.Click on Upload Form. Select the zip file and Upload.
12.In Runtime Settings click on Edit. In handler, type "main.handler" where main is the python file and handler denotes to the mangum.
13.Now click the Function URL to obtain Fastapi response.

                                                            

                                                            
