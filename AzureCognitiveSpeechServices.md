# Azure Cognitive Speech Services
## 1. Intro
Thanks to Speech Services contains 3 main functions: Speech to Text, Text to Speech and Speech Translation. Using first one we can transcribe audio streams in real-time using AI and ML. 
Text-to-speech provides inverse processing, creating synthetized voice of text. Last service translates provides funcionality of translating audio input. 

Processed text can be in many different languages, whic makes it useful as translation service or multi-language translator. This services also provide functions that could be used as other way of communication (i.e speech instead of text).

This service works as end-to-end system, which could be used by applications or other services. To integrate with that service we could use REST Api or dedicated SDK. 

Main functinalities of this service are:
- providing transcriptions to impore applications
- translate speech
- speech and voice synthetizer 
- integrate with LUIS to recognize entities

## 2. Use cases
- translating of live conferences and speechs
- real-time communication in different languages
- customer support
- subtitling media
- talking bots
- personal notes using speech
- writing text messages in car


## 3. How to
1. Create Azure Speech resource by using the Azure portal, the Azure CLI or the Cloud Shell, saving subscription-key.
2. Integrate over REST api passing subscription-key in query parameters. Endpoint could be found in azure portal in created resource.
3. Every funcionality has own endpoint and key, which should be used.

## 4. Pricing
Speech Services has 2 versions: free and standard. Free one provides per month: 5 hours of Speech to Text, 5 million characters in of standard input of Text to Speech, 5 audio hours of Speech Translation.
Standard version pricing vary on usage, which is using only standard features: 
- Speech to Text: $1 per audio hour
- Text to Speech: $4 per 1M characters
- Speech Translation: $2.50 per audio hour
