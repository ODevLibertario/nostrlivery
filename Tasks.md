## Roadmap

- T1:select-nostrlivery-node [done] by ODevLibertario  
Before login allow the user to input a nostrlivery-node URL and send, when you call an endpoint on that URL that is a GET url/identity the server will return an npub. Store this url and the npub in the apps memory. If those fields are not present in the memory then always return to this set node screen.<br><br>
If on calling the endpoint the call fails or doesn't return a valid npub show the user an error, if it succeeds redirect to the login page (this could be on the login page, this hide login and show this instead).<br><br>
The nostrlivery-node should on startup receive two env variables for nsec and npub so it can make the identity endpoint work and also sign events back to the client.

- T1.1:nostrlivery-node-authentication [done] by ODevLibertario  
This depends on T1 being completed, on every response from the node besides the identity endpoint
return a signed nostr event and make sure the apps verify every response with the npub they have in memory from when their selected the node.

- T1.2:nostrlivery-change-node [done] by rainanDeveloper  
Allow for the user in the profile screen to set another nostrlivery node to use and also show the URL of the current node being used

- T2:set-company-location [done] by ODevLibertario  
When the user is logged in, in the company app. Allow if to go to the profile tab and set his company location, the simples way is to add to fields to the screen that ask for latitude and longitude, of course this is not user friendly so we could also add a field that receives a google maps location URL and parses that to extract longitude and longitude.<br><br>
Once the user sends his location to the server, update his profile event k0 with no tags to add the following object {"location":{"latitude": 123, "longitude": 123}}.<br><br>
Also allow for the user to update his location at anytime

- T3:configure-menu [started]  by ODevLibertario
Allow a logged in company user to setup his company menu, it should be a crud of menu items,
each item having a picture(this is low priority on this task if it's too difficult), a name, a description, a price and a category (do we need more fields?).<br><br>
The user will configure his menu on the app and then when he presses save a JSON object of the menu will be sent to the node as a nostr event kind 30000 with the d tag with the value menu.<br><br>
The user should be able to edit his menu at any time
