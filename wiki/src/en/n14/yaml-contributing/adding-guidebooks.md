# Guidebook Entries
Guidebooks are the equivalent of an in-game wiki and can be hooked into the codebase to automatically generate information or import pictures etc.
Guidebooks have a prototype found in `Resources/Prototypes/Guidebook` or in our case `Resources/Prototypes/_Nuclear14/Guidebooks` and each yaml file is split roughly by the structure you see in game.

For example in `Nuclear14.yml` we have the following guideEntry prototype:
```
- type: guideEntry
  id: Nuclear14
  name: guide-entry-nuclear14
  text: "/ServerInfo/_Nuclear14/Guidebooks/nuclear14.xml"
  children:
  - N14Crafting
  - Factions
  - WeaponsAmmo
  ```
The name is a localisation string, so you'll need to head to `Resources/Locale/en-US/_Nuclear14/guidebooks.ftl` to see the translated name or add any new entries.

The `text` field is the link to the actual contents of the guidebook page, in .xml format.

`children:` is the list of subpages under that heading. So in our case in the guidebook in-game you'll see a Nuclear14 (this entry) and when you click it, you'll se the contents of as shown in the `text:` field but also links to the drop down links to the `children:` pages.

# Guidebook Contents
As mentioned you can find the directory of a guidebooks contents in its `text:` field so lets dive into the above example which can be found at `Resources/ServerInfo/_Nuclear14/Guidebooks/nuclear14.xml`.

These files are in xml format and can be edited in any generic text editor and viewed in a browser. You can view some example xml syntax for formatting [here](https://www.w3schools.com/xml/xml_syntax.asp), and view our existing guidebooks for help formatting.

We can do some useful things with guidebooks such as automatically generate a list of reagents based on their group. See here:
`<GuideReagentGroupEmbed Group="Chems"/>`
This code embeds all reagents with the group "Chems" which is one of the fields in a reagent prototype specified in yaml.

We can also embed singular reagents which will give information about that reagent:
`<GuideReagentEmbed Reagent="Water"/>`

And we can embed entities for their icons:
`<GuideEntityEmbed Entity="N14MaterialRadscorpionTail"/>`