# 🛣️ Roadmap

## Features needed for soft launch:

**AI advisor:**

* [x] Suggested messages
* [ ] Adapts for current chat information
* [ ] MUCH better prompt needed to explain the entire game, not just bits and pieces like now

**Reworked Chats:**

* [x] Focus on starting new chats
* [x] Works on mobile
* [ ] Next Speaker - Either AI or Player chosen
* [ ] Test chat functionality and fix bugs for many rounds

**In Game Tutorial**

* [x] Modals or interactive arrows with information (videos?) on how to play
* [x] Need to update data structure around the current user, maybe a flag like "finishedTutorial"?

**Wiki:**

* [ ] Rewrite the initial page
* [ ] Legacy Presets for existing pages
* [ ] Explanations for every gameplay modal
* [ ] Documentation for every AI stage
* [ ] Documentation for scripting language
* [ ] Instructions on creating a new preset
* [ ] Instructions on how to make a new map

**In game bug reporting:**

* [ ] Data structure for bugs
* [ ] Functional button in the advanced menu to report a bug with description
* [ ] Easily allow admin to view bugged games
* [ ] Discord notification in a (privileged?) bug channel when someone reports

**Payments & Accounts**

* [ ] Set up billing with stripe or someone to allow for users to pay for more tokens
* [ ] Discuss subscription
* [ ] Find out price per hour
* [ ] Revamp account details UI and page, make it easier to manage
* [ ] Revamp public profile UI to be fully functional minimally

**Prompts**

* [ ] Write all default prompts
* [ ] Revamp prompt UI in presets

**New Map**&#x20;

* [x] Switch to new basemap with zooms down to street level and dark mode
* [x] Fix a ton of bugs
* [ ] Add map markers - battalion is just one of them, and make this compatible with AI
* [ ] Find out if new Map painting stage needed

**User Analytics:**

* [ ] Funnels to answer questions like "what percent of users make it to starting a game" and "among users who start their first game, what percent of them finish the first round?"
* [ ] Good information on exactly how many users reach critical engagement thresholds like "played for at least 3 hours in the last month:

**Database**

* [ ] Audit rules for firestore and fire storage
* [ ] Audit supabase table rules
* [ ] Increase server time limit
* [ ] Audit login process

## Bug List:

* Remove code for and delete report-uri account
* ~~Advisor needs to see the latest message correctly~~
* ~~Chats needs to see the latest message correctly~~
* Default prompts not used properly when creating games
* Fix issues with speed -&#x20;
  * when clicking on public profile
  * when clicking on a preset from preset list
  * when clicking on account details
* simple-presets -> presets, simple-games -> games, move old to legacy
* round number updates multiple times, triggering multiple map rerenders
* ~~battalions being editable on published presets~~
* textareas not available when tutorial modal open
* tutorial modal scrolls outside\
