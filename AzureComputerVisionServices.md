# Process and classify images with the Azure cognitive vision services

## 1. Computer Vision API
### Intro
Computer Vision API provides various image processing alghoritms to process images and extract from them insights. There are few key features from this API:
- OCR - to recognize text from image
- Image understanding - to recognize objects from image
- Spatial analysis - to recognise people movement in space
- Face API - to detect and identify human faces, compare them and group unidentified faces.
- Emotion API - to recognize confidence of some emotions from face (such as anger, fear, hapiness etc.). Returns confidence for all of there emotions. 


### Use cases
* CCTV,
* face identification,
* auto-recognision of people on the photo,
* detecting handwritten text and recognising it.

### How to
1. Create resource: Cognitive Services and demanded features of API
2. Obtain subscription key to this feature
3. Get response using web request, filling up subsription key.

### Pricing
Free version provides 5000 transactions per month with 20 per minute. S1 pricing tier depends on features and amount of transactions, providing up to 10 transactions per second.

## 2. Custom Vision
### Intro
Custom Vision allows easilly create image classification model from previously created labeled images. Usage of model generated from Custom Vision is easy to use - it only requires few lines of code.

### Use cases
* recognision of defined objects on image
* finding labels for objects

### How to
1. Create project on https://www.customvision.ai/
2. Create dataset of labeled images
3. Create and train model 
4. Test using Quick Test
5. Future usage could be used with web requests over http. (need to use subscription key).

### Pricing
Free for 2 TPS, upload, training and prediction transactions, up to 1 hour training per month and 5000 training images free per project (max. 2 projects) and 10000 predictions per month.
Standard provides 10 TPS and max. 100 projects, and pricing depends on usage.

## 3. Video Indexer
### Intro
Video Indexer allows to index and extract insights from video data. Additionally, we can search some content in videos. This service includes face identification, object labels, text recognition, scene segmentations, and other useful features.

### Use cases
* filtering videos for content,
* censuring videos,
* finding key moments in videos,
* video live stream analysis,
* fitting ads based on content of watched videos

### How to
1. Create subsription on Video Indexer Developer Portal. 
2. Get credentials from portal
3. Using API (or portal) upload videos and get response

### Pricing
Free 10 hours of indexing to website users and up to 40 hours of indexing to API users.
Other pricings vary on features used and usage.
