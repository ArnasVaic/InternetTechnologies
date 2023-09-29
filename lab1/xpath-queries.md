# XPath queries

`/arpg:game/arpg:players/arpg:player[2]/arpg:items/ancestor::arpg:game`
`/arpg:game/arpg:players/arpg:player[2]/arpg:items/descendant::arpg:special`
`/arpg:game/arpg:players/arpg:player[2]/arpg:items/following-sibling::arpg:damage`
`/arpg:game/arpg:players/arpg:player[2]/arpg:items/preceding-sibling::birthday`
`/arpg:game/arpg:players/arpg:player[2]/arpg:items/following::arpg:special`
`/arpg:game/arpg:players/arpg:player[2]/arpg:items/preceding::arpg:damage`

Get player which has at least half as much health points as the Ogre

`/arpg:game/arpg:players/arpg:player[2 * arpg:health > /arpg:game/arpg:enemies/arpg:enemy[@race="Ogre"]/arpg:health]`

Count all tags that contain text (I don't like because it counts transitively)

`count(//*[text()])`

Tries to sum all tags in the document

`sum(//*)`

`/descendant::arpg:item/arpg:special[./arpg:chance > 0.2]/ancestor::arpg:player`

`/descendant::arpg:item` returns:

```xml
<arpg:item type="usable" amount="1">
    <name>Magic wand</name>
    <arpg:special>
        <name>Super mega magic blast</name>
        <arpg:chance>0.3</arpg:chance>
    </arpg:special>
</arpg:item>
<arpg:item type="consumable" amount="3">
    <name>health potion</name>
</arpg:item>
<arpg:item type="usable" amount="1">
    <name>Excalibur</name>
    <arpg:special>
        <name>Stronger than usual swing</name>
        <arpg:chance>0.4</arpg:chance>
    </arpg:special>
</arpg:item>
<arpg:item type="equipable" amount="1">
    <name>Chainmail</name>
</arpg:item>
<arpg:item type="usable" amount="1">
    <name>Lava bow</name>
    <arpg:special>
        <name>Volcano shot</name>
        <arpg:chance>0.2</arpg:chance>
    </arpg:special>
</arpg:item>
<arpg:item type="consumable" amount="64">
    <name>Arrow</name>
</arpg:item>
```

`/descendant::arpg:item/arpg:special[./arpg:chance > 0.2]` returns:

```xml
<arpg:item type="usable" amount="1">
    <name>Excalibur</name>
    <arpg:special>
        <name>Stronger than usual swing</name>
        <arpg:chance>0.4</arpg:chance>
    </arpg:special>
</arpg:item>
<arpg:item type="usable" amount="1">
    <name>Magic wand</name>
    <arpg:special>
        <name>Super mega magic blast</name>
        <arpg:chance>0.3</arpg:chance>
    </arpg:special>
</arpg:item>
```

`/descendant::arpg:item/arpg:special[./arpg:chance > 0.2]/ancestor::arpg:player` returns:

```xml
<arpg:player name="Mangirdas" class="Knight">
    <birthday>2002-07-10</birthday>
    <arpg:items>
        <arpg:item type="usable" amount="1">
            <name>Excalibur</name>
            <arpg:special>
                <name>Stronger than usual swing</name>
                <arpg:chance>0.4</arpg:chance>
            </arpg:special>
        </arpg:item>
        <arpg:item type="equipable" amount="1">
            <name>Chainmail</name>
        </arpg:item>
    </arpg:items>
    <arpg:health>250</arpg:health>
    <arpg:damage>30</arpg:damage>
</arpg:player>
<arpg:player name="Birutė" class="Mage">
    <birthday>2003-06-03</birthday>
    <arpg:items>
        <arpg:item type="usable" amount="1">
            <name>Magic wand</name>
            <arpg:special>
                <name>Super mega magic blast</name>
                <arpg:chance>0.3</arpg:chance>
            </arpg:special>
        </arpg:item>
        <arpg:item type="consumable" amount="3">
            <name>health potion</name>
        </arpg:item>
    </arpg:items>
    <arpg:health>100</arpg:health>
    <arpg:damage>50</arpg:damage>
</arpg:player>
```

