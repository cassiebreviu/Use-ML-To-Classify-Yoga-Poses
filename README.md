# Image Scraper using Bing Search Cognitive Service
Simple nodejs console app that uses Bing Image Search to scrape images to a local directory based on search term(s). This example is using yoga pose names to train a custom vision machine learning model to recognize yoga poses.


[Quickstart: Search for images with the Bing Image Search SDK for Node.js](https://docs.microsoft.com/en-us/azure/cognitive-services/bing-image-search/image-search-sdk-node-quickstart?WT.mc_id=techtogether-talk-casiljan)

[Cognitive Service Bing Search Docs](https://docs.microsoft.com/en-us/azure/cognitive-services/bing-web-search?WT.mc_id=techtogether-talk-casiljan)

[Cognitive Service Custom Vision Docs](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/home?WT.mc_id=techtogether-talk-casiljan)

# Create a service that can recognize yoga poses using Azure Cognitive Services

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

### Create Azure Resources
#### Create Bing Search Api
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

#### Create Custom Vision Api
* Go to [portal.azure.com](https://portal.azure.com/)
* Select "Create Resource"
* Search "Custom Vision"
* Select "Create"
* Complete the required fields
* Select "Create"
* When the deployment succeeds you will get a notification in the top right corner.
* Select "Go to resource"
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
   
#### Congrats! You have created a machine learning model that can recognize yoga poses!



