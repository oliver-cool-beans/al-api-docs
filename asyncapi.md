# Adventure Land - The Code MMORPG 1.0 documentation

* Support: [Adventure Land](http://www.adventure.land/)

[Find more info here.](http://adventure.land/docs)

Unofficial Documentation for Adventure Land

You can quickly play with the API using [wscat](https://github.com/websockets/wscat) like this:
```bash
wscat -c "wss://eud1.adventure.land:8443/socket.io/?EIO=4&transport=websocket"
```


## Table of Contents

* [Servers](#servers)
  * [EU I](#eu-i-server)
  * [EU II](#eu-ii-server)
  * [EU PVP](#eu-pvp-server)
  * [US I](#us-i-server)
  * [US II](#us-ii-server)
  * [US III](#us-iii-server)
  * [US PVP](#us-pvp-server)
  * [ASIA PVP](#asia-pvp-server)
* [Operations](#operations)
  * [SUB /](#sub--operation)

## Servers

### `EU I` Server

* URL: `wss://eud1.adventure.land:2053`
* Protocol: `wss`



### `EU II` Server

* URL: `wss://eud1.adventure.land:2083`
* Protocol: `wss`



### `EU PVP` Server

* URL: `wss://eud1.adventure.land:2087`
* Protocol: `wss`



### `US I` Server

* URL: `wss://usd1.adventure.land:2053`
* Protocol: `wss`



### `US II` Server

* URL: `wss://usd1.adventure.land:2083`
* Protocol: `wss`



### `US III` Server

* URL: `wss://usd1.adventure.land:2096`
* Protocol: `wss`



### `US PVP` Server

* URL: `wss://usd1.adventure.land:2087`
* Protocol: `wss`



### `ASIA PVP` Server

* URL: `wss://eud1.adventure.land:8443`
* Protocol: `wss`



## Operations

### SUB `/` Operation

*Game events that can be subscribed to via `socket.on(eventName, (...args) => {})`
*

Accepts **one of** the following messages:

#### Message `welcome`

*Welcome message sent on a succesful login*

A message sent after a succesful login, the welcome message contains information about the characters initial login coordinates, map and server


##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| gameplay | string | - | const (`"normal"`) | - | - |
| info | object | - | - | - | **additional properties are allowed** |
| map | string | A valid game map | allowed (`"main"`, `"winterland"`) | - | - |
| name | string | A valid server identifier | allowed (`"I"`, `"II"`, `"III"`, `"pvp"`) | - | - |
| pvp | boolean | - | - | - | - |
| region | string | A valid server name | allowed (`"ASIA"`, `"US"`, `"EU"`) | - | - |
| x | integer | - | - | - | - |
| y | integer | - | - | - | - |

> Examples of payload

_welcome_

Example of a standard welcome message

```json
[
  "welcome",
  {
    "gameplay": "normal",
    "in": "winterland",
    "info": {},
    "map": "winterland",
    "name": "I",
    "pvp": false,
    "region": "ASIA",
    "x": 1235,
    "y": -737
  }
]
```


#### Message `entities`

*All entities in the current map within X distance*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | All surrounding entities | - | - | **additional properties are allowed** |
| in | string | A valid game map | allowed (`"main"`, `"winterland"`) | - | - |
| map | string | A valid game map | allowed (`"main"`, `"winterland"`) | - | - |
| players | array<object> | - | - | - | - |
| players.afk | string | Control method of the player | allowed (`"code"`, `"manual"`) | - | - |
| players.age | integer | Age in days of player | - | - | - |
| players.angle | number | Angle of the player | - | - | - |
| players.armor | integer | The players armour score | - | - | - |
| players.attack | integer | the players attack score | - | - | - |
| players.c | object | An object containing abilities the player is channeling | - | - | **additional properties are allowed** |
| players.cid | integer | - | - | - | - |
| players.controller | string | - | - | - | - |
| players.ctype | string | The players class type | allowed (`"mage"`, `"warrior"`, `"priest"`, `"rogue"`, `"paladin"`, `"archer"`, `"merchant"`) | - | - |
| players.cx | object | An object containing the player applied customisations | - | - | **additional properties are allowed** |
| players.focus | integer | The focus target ID of the player | - | - | - |
| players.frequency | integer | The players frequency score | - | - | - |
| players.hp | integer | The players current Health Points | - | - | - |
| players.id | string | The players id (Doubles as the player name) | - | - | - |
| players.level | integer | The players current level | - | - | - |
| players.max_hp | integer | The players maximum Health Points | - | - | - |
| players.max_mp | integer | The players maximum Mana Points | - | - | - |
| players.mp | integer | The players current Mana Points | - | - | - |
| players.owner | string | The owner ID of this player | - | - | - |
| players.party | string | The player ID of the players party leader | - | - | - |
| players.pdps | number | The players DPS share whilst in the players current party | - | - | - |
| players.q | object | - | - | - | **additional properties are allowed** |
| players.q.compound | object | - | - | - | **additional properties are allowed** |
| players.q.compound.len | number | - | - | - | - |
| players.q.compound.ms | number | - | - | - | - |
| players.q.compound.num | number | - | - | - | - |
| players.q.compound.nums | array<number> | - | - | - | - |
| players.q.compound.nums (single item) | number | - | - | - | - |
| players.q.upgrade | object | - | - | - | **additional properties are allowed** |
| players.q.upgrade.len | number | - | - | - | - |
| players.q.upgrade.ms | number | - | - | - | - |
| players.q.upgrade.num | number | - | - | - | - |
| players.q.exchange | object | - | - | - | **additional properties are allowed** |
| players.q.exchange.len | number | - | - | - | - |
| players.q.exchange.ms | number | - | - | - | - |
| players.range | integer | The players attack range | - | - | - |
| players.resistance | integer | The players resistance score | - | - | - |
| players.rip | boolean | Denotes whether the character is currently dead | - | - | - |
| players.s | object anyOf | An object containing the players applied effects | - | - | **additional properties are allowed** |
| players.s.0 (anyOf item) | object | - | - | - | **additional properties are allowed** |
| players.s.0.ms | number | The time in milliseconds remaining of the buff | - | - | - |
| players.s.0.f | string | The player ID who applied the buff | - | - | - |
| players.s.0.strong | boolean | Denotes whether this buff is `strong` meaning it cannot be replaced with an identical buff from another player | - | - | - |
| players.skin | string | The ID of the skin applied to the player | - | - | - |
| players.slots | object | All currently equipped items on the player | - | - | **additional properties are allowed** |
| players.slots.itemName | object | A standard item object | - | - | **additional properties are allowed** |
| players.slots.itemName.name | string | - | - | - | - |
| players.slots.itemName.level | integer | - | - | - | - |
| players.slots.itemName.stat_type | string | The current stat type applied to the item from a scroll | allowed (`"int"`, `"str"`, `"dex"`, `"vit"`) | - | - |
| players.slots.itemName.acc | integer | The items achievement progress | - | - | - |
| players.slots.itemName.ach | string | The items applied achievement name | - | - | - |
| players.slots.itemName.expires | string | A timestamp that when reached, the item will be deleted | - | - | - |
| players.slots.itemName.gf | string | The character that gifted the item to the player | - | - | - |
| players.slots.itemName.grace | integer | An integer that denotes how likely a player is to success when attempting to upgrade or compound the item. A higher number means a higher change to succeed | - | - | - |
| players.slots.itemName.l | string | Denotes whether the item is (l)ocked, (s)ealed or (u)nlocking | allowed (`"l"`, `"s"`, `"u"`) | - | - |
| players.slots.itemName.ps | array<string> | An array of applicable titles for this item | - | - | - |
| players.slots.itemName.ps (single item) | string | - | - | - | - |
| players.speed | integer | The characters speed score | - | - | - |
| players.target | string | The ID of the players current target | - | - | - |
| players.x | number | The players x coordinate | - | - | - |
| players.xp | integer | The players accumulated xp at the current level | - | - | - |
| players.y | number | The players y coordinate | - | - | - |
| monsters | array<object> | - | - | - | - |
| monsters.abs | boolean | - | - | - | - |
| monsters.angle | number | Angle of the monster | - | - | - |
| monsters.armor | integer | The monsters armour score | - | - | - |
| monsters.cid | integer | - | - | - | - |
| monsters.going_x | number | The x coordinate on the monsters `map` the monster is currently moving to | - | - | - |
| monsters.going_y | number | The y coordinate on the monsters `map` the monster is currently moving to | - | - | - |
| type | string | - | allowed (`"all"`, `"xy"`) | - | - |

> Examples of payload _(generated)_

```json
{
  "in": "main",
  "map": "main",
  "players": [
    {
      "afk": "code",
      "age": 0,
      "angle": 0,
      "armor": 0,
      "attack": 0,
      "c": {},
      "cid": 0,
      "controller": "string",
      "ctype": "mage",
      "cx": {},
      "focus": 0,
      "frequency": 0,
      "hp": 0,
      "id": "string",
      "level": 0,
      "max_hp": 0,
      "max_mp": 0,
      "mp": 0,
      "owner": "string",
      "party": "string",
      "pdps": 0,
      "q": {
        "compound": {
          "len": 0,
          "ms": 0,
          "num": 0,
          "nums": [
            0
          ]
        },
        "upgrade": {
          "len": 0,
          "ms": 0,
          "num": 0
        },
        "exchange": {
          "len": 0,
          "ms": 0
        }
      },
      "range": 0,
      "resistance": 0,
      "rip": true,
      "s": {
        "ms": 0,
        "f": "string",
        "strong": true
      },
      "skin": "string",
      "slots": {
        "itemName": {
          "name": "string",
          "level": 0,
          "stat_type": "int",
          "acc": 0,
          "ach": "string",
          "expires": "string",
          "gf": "string",
          "grace": 0,
          "l": "l",
          "ps": [
            "string"
          ]
        }
      },
      "speed": 0,
      "target": "string",
      "x": 0,
      "xp": 0,
      "y": 0
    }
  ],
  "monsters": [
    {
      "abs": true,
      "angle": 0,
      "armor": 0,
      "cid": 0,
      "going_x": 0,
      "going_y": 0
    }
  ],
  "type": "all"
}
```


#### Message `action`

*An action by a character in the rendered area*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | A standard action | - | - | **additional properties are allowed** |
| attacker | string | The ID of the player performing the action | - | - | - |
| damage | integer | The amount of damage the action has calculated | - | - | - |
| eta | integer | - | - | - | - |
| m | integer | - | - | - | - |
| pid | string | The actions unique identifier | - | - | - |
| projectile | string | The type of projectile for this action (if any) | - | - | - |
| source | string | The origin or trigger of this action | - | - | - |
| target | string | the target ID of this action | - | - | - |
| type | string | The type of this action | - | - | - |
| x | number | The origin X coordinate of this action | - | - | - |
| y | number | The origin Y coordinate of this action | - | - | - |

> Examples of payload _(generated)_

```json
{
  "attacker": "string",
  "damage": 0,
  "eta": 0,
  "m": 0,
  "pid": "string",
  "projectile": "string",
  "source": "string",
  "target": "string",
  "type": "string",
  "x": 0,
  "y": 0
}
```


##### Message tags

| Name | Description | Documentation |
|---|---|---|
| public | - | - |

#### Message `sid`

*A initial message sent when connecting to a server*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| pingInterval | integer | - | - | - | - |
| pingTimeout | integer | - | - | - | - |
| sid | string | - | - | - | - |
| upgrades | array<any> | - | - | - | - |

> Examples of payload _(generated)_

```json
{
  "pingInterval": 0,
  "pingTimeout": 0,
  "sid": "string",
  "upgrades": []
}
```


#### Message `hit`

*An event containing data when an entity is hit*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | A standard hit event | - | - | **additional properties are allowed** |
| anim | string | The name of the animation | - | - | - |
| damage | integer | The damage applied to the target `hid` | - | - | - |
| hid | string | The ID of the entity effected by the hit | - | - | - |
| kill | boolean | Denotes whether this hit killed the target `hid` | - | - | - |
| lifesteal | integer | Life stolen by this hit | - | - | - |
| pid | string | The unique identifier of this hit event | - | - | - |
| projectile | string | The name of the projectile sprite to use for this hit | - | - | - |
| source | string | The source that triggered this hit | - | - | - |

> Examples of payload _(generated)_

```json
{
  "anim": "string",
  "damage": 0,
  "hid": "string",
  "kill": true,
  "lifesteal": 0,
  "pid": "string",
  "projectile": "string",
  "source": "string"
}
```


##### Message tags

| Name | Description | Documentation |
|---|---|---|
| public | - | - |

#### Message `ping_ack`

*A ping acknowledgement from the server*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| id | string | - | - | - | - |

> Examples of payload

_ping_ack_

Example of a standard ping_ack

```json
[
  "ping_ack",
  {
    "id": "L3MpF"
  }
]
```


#### Message `death`

*A death event from the server generated from surrounding entities*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| id | string | The ID of the entity that died | - | - | - |

> Examples of payload

_death_

Example of a standard death event

```json
[
  "death",
  {
    "id": "7250984"
  }
]
```



