---
description: A non-exhaustive list of features and bug fixes over time
layout: editorial
---

# 🚧 Change Log

## Thursday Mar 6

* wrote documentation for [https://wiki.paxhistoria.co/editing-prompts/regions](https://wiki.paxhistoria.co/editing-prompts/regions)&#x20;
* Default prompts are now available in presets and will automatically update to whatever we consider the best prompt + ai model combination

## Nov - Mar 5

* Fixed pathfinding
* Fixed grey lines during generate actions
* A lotttt of other fixes, too many to list

## Sunday Nov 3

* Alpha tag on landing page
* On mobile no more "Welcome to" it just says "Pax Historia" on the landing page
* The preset store is now adapted for mobile, tabs show at the top and not in a sidebar
* Refactor out preset tab logic from page.tsx into new component
* usePresetsByAuthor hook now works with published presets
* publish toggle correctly updates base "hasPublishedVersion" boolean
* Adjust landing page text sizes so that "alpha" tag doesn't get cut off on mobile
* Fixed issue with dark mode text in the getting started modal

## Saturday Nov 2

* Got rid of beta sign up modal from landing page
* Added log in with Google, and continue as guest modal to landing page
* New accounts now get reasonable starting token amounts:
  * $0.10 for anonymous users who pass recaptcha bot check
  * $0.90 for users who sign in with Google
* Redirect logged in users from the landing page to their dashboard
* Upgraded to nextJS 15 and adjusted for breaking changes
* Guest users get a default incognito mode icon for their user avatar

## Wednesday Sep 24 - Nov 1

* A lot of behind the scenes bug fixes
* Begun work toward a major map refresh (both visually and technically)

## Tuesday Sep 24

* Fixed login during development mode being broken with chrome 129
* No need to refresh page after logging in to update the navbar

## Sunday Sep 22:

* Completed major design refresh of landing page with stars and a more modern font.
* Added and made functional a form to request being added to beta list.&#x20;
* When creating new rounds, each conflict event should add an initial “byRound” that is a copy of the last round

## Saturday Sep 21:

* Began investigation into why deployments have been failing in the last week
* Designed mockup of new landing page

## Saturday Sep 14 - Sep 20:

* Forgot to update change log
* A handful of bug conflict fixes

## Friday Sep 13:

* Added validation and parsing tab to the game "prompts" modal
* Fixed bug where "${thisRound}" would break safeEval. Now resolves to the round number.
* Filtering events for the current round like "${events.with({round: thisRound})}" now works.
* useTransformedCountries now works for a specific round, and is faster because it no longer loads every single round's data
* useTransformedEvents no longer relies on transformed countries
* useTransformedEvents filtering "with" function is now type safe
* useTransformedRegions now works for a specific round, and is faster because it no longer loads every single round's data
* Improvements in the preset "prompts" modal:
  * Can choose a round to parse the prompt as

## Thursday Sep 12:

* Added buttons for changing the current round in the timeline box
* Timeline now only show events for the current round
* Fixed pathfinding bugs:
  * Web worker algorithm is now being properly allowed to complete calculations
  * Paths are no longer overly simplified
  * If given water access, troops now can actually move through those owned straits
  * Pathfinding algorithm no longer breaks when a rough path crosses multiple straits
* Fixed 'undefined country ID' error when parsing prompts in newly created rounds
* Transitioned a ton of old imports of create-battalion to new-create-battalion

## Wednesday Sep 11:

* Firestore security rules to ban the client from changing the total rounds played in a preset or in a game.
* Create a server function to increment round count and cost for a game and the preset it was created from
  * The server makes sure the request is authenticated and that the latest round in the game has really been played.
  * If the round was really played, then the server increments both the game’s totalRoundsPlayed and the preset’s totalRoundsPlayed field
* Notifications are now shown / hidden correctly for old rounds and when creating a new round
* Games now track their total cost and costs across versions
  * Updated type for presetDescription to include totalCostUSD
  * Updated type for versionReference to include versionRoundsPlayed and versionTotalCostUSD
  * Shows the cost of a game in the three dots dropdown (only updates when a new round is created)
* Package updates
* Fixed ESLint errors for useGameDescription and useVersionDescription

## Tuesday Sep 10:

* Several updated types with better field names. Ex: within preset data, uid field is now called gameUID and the arguments passed to getAIResponse are consistent with the column names in Supabase.
* When selecting logs, the ‘delete’ button (non functional) at least shows the right number of logs to delete
* Logs include the preset owner id now
* Large fields in logs (prompt, template, and AI response) are now loaded per-log and only when requested
* Supabse row level security to completely lock down any edits or reads from anything other than the Vercel server&#x20;

## Monday Sep 9:

* Can select logs, but can’t do anything with them yet

## Wednesday Sep 4:

* Add sorting and country names to read-logs in preset
* Logs now store the time, tokens in, tokens out totalCost
* Buttons to choose the visible columns and refresh the logs
* Fixed error with prompt modal in preset not showing AI output
* Correct validation function for generating chat invitations, and can scroll within column selector
* Corrected 150+ errors to be the special “validation error” type

## Tuesday Sep 3:

* Tried and failed to get row level security working with firebase auth cookies and no JWT
* Created Supabase table schema and types
* Added read-logs api route
* Refactored getAI response to return response text and errors separately and log AI input and output to Supabase
* Added extremely basic, half functioning log table for logs in the advanced tab of presets

## Monday Sep 2:

* Decided to use Supabase as the database for logging

## Sunday Sep 1:

* Created default empty optional data for safe eval with explanatory field values like “No chat provided” or “No action description provided” etc.&#x20;
* No more client side error if de-selecting a chat in the prompt modal (preset screen)
* Can select chats in the prompt modal (in game)
* Now no longer necessary to to select a country to parse a prompt in the game or preset prompt modals.
* countryID is now optional for safeEval, and the returned state of ‘isLoadingSafeEval’ is actually the correct value now
* No more client side errors when changing games in the preset prompt modal
* Chats are now summarized for the player as well as for the AI’s involved
* Fixed bug where transformed conflict events would try and access battalion descriptions by round that didn’t exist yet
* Fixed bug where transformed threat surveys toString was causing errors inside safeEval
* Created a tab for JSON Parsing to replace the validation tab inside the prompt modal (in game only) that shows the entire parsing pipeline, and the contents at each stage
* When parsing JSON, it will correctly escape quotes and newlines within fields, no matter how deeply nested
* Changed the allowed list of defendable regions to now:
  * Include all regions that are physically accessible and you have military access to
  * Include all regions you control (puppets, occupied, owned)
  * Bordering regions are no longer included by default

## Saturday Aug 31:

* Got openRouter models working again
* Validates that move troops actions don’t have the same destination as their current location
* Move troop events toString now includes the starting region of the troops
* Unified and simplified prompt type definitions
* Fix bug so that changing a country’s name now properly edits empty alternative names
  * This will also fix bug where establishment actions are valid, but right now are being rejected because the validity function sees ‘null’ for the nameAsPuppet
* Create modal skeletons for missing advanced settings
* Added mutation to usePreset
* Added an advanced setting for auditCountryNames that can find countries with empty names and replace them across the preset
* Threat survey is created with the correct ‘type’ field value
* Threat survey events can now be transformed, and have a reasonable toString function
* Events on the gameplay timeline correctly show newline characters
* Timeline separates out events visible to the player, and those hidden from them
* Clicking 'clear events' for the chat stage in the set stage modal works now
* ${events} in safe eval are sorted by round with a header for each round
* Chat events have a reasonable toString that includes a summary of how the chat went

## Friday Aug 30:

* The tip for how to get AI generated actions is just a tooltip, it's no longer text that causes layout shift
* Tried and failed to get meticulous E2E testing set up
* Added troop redirection prompt and optimized the visual order of prompts on the edit screens
* Fixed bug where when deleting all games it was possible for the operation to only complete halfway. However it's now extremely slow
* Fix notification bug that showed all notifications when only the chat stage was complete
* Fix order of edit stages modal to show chats first
* The “Clear Events” button for the conflict stage now resets troops to how they were at the end of the last round
* Conflict events toString now includes&#x20;
  * Description of attack
  * Description of defense requests and their responses
  * Descriptions of defending and attacking troops
* npm package updates
* Major chat refactor
  * Moved chat stage to beginning of turn
  * AI countries start planning their chats and doing AI-AI chats automatically when the chat modal is opened, no input needed from user
  * Users can start as many chats as they want
* openRouter models work (like the new gemini flash models)
* openRouter models became broken again!!

## Thursday Aug 29:

* Created a lot of google slides for potential simplified ui
* Created empty autopilot modal
* Emoji for events
* Generate actions modal now uses the same toStrings as the timeline box
* Changing a country’s name also changes unset other names
* New games start on round 1
* In the stage modal, clearing events and battalions for conflict no longer destroys defense minister battalions
