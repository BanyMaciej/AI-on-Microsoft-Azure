# Dogs Breed Recognizer using Azure Cognitive Services
### Project
This project implements recognizing dogs breed from image. Solution is based on ML model developed using Azure Custom Vision. Using photo of dog we can ask service for probability for few breeds. 

### Dataset
Dataset for training the model is ImageNetDogs from Stanfrod database. This dataset contains a lot of images of dogs categorised by breed. Whole dataset provides 120 classes (breeds) and over 20 000 images.
http://vision.stanford.edu/aditya86/ImageNetDogs/

### Custom Vision
To train the model using Azure Custom Vision, there is necessary to create Azure Cognitive Services resource. Next, in custom vision portal (https://www.customvision.ai/), after logging in, it is possible to create new project and setting up connection to cognitive services.
![AzureCreateCustomVisionProject](https://github.com/BanyMaciej/AI-on-Microsoft-Azure/raw/main/Assets/AzureCreateCustomVisionProject.png)

### Data preparation and upload
Free version of Azure Custom Vision provides up to 50 tags and 5000 images per project. Thus, 120 classes to 50 and from 20530 images to 100 for every used tag. 
To prepare dataset for training with Custom Vision python api was used by installing package:
`azure-cognitiveservices-vision-customvision`. That package allows to create tagged images which could be used by Custom Vision service (i. e. ImageFileCreateEntry). Creating this dataset has been done using attached Jupter notebook: [AiOnAzureVisionDataPreparer.ipynb](https://github.com/BanyMaciej/AI-on-Microsoft-Azure/blob/main/AiOnAzureVisionDataPreparer.ipynb).

Each image has been placed in ImageFileCreateEntry with corresponding tag and dog's boudaries. This data could be found in provided dataset in xml format.

List of ImageFileCreateEntry objects (containing 5000 images) was uploaded to Custom Vision service. To do that, whole list has been splited to batches of 50 images and uploaded using `trainer.create_images_from_files` method. Some of images retured status `OkDuplicate` and was skipped. After uplading in Custom Vision portal could be found 4995 training images.
![enter image description here](https://github.com/BanyMaciej/AI-on-Microsoft-Azure/raw/main/Assets/AzureCustomVisionDataset.png)

### Training
Next step was training model using these training images. It was really easy - it comes down to click "Train" button in https://www.customvision.ai/. 
After some time of training (aprox. 15 minutes), model's performance charts was displayed. Model seems to be properly trained with quite good results. Propably using more images for training would led to even better accuracy.
![enter image description here](https://github.com/BanyMaciej/AI-on-Microsoft-Azure/raw/main/Assets/AzureTrainingResult.png)

Trained iteration has been published and then it's ready for testing.

### Tests
After publishing, trained model was tested using quick test feature in Azure Custom Vision portal and with sending http request.
#### Quick test
That feature allows to fast and easy test model with custom images. There is possibility to upload image from computer or using image's url. For the test, two different breeds and thier images from wikipedia has been selected: [Airedale](https://upload.wikimedia.org/wikipedia/commons/6/6b/Wystawa_Rybnik_02.10.2011_airedale_terrier_1pl.jpg) and [Whippet](https://upload.wikimedia.org/wikipedia/commons/5/5e/WhippetWhiteSaddled_wb.jpg). These images were not included in training dataset.
After filling image url and pressing enter, image was processed and results was displayed. For both images correct breed was predicted.
![Airedale](https://github.com/BanyMaciej/AI-on-Microsoft-Azure/raw/main/Assets/AzurePredictionTestAiredale.png) 
![enter image description here](https://github.com/BanyMaciej/AI-on-Microsoft-Azure/raw/main/Assets/AzurePredictionTestWhippet.png)
#### Http requests
Usage of service was also tested using http requests using program Postman. All connection informations could be gathered after clicking on "Prediction URL" button.
Test has been done with downloaded image of [Beagle](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/Beagle_Faraon.JPG/1200px-Beagle_Faraon.JPG). 
Again, model correctly recogized breed - prediction value for beagle is greater than 0.5.
![Beagle](https://github.com/BanyMaciej/AI-on-Microsoft-Azure/raw/main/Assets/AzurePredictionTestBeagle.png)
#### Video presentation
ideo presentation of the solution (in polish): https://youtu.be/uOh867XiIh0
