# 🛣️ Roadmap

## Features needed for soft launch:

* AI advisor
  * Suggested messages
  * Starting message
  * Adapts for current chat information
  * Adapts for the threat survey
* Reworked chat UI
  * Focus on starting new chats
  * Can start working on threat survey (but not submit it) before all AI-on-AI chats have completed
* Wiki
  * Explanations for every gameplay stage
  * Documentation for every dollar sign script
  * Documentation for every AI stage
  * Instructions on how to make a new map
* Editing presets:
  * Upload new maps
* Game to Preset functionality:
  * Starting events
  * Starting round
* Rebellions:
  *

## Bug List:

* Tons of map bugs related to conflict&#x20;
* Added new prompt options:
  * In troop redirection added ${numberOfRemainingTroopsInDefeatedArmy}
  * ${defeatedArmy.remainingTroops}
  * ${defeatedArmy.opposingCountries}
* In WW1 Preset, created an ocean region around South Africa so that pathfinding algorithm isn't nearly forced to go west under South America instead of east under Africa
* Made the "delete logs" button functional
* Removed user ID from chat api request body, made it based solely on verified auth cookie
* Create one universal component for displaying a transformed event&#x20;
* Make it so that countries can move troops within the same region from attack -> defend or vice versa
* Remove code for and delete report-uri account
