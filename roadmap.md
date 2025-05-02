# 🛣️ Roadmap

## Features needed for soft launch:

**AI advisor:**

* [x] Suggested messages
* [x] Adapts for current chat information
* [ ] MUCH better prompt needed to explain the entire game, not just bits and pieces like now

**Reworked chat UI:**

* [x] Focus on starting new chats
* [x] Works on mobile
* [ ] Can start working on threat survey (but not submit it) before all AI-on-AI chats have completed

**In Game Tutorial**

* [ ] Modals or interactive arrows with information (videos?) on how to play
* [ ] Need to update data structure around the current user, maybe a flag like "finishedTutorial"?

**Wiki:**

* [ ] Explanations for every gameplay stage
* [ ] Documentation for every dollar sign script
* [ ] Documentation for every AI stage
* [ ] Instructions on how to make a new map

**Game to Preset functionality:**

* [ ] Starting events
* [x] roundsPlayed as a separate data structure vs lastRoundCompleted&#x20;

**Rebellions:**

* [ ] Add a new 'sponsor rebels' or similar action type
* [ ] Add new statistics like chanceOfCoup, chanceOfElection, chanceOfCivilWar, chanceOfSeparatists
* [ ] Correctly trigger rebellions during rounds
* [ ] Add simple heuristic consequences for each type of rebellion

**In game bug reporting:**

* [x] Data structure for bugs
* [x] Functional button in the advanced menu to report a bug with description
* [x] Easily allow admin to view bugged games
* [x] Discord notification in a (privileged?) bug channel when someone reports

**Build eval infrastructure for at least:**

* [ ] chat invitations
* [ ] stat manager
* [ ] generate actions
* [ ] chat with user
* [ ] advisor

**Payments**

* [ ] Set up billing with stripe or someone to allow for users to pay for more tokens

**New Map**&#x20;

* [x] Switch to new basemap with zooms down to street level and dark mode
* [x] Fix a ton of bugs

**User Analytics:**

* [ ] Funnels to answer questions like "what percent of users make it to starting a game" and "among users who start their first game, what percent of them finish the first round?"
* [ ] Good information on exactly how many users reach critical engagement thresholds like "played for at least 3 hours in the last month:

## Bug List:

* Added new prompt options:
  * In troop redirection added ${numberOfRemainingTroopsInDefeatedArmy}
  * ${defeatedArmy.remainingTroops}
  * ${defeatedArmy.opposingCountries}
* In WW1 Preset, created an ocean region around South Africa so that pathfinding algorithm isn't nearly forced to go west under South America instead of east under Africa
* Made the "delete logs" button functional
* Removed user ID from chat api request body, made it based solely on verified auth cookie
* Make it so that countries can move troops within the same region from attack -> defend or vice versa
* Remove code for and delete report-uri account
