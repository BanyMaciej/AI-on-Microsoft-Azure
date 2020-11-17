# Driver assistant bot

## Use case

Driver assistant bot is service, which helps drivers in staying avare from exceeding the speed limit. To do that, bot should allow user to report passed police patrol, marking down it's location. Bot should ask for location of user passing police patrol and about type of patrol. Other functionality of driver assitant should allow to check nearby patrols. To do that, bot should ask for user location and then show on map patrols in radius of 10 km. Last feature of bot is showing map of address provided by user.

Driver assistant bot is created using Bot Framework Composer, which connects to Azure Cognitive Services. Additionaly, bot integrates with Azure Maps service to provide images of maps and geographic coordinates of addresses. 

## Bot components

### Bot Framework Composer

Main tool to create this bot is Bot Framework Composer. It's graphical bot creator, which allows to create whole bot logic using tiles. 

First steps to create bot are create dialogs. 

Every dialog have triggers. Trigger could be understand as handling of event. Triggers contains one or more actions. Actions are instructions that bot will execute. Using that actions you can build complicated logic and specific bot behaviour.

Driver assistant bot is composed of main dialog, dialogs for each action and 2 additional dialogs. First one is Menu dialog, which is router of user choice - it asks user for his intention and then provides neccesary dialog. Becouse of that, every dialog has only one trigger, which is started with creation of particular dialog. 

Second additional dialog is GetLocation, which asks user for his location and using integration with maps get geographic coordinates. When user inputs address, it is searching using Azure Maps for it and results as list and asking user to specify one result. Then it saves this address position. This dialog has flag "user.getLocationFailed" to indicate if process ended successfully. It has privided function that allows user to repeat action in case of invalid input.

Main dialog is only for greeting and redirectig user to menu.
Feature dialogs are:
1. ShowMap - showing user position on map. It uses GetLocation and then thanks to Azure Maps integration it creates image of map with pin in center, which points user location. 
2. ReportPatrols - reporting position of police patrol. For now, it stores records in temporary variable - in futher versions it should be integrated with storage services. 
3. CheckPatrols - showing close patrols on map. Works similarly to ShowMap, but there are additional pins that indcate positions of police patrols. For now, it bases only on database mentioned above. 
   
### Azure Maps Integration

To integrate with Azure Maps service there was necessary to create Azure Maps Service. Then, subscription-key was used to authenticate. 
In driver assitant bot 2 functions of Azure Maps was used:
- Search - Get Search Address - it provides search function of address. Search result is array of fitting addresses. Each address has geographical coordinates, which is used by bot.
- Render - Get Map Image - it provides function of getting image of map in specified position. Additionally, there is possibility to add pins in specific coordinates, which is user to specify user and police patrols positions.

Searching addresses with Azure Maps service requires sending HTTP requests. To do that, Bot Framework Composer tile named "Send an HTTP request". It allows to send HTTP request to specified endpoint. 
Downloading map image has been done using Bot Framework Composer cards. This composer funcionality allows to send defined card containing custom images, text and formatting. To display map as image bot sets endpoint to Azure Maps service which returns correct image.

### Bot Framework Emulator

Bot Framework Emulator is tool used to test bot locally. Thanks to it, we could start chat with developed bot and test programmed features. 

## Bot creation steps

To create described bots these steps has been done:
1. Installation of Bot Framework Composer and Bot Framework Emulator.
2. Create dialogs for main features
3. For each dialog create triggers to handle necessary functions - there various actions has been created to handle user inputs and business logic.
4. Create additional dialogs: Menu and GetLocation and connection previous dialogs with them
5. During whole process of developing this bot, Bot Framework Emulator has been used to check developed functions.


## Video presentation

Video presentation of the bot (in polish language):
https://youtu.be/8rPUiWliPfE

