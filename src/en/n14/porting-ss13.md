# Porting Assets from Space Station 13
## Where to find things and Basics
To preface this guide, code between SS13 and SS14 is not compatible and cannot just be copy pasted or ported simply. When we refer to porting we refer to art assets like icons / sprites and sounds. This guide is primarily concerned with sprites.

The main resource for obtaining SS13 sprites and assets is through the Github pages for that repository. If you know the name of the repository you can search that on Github or your search engine of choice. 

Sprites are typically found in the top level `icons` folder, or depending on the codebase they might have been smart and separated their specific sprites into a folder first like `fallout`, `goon` `tg` or `mojave` as an example and then into `icons`.

Icons follow a similar structure to SS14, separating things into decals, effects, mobs, objects and structures. Tiles are called turf in SS13 and there are some othe minor differences.

Icons are stored as PNGs but within a .dmi file. You can open .dmi files with dreammaker, the byond software however if you're porting to SS14 I'd recommend just opening them with RSI Edit. You can download the [latest version here](https://github.com/space-wizards/RSIEdit/releases/), 
extract it and run the .exe. You can then copy and paste the link directly to the .dmi from Github by right clicking the file and copy link, then paste it directly into RSI Edit to open it. This preserves the copyright information for later and the source. More on that in a moment.

Another tool I'd like to reference now is [Scrubby Icon Search by MelonMesa](https://scrubby.melonmesa.com/icon/search). If the codebase you want to look in is on there, try searching key words to find the sprite you want and it will find the .dmi it is in. This is important
because a lot of SS13 sprites can be in weird places or wrong files making them hard to find.

## How to port
So as mentioned above, the number one way to port things is with RSIedit which is the method we will cover here. Follow the instructions above to get it, copy paste your link to a .dmi in there.

Then you can go through deleting any sprites from that view you don't want to port, renaming them to suit the naming convention of the fork e.g. kebab or snake case, (or because they were originally named stupidly) or just with more logic e.g. adding numbers to like sprites.
On this topic, some SS13 sprites might have matching names with other sprites so they WILL need changed.
Also worth noting, in SS14 we use a format called .rsi to replace .dmi. This is the collection of sprites that the game can read. In SS13 for an item the icons would be in one folder and the "onmob" or worn or inhand (held) sprites are in separate folders, so you'll need to dig those out.
You can then export individual sprites from RSIedit as PNGs into another folder, in RSIedit hit file > new, then drag and drop those sprites in there to make a new .RSI, making sure to copy paste one of the copyright lines in too to preserve credit. This will be necessary for any weapons and clothing especially.

Once you're done you can save / export that file as a .RSI into the textures directory of your fork. You'll notice a meta.json file will have been generated in that folder. This is what tells the game how to read your sprites for example telling the game if your sprite has directions, animations and the size of a single sprite state in that file.
Make sure to check that all sprites in that file are the same dimensions, and if a sprite has multiple directions or animation states it will have a multiple of that direction and must match / divide equally between the directions / states, the dimensions of the file and the size stated in the meta.json.

## I have my RSI, what now
Now you canm follow the YAML Contributing guides and make the item, pointing the sprites towards your new .rsi file.