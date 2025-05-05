# 👲 Troop Movement

**Which regions can you attack?**

* Regions that border land you can access (either because you own it, or because you've been given military access by the country that does)&#x20;
* You can NOT attack regions you own
* Regions owned by countries that have given you military access through their lands.

**Which regions can you defend?**

* Regions you own of course
* Regions owned by countries that have given you military access
* Special case: if you were sent a military defense request by a country that has not given you military access through their lands, any battalions you send specifically in response to that request will gain access to only that region.

**How do we display to the AI that certain regions are only accessible by certain battalions?**

* The group of battalions (battalion\_3 located in Southern USA, battalion\_4 located in Germany) can attack these regions:
  * coastal region 1
  * ...
* A different group of battalions (... with location) can attack these regions:
  * interior region 2
  * interior region 3
  * ...
* Notes:
  * There could be a tiny bit of overlap between each 'island' of battalions in terms of attackable regions.

**What happens to troops in land owned by a country that revokes military access?**

* The country revoking access must decide to either:
* "send home peacefully"
  * Which means: battalions are redirected to the nearest defendable region. And none die along the way.
* "attempt to capture"
  * Which means: battalions travel to the nearest defendable region, but as they're traveling a percent of them die daily based on:
    * how much the leaving country trusted them (if you gave them a super low threat then more will die)
    * Relative amounts of troops retreating to the defending troops and population.

**How do battalions decide the path they take?**

* We just get the fastest route (not just shortest distance, because water travel is much faster in most time periods) that goes through land, oceans, and straights you have military / straight access to.

