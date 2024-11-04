YAML is one of the main languages used for adding content into space station 14. It's very human readable and can be written in a simple text editor like notepad++ or in an IDE like VSCode or Rider. I like to describe it as fancy text because it's that simple, a logical way of building entities and other prototypes in the game with a list of easily readable text and component which give it functionality. A few examples of things you can do with YAML include:
* Changing the values of damage done by weapons or damage resistances of structures or armors.
* Adding new weapons, medical items, food, armor.
* Adding new tiles, structures, decals or any objects.
* Adding new roles, factions and much much more.

The biggest thing with YAML is knowing where to look and what components to use to get the desired result you want. [https://docs.spacestation14.com/en/ss14-by-example/adding-a-simple-bikehorn.html Here] is a handy guide written by Wizards Den on adding a brand new entity / object to the game and describing a lot of the basics. Explore the rest of our wiki to see our own step by step guides on YAML too.

You can also check out their [https://docs.spacestation14.com/en/general-development/setup.html guides] on setting up a development environment (IDE) and other general guidance on Git etc. If in doubt, speak with a contributor on our discord. We again have our own guides in this wiki too.

## Introduction
So you're ready to take a look into contributing to our projects. The guidance here in is applicable to any Space Station 14 fork however we will use examples from Nuclear14 for reference. For additional help with contributing you can also ask questions in the Wizards Den discord as well as the Einstein Engines discord which is the upstream fork for Deep Station and Nuclear14.

## Folder Structure
All YAML and other important resources in SS14 are held within the `Resources` folder which is typically in your `repository-name/Resources` location. In here you'll find quite neatly folders such as `Audio`, `Locale`, `Prototypes` and `Textures`. These are all handy folders to look into when creating prototypes later on for assets.

YAML is all located in the `Resources/Prototypes` folder which is all the prototypes that make up everything you see in game. All of the upstream content is in this directory so if you need a reference for something you want to make with similar behaviour, look here first. For most forks in SS14, we typically put our content in its own sub prototypes folder to prevent conflicts which for us is in `Resources/Prototypes/_Nuclear14`. The underscore at the start of the name helps organise the folder to either go always to the top or bottom of the folder structure so its easier to find. In this directory you'll find most things are quite logically laid out. Let's run through the folder list as it is at the time of writing to describe what you'll find in each section.

* Access - Here you will find `accesslevel` and `accessgroup` prototypes which are used for roles / ID cards and doors for restricting access to areas in the game map.
* Actions - These are the actions that appear in the actions bar on the left or top of your screen. Generally not beginner friendly.
* Body - Here you'll find prototypes regarding species, organs and body parts for mobs.
* Catalog - Here you'll generally find any lists for storage fills and menus such as point redemption screens or cargo consoles. Storage fills are list of entities that appear within a storage entity when spawned, or with a chance of appearing randomly with a set probability.
* Damage - Here you'll find damage modifier sets which are like your damage resistances to give to structures or mobs.
* Decals - Here you'll find entries for decals for the decal placement menu.
* Entities - The main place you'll spend most of your time, this is where things like objects, structures and mobs are all defined. Things are organised as best as possible here but you might find some things fit in multiple categories such as wallmounts, furniture or decoration, and some things are intentionally separated based on their parenting. When in doubt, do a "search in files" in a program like notapad++ to find all examples of a certain ID or component in that directory.
* Guidebooks - This is where guidebook prototypes are written. This is the structure of guidebooks as displayed in games and what text page they should be showing. For actual guidebook entries head to `Resources/ServerInfo/Guidebooks`.
* Hydroponics - This is where all the prototypes for plants growing are defined with all their relevant variables for growth and harvesting.
* Loadouts - This is where the character creation screen loadouts are defined. Each prototype is an entry in that menu with a different item, its cost etc.
* Procedural - This is where procgen / biome information is stored. Largely you won't need to touch this.
* Reagents - This is where chemicals and other reagents are defined for the game as well as the effects they have on the player and otherwise when used. See the convention for localisation for extra details.
* Roles - This is where jobs / factions / departments are defined as well as things like their inherent access levels and their starting loadout when spawning. See the convention for localisation for extra details.
* SoundCollections - This is where collections of sounds found in the `Resources/Audio` directory are put together into a prototype to make randomly selected sounds for using entities in game.
* Special - This is where SPECIAL stat prototypes are defined.
* Stacks - Another important one relevant to the entities section. This is where stacks which are multiples of entities are defined.
* Tiles - This is where tiles which are the flooring in game are defined as well as their various effects and data. Some are tile prototypes whereas some as actually entities which act like tiles but with additional functionality.

There's various other things in this directory that are loose prototypes that don't deserve a full folder and are fairly self explanatory. If in doubt, ask.

When in doubt about what variables you can edit or the functionality of a component or prototype, searching in the IDE for that component or prototype will give a list of possible bools (true / false options) and datafields (free form entry of options) so you know what functionality you can unlock, or looking at other examples in the codebase for usage.

## Our YAML Conventions
* When contributing new prototypes such as entities, to prevent conflicts its often required to put the forks prefix in the ID name for example instead of `Cloth`, we would have `N14Cloth` for Nuclear14 to ensure our cloth prototype doesn't interfere with any upstream changes and cause conflicts or issues.

* To that effect, always put things in the `Prototypes/_Nuclear14` directory or relevant other directory like `Textures/_Nuclear14` and `Locale/en-US/_Nuclear14` That way we get less conflicts and can find things easier.

* Localisation is also a key element of contributing. A lot of prototypes such as roles and reagents have their names and descriptions replaced with a localisation string which is then defined in `Resources/Locale` to ensure the game can easily be transalted for other regions.

* If you change an existing ID, make sure to create an entry in the `Resources/N14Migrations.yml` file otherwise the maps will break when they try to load an ID that no longer exists.