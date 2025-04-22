# 🛣️ Roadmap

## Features needed for soft launch:

* AI advisor
* Reworked chat UI
* Good documentation on how to play
* Stable stat manager
* Chats considered 'fun'
* Starting events
* Game to Preset functionality
* Stability through at least round 12
* Billing

## Bug List:

* Added new prompt options:
  * In troop redirection added ${numberOfRemainingTroopsInDefeatedArmy}
  * ${defeatedArmy.remainingTroops}
  * ${defeatedArmy.opposingCountries}
* In WW1 Preset, created an ocean region around South Africa so that pathfinding algorithm isn't nearly forced to go west under South America instead of east under Africa
* Made the "delete logs" button functional
* Games now have a logs modal, just like presets do.
  * Edit existing read logs api so that requests include filters for a specific preset or game id
* Removed user ID from chat api request body, made it based solely on verified auth cookie
* Create one universal component for displaying a transformed event&#x20;
* Make it so that countries can move troops within the same region from attack -> defend or vice versa
* Remove code for and delete report-uri account
