# Image Scraper using Bing Search Cognitive Service
Simple nodejs console app that uses Bing Image Search to scrape images to a local directory based on search term(s). This example is using yoga pose names to train a custom vision machine learning model to recognize yoga poses.

## Helpful Doc Links

[Quickstart: Search for images with the Bing Image Search SDK for Node.js](https://docs.microsoft.com/en-us/azure/cognitive-services/bing-image-search/image-search-sdk-node-quickstart?WT.mc_id=techtogether-talk-casiljan)

[Quickstart: Create an image classification project with the Custom Vision Node.js SDK](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/node-tutorial?WT.mc_id=techtogether-talk-casiljan)

[Cognitive Service Bing Search Docs](https://docs.microsoft.com/en-us/azure/cognitive-services/bing-web-search?WT.mc_id=techtogether-talk-casiljan)

[Cognitive Service Custom Vision Docs](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/home?WT.mc_id=techtogether-talk-casiljan)

## How to create a service that can classify yoga poses using Azure Cognitive Services

### Create an Azure Account
Students get a free 100 dollar credit and dont need a credit card to sign up!

[Click here to create your account](https://azure.microsoft.com/en-us/free/students?WT.mc_id=techtogether-talk-casiljan)

### Get Source and Install Packages
Make and go to the file directory:
<br>
`md consolejsimagescraper`
<br>
`cd consolejsimagescraper`

Clone the repo <br>
`git clone https://github.com/cassieview/CogServiceImageScraper.git`

Install packages <br>
`npm install`

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
* Select "Custom Vision Portal"
* Select 'Sign in"
* Select "New Project"
  - Enter a Name and Resource Group and 
  - Project Types: Classificaion
  - Classification Types: MultiClass General
  - Domains: General
* Create project
* Add and tag images
  - Select "Add Images" and navigate to the train folder for the scraped images
  - Ctrl + A to selet all the images in the folder
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
* If you scoll all the way to the bottom there are code samples in multiple languages to get you started

### Test API in Postman
* Get the predction Url as described above
*  Select "Post" from the dropdown and paste in the url
* Go to the settings and get the Prediction Key
* In the headers add the `Prediction-key` as the key and the actual key as the value
* Auth should be set to no auth
* Select Body > Raw > Json
* Paste in the following Json
``{
  "Url": "UrlForImageGoesHere"
}``
* Send Request

