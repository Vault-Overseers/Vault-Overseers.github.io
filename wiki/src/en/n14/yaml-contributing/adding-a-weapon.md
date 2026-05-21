# Intro to Weapons
All of our gun yaml (code) is located at `Resources/Prototypes/_Nuclear14/Entities/Objects/Weapons/Guns` and are broken down into sub folders depending on the type of weapon.

Most types of guns already exist in one form or another so the quickest way to add a gun is to parent off of an existing one. In the below example we will go over adding a unique variant of a weapon to start, and expand from there.

## Unique Named weapon
Let's say we want to add the "Ol' Painless" from Fallout 3 to the game. Head to where we currently keep our hunting rifles in this path:
`Resources/Prototypes/_Nuclear14/Entities/Objects/Weapons/Guns/Snipers/snipers.yml`
Inside you should find our current hunting rifle code:
```
 - type: entity
  name: hunting rifle
  parent: BaseWeaponSniper
  id: N14WeaponSniperHunting
  description: A rugged bolt action rifle. Uses .45 ammo.
  components:
  - type: Sprite
    sprite: Nuclear14/Objects/Weapons/Guns/Snipers/hunting.rsi
  - type: Item
    sprite: Nuclear14/Objects/Weapons/Guns/Snipers/hunting.rsi
  - type: Gun
  - type: BallisticAmmoProvider
    whitelist:
      tags:
      - CartridgeMagnum
    capacity: 10
    proto: CartridgeMagnum
```
Now if we wanted to make an entity with a lot of the same features as this one, we can simply use it as a parent and not need to duplicate all the code. This would look something like this:
```
- type: entity
  name: Ol' Painless
  parent: N14WeaponSniperHunting
  id: N14WeaponSniperHuntingOlPainless
  description: A special bolt action rifle. Uses .45 ammo.
```
Notice how the parent has now changed from BaseWeaponSniper to our previous hunting rifle entity. This means it will inherit all of the components it has. Any component you now write that are the same as the parent will override that component only. For example, we now inherit the sprite component so the sprite is the same.

If we wanted to keep all the other things the same but only change the sprite we could simply add:
```
  components:
  - type: Sprite
    sprite: Nuclear14/Objects/Weapons/Guns/Snipers/newsprite.rsi
```
Now to truly give our new weapon something special about it we would need to change more than just it's name and description. We could for example:
Change the firerate with this component:
```
  -   - type: Gun
    fireRate: 4
```
Change the ammo it takes and thus the damage it outputs with this component:
```
  -   - type: ItemSlots
    slots:
      gun_magazine:
        name: Magazine
        startingItem: MagazineLightRifle
        insertSound: /Audio/Weapons/Guns/MagIn/ltrifle_magin.ogg
        ejectSound: /Audio/Weapons/Guns/MagOut/ltrifle_magout.ogg
        priority: 2
        whitelist:
          tags:
            - MagazineLightRifle
      gun_chamber:
        name: Chamber
        startingItem: CartridgeLightRifle
        priority: 1
        whitelist:
          tags:
            - CartridgeRifle
```
In this section we would be changing MagazineLightRifle to a different type of magazine, and CartridgeLightRifle to another type of cartridge.

For melee weapons the process is a lot easier, doing what we've done above with the name and description but simply changing the below component:
```
  - type: MeleeWeapon
    attackRate: 1.5
    damage:
      types:
        Slash: 10
```
And either increasing the `attackRate` or the `Slash: 10` value to make our special weapon just that bit more useful.

You can also edit most of these variables during mapping using the view variables command if you don't want to add it to the games files or if it's not going to get much usage.
