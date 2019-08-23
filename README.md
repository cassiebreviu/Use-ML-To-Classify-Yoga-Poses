# How to Get a Dataset and Create a ML Model to Classify Yoga Poses (Using Azure Cognitive Services)
This tutorial will go over how to use Azure Cognitive Services to get an image dataset and train a Custom Vision model. The repository has a simple nodejs console app that uses Bing Image Search to scrape images to a local directory based on search term(s). Then use the images scraped to create a Custom Vision model with Azure Cognitive Services.


### Create an Azure Account
[Click here to create your account](https://azure.microsoft.com/free/?WT.mc_id=blog-github-casiljan)

### Create Bing Search Api Resource
* Go to [portal.azure.com](https://portal.azure.com/)
* Select "Create Resource"
* Select "AI + Machine Learning"
* Select "Bing Search v7"
* Complete the required fields
* Select "Create"
* When the deployment succeeds you will get a notification in the top right corner.
* Select "Go to resource"
* Select "Keys" from the left hand navigation for the resource.
* Copy the Subscription Key and paste it into the script.

### How to Run the Image Scraper Script
# Image Scraper using Bing Search Cognitive Service
Clone the repo <br>
`https://github.com/cassieview/Use-ML-To-Classify-Yoga-Poses.git`
<br>
`cd Use-ML-To-Classify-Yoga-Poses`

Install packages <br>
`npm install`

Open in VS Code <br>
`code .`

Add the key into the app.js script <br>
`const subscriptionKey = 'addyourkeyhere'`

Update the host to the endpoint you created <br>
`const host = 'resourcename.cognitiveservices.azure.com';`

Run the script <br>
`node app.js`

### Create Custom Vision Api Resource
* Go to [portal.azure.com](https://portal.azure.com/)
* Select "Create Resource"
* Search "Custom Vision"
* Select "Create"
* Complete the required fields
* Select "Create"
* When the deployment succeeds you will get a notification in the top right corner.
* Select "Go to resource"

### Create Project and Train Model
* Select "Quick Start"
* Select "Custom Vision Portal" or go to https://www.customvision.ai/projects and login
* Select 'Sign in"
* Select "New Project"
  - Enter a Name and Resource Group and 
  - Project Types: Classification
  - Classification Types: MultiClass General
  - Domains: General
* Create project
* Add and tag images
  - Select "Add Images" and navigate to the train folder for the scraped images
  - Ctrl + A to select all the images in the folder
  - Select "Open"
  - Add tag for photos to indicate the yoga pose
  - Select "Upload photos"
  - Repeat these steps for each yoga pose (class)
* Select "Train"
* Test your model
   - Select "Quick Test" from the upper right corner
   - Browse to local files and select a image from the test folder
   - The predication will appear on the right side of the window
   
### Get the Prediction Url
* Select "Performace" from the top navigation in the Custom Vision portal
* Select "Prediction Url"
* Copy the Url to either use an image url or image file
* Additionally by selecting the settings icon in the right corner will bring you to the keys and urls to call the endpoint.

### Consume the API in an App

Once the model is trained and at a satisfactory accuracy its ready to be used in your App
* Go to the Resource Group that contains the Custom Vision Resource
* There should be a resource named "YourCustomVisionResourceName_Prediction - Quick start"
* The Select "Api Reference" from the list of helpful links
* This will open a page with docs on how to call the api to get predictions from the model
* If you scroll all the way to the bottom there are code samples in multiple languages to get you started

### Test API in Postman
* Get the predction url as described above
* Select "Post" from the dropdown and paste in the url
* Go to the settings and get the Prediction Key
* In the headers add the `Prediction-key` as the key and the actual key as the value
* Auth should be set to no auth
* Select Body > Raw > Json
* Paste in the following Json
``{
  "Url": "UrlForImageGoesHere"
}``
* Send Request


## Helpful Doc Links

[Quickstart: Search for images with the Bing Image Search SDK for Node.js](https://docs.microsoft.com/en-us/azure/cognitive-services/bing-image-search/image-search-sdk-node-quickstart?WT.mc_id=techtogether-talk-casiljan)

[Quickstart: Create an image classification project with the Custom Vision Node.js SDK](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/node-tutorial?WT.mc_id=techtogether-talk-casiljan)

[Cognitive Service Bing Search Docs](https://docs.microsoft.com/en-us/azure/cognitive-services/bing-web-search?WT.mc_id=techtogether-talk-casiljan)

[Cognitive Service Custom Vision Docs](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/home?WT.mc_id=techtogether-talk-casiljan)

[Create a Node.js app in Azure App Service on Linux](https://docs.microsoft.com/en-us/azure/app-service/containers/quickstart-nodejs?WT.mc_id=techtogether-talk-casiljan)
