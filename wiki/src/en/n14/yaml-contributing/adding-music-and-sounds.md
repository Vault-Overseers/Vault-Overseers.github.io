# Format
All audio in Space Station 14 / Nuclear 14 is stored in the `Resources/Audio` and `_Nuclear14` subfolder respectively. All audio is in .ogg format and should be MONO not stereo and you can use many free online converters to change from your chosen audio format to .ogg.

Once you've chosen an audio file to add, you'll also need to create an `attributions.yml` file which has all the copyright information in for that file or files. This looks like this:
```
- files: ["war_never_changes.ogg"]
  license: "CC-BY-NC-SA-3.0"
  copyright: "Bethesda Softworks."
  source: "https://www.myinstants.com/en/instant/war-never-changes-fallouts-narrator-15365/"
```
Each file name needs to include the extension and be in quotation marks. You can separate files out with commas if you have more than one file from the same source.
License is what the audio file is licensed under for copyright and usage.
Copyright is the owner or creator of the audio works.
Source is where you got it from.

# Adding Ambient Music
After you've added your files to the relevant subfolder as shown above, now you'll want that music to appear in game. There's a various of places that you can specify audio in game. 
You can create a sound collection from multiple files as shown here:
```
- type: soundCollection
  id: AmbienceWasteland
  files:
    - /Audio/_Nuclear14/Ambience/01-Radiation_Storm.ogg
    - /Audio/_Nuclear14/Ambience/02-Industrial_Junk.ogg
```
The prototype is soundCollection, the ID is something unique to identify the collection, then we have a list of files.

If you head to `Resources/Prototypes/_Nuclear14/audio.yml` you'll find some of our sound collections, rules and ambient music.
To add ambient music, we use the following prototype:
```
- type: ambientMusic
  id: Wasteland
  sound:
    params:
      volume: -12
    collection: AmbienceWasteland
  rules: NearWasteland
  priority: 2
```
Unique to this prototype we have the `collection:` which specifies a soundCollection ID as we made earlier.
`rules` is something we will explore next. `priority:` decides which ambientMusic takes priority when in range of many rules or sources.

Here's an example of a rule:
```
- type: rules
  id: NearSupermarket
  rules:
    - !type:NearbyTilesPercentRule
      percent: 0.25
      tiles:
        - FloorSteelCheckerLight
      range: 3
```
This is telling the game that when more than 25% of the tiles near you are `FloorSteelCheckerLight` that the `NearSupermarket` rule is fulfilled and to play whatever ambientMusic is associated with that rule.

# Adding Lobby Music
Similar to before, you can find most sound collections in `Prototypes/_Nuclear14/SoundCollections` and our lobby music is stored in `lobby.yml`. Adding your new files to that list in the `LobbyMusic` SoundCollection will put it into rotation.

# Adding Jukebox Songs
Jukebox songs are handled slightly different to what we've done so far. Because they're more in-game than the rest, they're stored in a catalogue of songs found at `Resources\Prototypes\_Nuclear14\Catalog\Jukebox\Standard.yml`. Here we have `jukebox` prototypes like this:
```
- type: jukebox
  id: AKissToBuildADreamOn
  name: Louis Armstrong - A Kiss to Build A Dream On
  path:
    path: /Audio/_Nuclear14/Lobby/a_kiss_to_build_a_dream_on.ogg
```
Pretty simple right? The name of what shows in the jukebox and the path to the file. Currently the jukebox just picks from all of these but in future we hope to have records to collect.