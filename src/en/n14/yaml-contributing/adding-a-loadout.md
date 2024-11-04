# Loadouts
## Role startingGear
Loadouts may refer to one of three things, the first is the role loadout which in code is called a `startingGear` prototype and can be found in the `prototypes/_Nuclear14/Roles/Jobs` directory in the respective role file. This is a list of equipment that always spawns with the person unless changed in their loadout. This is the legacy loadout.

## Loadouts 2024
The second is the actual Loadouts system added in 2024 which the player accesses in their character preferences. These are found in `Resources/Prototypes/_Nuclear14/Loadouts` and have a file per category e.g. `head.yml` for head loadout items. If we dive into this file we get the following code example:
```
- type: loadout
  id: N14LoadoutHeadHatBaseball
  category: Head
  cost: 0
  requirements:
    - !type:CharacterItemGroupRequirement
      group: N14LoadoutHead
  items:
    - N14ClothingHeadHatBaseball
```
Breaking this down we have the prototype which is `type: loadout`, the ID for this loadout item, the category which are listed in `Loadouts/categories.yml`, it's cost if it should cost any loadout points (if you don't put this line it will default to 1), any requirements for taking this loadout item such as requiring a certain role, species etc and finally the item prototype ID it should give for selecting this loadout option. You can also put `exclusive: true` below cost for example if you want it to replace the startingGear or be the only item on that category the player can take.

If you want a species requirement you can use the following code, replacing `Vox` with whatever species e.g. `Ghoul`:
```
    - !type:CharacterSpeciesRequirement
      species: Vox
```
If you want a specific job to have this loadout option you can use the following code, replacing `StationEngineer` with whatever role ID you want:
```
    - !type:CharacterJobRequirement
      jobs:
        - StationEngineer
```
This isn't an exhaustive list of loadout options but its a good start. Poking around the loadout system and component in an IDE is a good way to find more options.

## Kits
Kits are a third form of loadout and are fairly unique to Nuclear14. They aren't actually loadouts as such but instead use an entity with a UI for selecting a kit from a list, then said kit which is another entity that on being used spawns a bunch of entities. So lets break that down.

Head to `Prototypes/_Nuclear14/Entities/Objects/Specific/Kits` and in here you have `UndecidedLoadout.yml`. In this file you have the first entity we mentioned that has the UI with a list of available kits. Each kit has a unique ID, name, sprite state and specific to this guide is the component `type: UndecidedLoadoutBackpack`. For example, the NCR trooper kit has the following setup for that component:
```
  - type: UndecidedLoadoutBackpack
    transformAfterSelect: AlwaysPoweredWallLight
    possibleSets:
    - RiflemanSet
    - MarksmanSet
    - PointmanSet
    - MoraleSet
    - MedicSet
```
The possible sets is the part we're interested in as this is the list of options that you can choose.

If we scroll down in this file we have the prototypes for `UndecidedLoadoutBackpackSet` that match these IDs listed in `possibleSets`. The RiflemanSet for example looks like this:
```
- type: UndecidedLoadoutBackpackSet
  id: RiflemanSet
  name: undecided-loadout-category-rifleman-name
  description: undecided-loadout-category-rifleman-description
  sprite:
    sprite: _Nuclear14/Objects/Misc/kits.rsi
    state: rifleman
  content:
  - KitRifleman
```
Breaking this down we have the unique ID, name and description which are in a localisation string (guide to follow, for now go to `Resources/Locale/en-US/_Nuclear14/undecidedloadout.ftl` and fill out an entry), sprite and content. The content is again the entitiy ID of what should be spawned if you select this option.

To find these kits and their contents you now want to go back out of this file to the folder `Kits` and into the file `kits.yml`. In here you'll find the list of kits that are spawned when you select them from the previous entity. The important part is the contents which can look like this:
```
  - type: SpawnItemsOnUse
    items:
      - id: N14ClothingOuterNCRVestSnow
      - id: ClothingBeltNCRPouches
      - id: N14WeaponRifle556Service
      - id: Magazine556Rifle
        amount: 4
      - id: N14WeaponPistol9mm
      - id: N14MagazinePistol9mm
        amount: 2
      - id: N14CombatKnife
      - id: N14BoxCardboardMREBoxCFilled
    sound:
      path: /Audio/Effects/unwrap.ogg
```
This is a list of all the entity IDs that will spawn and in what amounts if you use this item.


So to recap, if you want to create a new kit you'll want to go to the `UndecidedLoadout.yml` file, copy one of the existing options and put it under the correct heading e.g. under `#MARK: BoS Midwest Kits` if you want to make a Midwest BOS kit, give it a unique ID but following the convention e.g. `BoSRifleSet`, give it a new localised name and description, making sure to fill out an entry for this in the correct `locale` file, giving it an appropriate sprite state, then giving it a correct `content:`. 

This is the kit done, if it's for an existing role then head back up to the top of the file and add it to the `possibleSets:` list for said role, or if its for a new faction, role or kit entirely, copy paste one of the `type: entity` options, again giving it a new ID following the format in the file, then giving it a new `UndecidedLoadoutBackpack` component with the relevant `possibleSets:` with the kit you previously made.

Then we need to make said `content:` so we head to the `kits.yml` file, copy one of the existing kits and put it under the relevant heading again for the faction, give it an ID that matches the ID you put under `content:` in the previous file, making sure its unique but follows the format, give it the correct name and description for what it is then fill out its `SpawnItemsOnUse` component list.

In total you should have edited 3 files. `kits.yml`, `UndecidedLoadout.yml` and `undecidedloadout.ftl`. Then head back to the first section of this guide if you want to aid the kit selector to a role on spawn like it is for other existing roles e.g. for the `ncr_cadet.yml` its `pocket1: NCRtrooperloadoutkits`. You can generally put any entity in a kit, but stick to objects which you can find IDs for in `Prototypes/_Nuclear14/entities/objects`.
