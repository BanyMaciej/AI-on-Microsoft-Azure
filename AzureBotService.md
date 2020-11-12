# Azure Bot Service
## 1. QnA Maker
### Intro
QnA Maker is azure cognitive service which allows to create knowledge base (in shape of set of questions and answers) for processing human input. Using NLP and that knowledge base this service can create bot that behave like texting with human assistant. Thanks to that, user input is semantically processing and result is fitted to provided questions and answers.
### Use 
Almost every bot, that base on human questions, like:
- FAQ bot
- first-line support bot
- ordering bot
### How to?
1. Create QnA Maker resource in Azure subscription.
2. Define questions and answers - define pairs of question and answer in QnA Maker portal. These can be imported or added manually. Also there is possibility to add similar questions with same meaning and assign to them same answer - that is helpful for recognising user intentions.
3. Train and test knowlege base - create model with build-in NLP. Then test it using QnA Maker Portal
4. Publish knowledge base - to use with REST it in a bot 
5. Create bot, using Microsoft Bot Framework SDK or build-in QnA Maker creating bot funcionality. Connect knowledge base to bot and deploy it as Azure Bot Service.
### Pricing
There are 2 payment plans:
- Free, with 3 transactions per seconds and 3 managed documents with:
  - Up to 1MB each document
  - Up to 100 transactions per minute
  - Up to 50,000 transactions per month.
- Standard with 3 transactions per seconds and up to 100 transactions per minute. Cost: $10 for unlimited managed documents.

Additionally there is need to pay for necessary resorces to deploy bot - Azure App Service for runtime and Azure Cognitive Search.
## 2. Bot Framework Composer
### Intro
Bot Framework Composer is service that allows to build conversational bot using only graphical interface, with no need to write code. This tool uses most of the newest Bot Framework SDK Features like LUIS and presents them as visual elements that can be connected together. There are some advantages of using composer instead of Bot FrameworkSDK and code:
- possibility to use Adaptive Dialogs for Language Generation
- easy to use
- no coding environment needed
- posiibility to reuse JSON and markdown components
### Use cases
Almost every bot, that base on human questions, like:
- FAQ bot
- first-line support bot
- ordering bot
### How to?
1. Bot Framework Composer - there are distributions for Windows, Linux and macOS.
2. Optionally instal Bot Framework Emulator - that allows to test bot locally
3. Create a new project and using visual interface create necessary triggers, dialogs, activities and custom events. There could be implemented complicated logic of bot behavior.
4. Then bot can be started and tested in emulator
5. Bot can be also integrated with knowledge base from QnA Maker
6. From Composer there is possibility to deploy bot to Azure Bot Service.
### Pricing
Usage of Bot Framework Composer is free, you only need to pay for necessary resorces to deploy bot - Azure App Service for runtime and Azure Cognitive Search for data.
