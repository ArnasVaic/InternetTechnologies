# XPath queries

```xpath
/arpg:game/arpg:players/arpg:player[2]/arpg:items/ancestor::arpg:game
/arpg:game/arpg:players/arpg:player[2]/arpg:items/descendant::arpg:special
/arpg:game/arpg:players/arpg:player[2]/arpg:items/following-sibling::arpg:damage
/arpg:game/arpg:players/arpg:player[2]/arpg:items/preceding-sibling::birthday
/arpg:game/arpg:players/arpg:player[2]/arpg:items/following::arpg:special
/arpg:game/arpg:players/arpg:player[2]/arpg:items/preceding::arpg:damage
```

Get player which has at least half as much health points as the Ogre

```xpath
/arpg:game/arpg:players/arpg:player[2 * arpg:health > /arpg:game/arpg:enemies/arpg:enemy[@race="Ogre"]/arpg:health]
```

Count all tags that contain text (I don't like because it counts parents too)

```xpath
count(//*[text()])
```

Tries to sum all tags in the document

```xpath
sum(//*)
```


