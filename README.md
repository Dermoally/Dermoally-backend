# Flask API Documentation 🤖

## API URL 🔗
[Your Machine Learning API](https://dermoally-vvergznbcq-et.a.run.app/)

## API Endpoint 🚪
If you want to access our endpoints, you first need to access the register and login endpoints to get the JWT Token for credentials to access our Machine Learning API endpoints. You can access register and login endpoints from [Register API](https://dermoally-vvergznbcq-et.a.run.app/register) and [Login API](https://dermoally-vvergznbcq-et.a.run.app/login). For details, please check the tables below to see the API documentation and which endpoints need the JWT Token (shown in the checklist):

|             Endpoint            | Method |              Input              |                                          Description                                          |  JWT Token  |
| :-----------------------------: | :----: | :-----------------------------: | :--------------------------------------------------------------------------------------------: | :---------: |
|              /                  |  GET   |                -                |                                         Access root endpoint                                   |   &#9744;   |
|          /predict               |  POST  |              file               |Predict the user's face image using our Machine Learning models and return the analysis result. |   &#9745;   |
|          /history               |  GET   |                -                |                                 Show the history of analyzed results                          |   &#9745;   |
|   /predict/recent               |  GET   |                -                |                                 Show recent prediction results                                |   &#9745;   |
| /disease/<int:id>/medications   |  GET   |                -                |                            Show medications for a specific disease                             |   &#9744;   |
|          /favorites             |  GET   |                -                |                                 Show user's favorite predictions                              |   &#9745;   |
|          /user                  |  GET   |                -                |                                       Get user information                                     |   &#9745;   |
|       /get_id_disease           |  GET   |        disease_name             |                                Get disease ID by disease name                                  |   &#9744;   |
|      /disease/info/<int:id>     |  GET   |                -                |                                  Get information about a disease                               |   &#9745;   |
|      /favorites/<int:id>        |  PUT   |          favorite               |                                 Update favorite status for a prediction                        |   &#9745;   |
|          /profile               |  PUT   |    email, name, profile_image_url |                                      Update user profile                                      |   &#9745;   |
|      /process/<int:id>          |  GET   |                -                |                         Show process information for a specific analysis                       |   &#9745;   |

## How to run this API on your local machine 💻
If you want to run this API Server on your local machine, you need to follow these steps:
- First, clone this repository. `git clone https://github.com/yourusername/yourproject.git`
- Second, open terminal and go to this project's root directory.
- Third, type `pip install --no-cache-dir -r requirements.txt` in your terminal to install dependencies and hit enter.
- Fourth, type `python deploy.py` in your terminal and hit enter.
- Finally, the server will run on http://localhost:9000

## How to deploy this API to Cloud Run 🚀
If you want to deploy this API server to Cloud Run, you need to follow these steps:
- First, open your Google Cloud Console. https://console.cloud.google.com/
- Second, open the Cloud Shell at the top right corner in the Google Cloud Console. Make sure you enable Cloud Run API and Cloud Build API before.
- Third, copy the command below to clone this repository into the Cloud Shell.
 ```
 git clone https://github.com/yourusername/yourproject.git
 ```
- Fourth, go to this project's root directory in the Cloud Shell.
- Fifth, copy the command below to build the image container and upload it to the Container Registry.
 ```
gcloud builds submit \
  --tag gcr.io/$GOOGLE_CLOUD_PROJECT/your-ml-api
  ```
- Sixth, copy the command below to deploy your image container to Cloud Run.
 ```
 gcloud run deploy your-ml-api \
  --image gcr.io/$GOOGLE_CLOUD_PROJECT/your-ml-api \
  --platform managed \
  --region your-region \
  --allow-unauthenticated \
  --max-instances=3 \
  --port=9000 \
  --memory=8Gi
 ```
- Finally, your API server will be deployed to Cloud Run, and you will get the URL in the Cloud Shell to access your server.
