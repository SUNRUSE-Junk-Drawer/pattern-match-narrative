# pattern-match-narrative
Experimental narrative generation implemented during a flight

I saw a [YouTube video](https://youtu.be/k2rgzZ2WXKo) the night before my flight back from a holiday and decided to experiment with a DSL and data store built for it.

The data store is to be a triplestore-lite, wherein all data is to be stored as a subject, property and value.
Ideally, changes would therefore be applicable in patches, similar to how Bethesda's Gamebryo family allow for modding.

The DSL will apply a pattern matching system to the aforementioned data store, then capable of executing simple procedures.

Example syntax:

```
Create True
Create False

Create PartyFaction
Create MonsterFaction

Create Cave
Create Road
Create Road-Cave
Set Road-Cave From Road
Set Road-Cave To Cave 

Create Hero
Set Hero Faction PartyFaction
Set Hero Dead False
Set Hero Location Road

Create Spider
Set Spider Faction MonsterFaction
Set Spider Dead False
Set Spider Location Cave

Scenario Move
	When actor Location fromLocation
	And link From fromLocation
	And link To toLocation
	Set actor Location toLocation

Scenario Attack
	When attacker Faction attackerFaction
	And attackee Faction Not attackerFaction
	And attackee Dead False
	Set attackee Dead True
```

An example narrative which could be randomly generated from this dataset:

- Hero moves to Cave.
- Spider moves to Road.
- Hero moves to Road.
- Spider attacks Hero.
