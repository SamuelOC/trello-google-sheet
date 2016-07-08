# Google Sheet script - Import Trello data 

[![WTFPL license](http://img.shields.io/badge/License-MIT-blue.svg)](http://opensource.org/licenses/MIT)

A Google Sheets script that imports [Trello](https://trello.com/guide) data into the Google Sheet. 
The data will be imported in 2 ways :
1. A main sheet listing information of each card the user has access to accross all boards and lists
2. A new sheet for each board giving a simple version of the view on Trello

The requirements for this script is only to get very basic data and include any stickers that is added on cards. The script is not very efficient due to making a REST call for each card in order to retrieve the sticker data.

A menu will be added with the following options :
- **Update Main Sheet** : Updates only the main sheet
- **Update All Board Sheets** : Updates all the sheets (including main)
- **Update Current Board Sheet** : Updates the current active board sheet
- **Clear all** : Deletes all board sheets and resets the main sheet

## Trello API
See [https://developers.trello.com/](https://developers.trello.com/) for more details on the Trello API calls

## Authorising
Google sheets depricated their built in OAuth 1.0 api and now only supports OAuth 2.0 ([OAuth1 docs](https://developers.google.com/identity/protocols/OAuth_ref)). As Trello only supports OAuth 1.0 we have to use a token to authorise the REST calls. The developer API key and token will have to be included in all REST calls. 

You should replace the placeholder values for :
- trelloKey
- trelloToken
- username

To get your developer API key go to [https://trello.com/app-key](https://trello.com/app-key). Generate the token with the following URL pattern : https://trello.com/1/authorize?key={trelloKey}&name=GoogleSheets&expiration=never&response_type=token&scope=read,write. 

## Global variables

- trelloKey : Developer API key
- trelloToken : Generated token
- trelloAPIEndPoint : Trello REST API base URL
- username : Your Trello username
- mainSheetName : Name of the main sheet
- insertCardStickers : Flag indicating wether sticker images must be inserted
- addBoardSheets : Flag to indicate if sheets must be created for each board (Main sheet will always be created and populated)
- delimiter : delimeter to split card labels and sticker string


