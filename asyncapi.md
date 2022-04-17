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
  * [SUB /socket.io](#sub-socketio-operation)

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

### SUB `/socket.io` Operation

*Receive game events for the current server*

Accepts **one of** the following messages:

#### Message `welcome`

*Welcome message sent on a succesful login*

A message sent after a succesful login, the welcome message contains information about the characters initial login coordinates, map and server


##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | tuple<string, object, ...optional<any>> | - | - | - | **additional items are allowed** |
| 0 (index) | string | The name of the event | const (`"welcome"`) | - | - |
| 1 (index) | object | - | - | - | **additional properties are allowed** |
| 1.gameplay | string | - | const (`"normal"`) | - | - |
| 1.info | object | - | - | - | **additional properties are allowed** |
| 1.map | string | A valid game map | allowed (`"main"`, `"winterland"`) | - | - |
| 1.name | string | A valid server identifier | allowed (`"I"`, `"II"`, `"III"`, `"pvp"`) | - | - |
| 1.pvp | boolean | - | - | - | - |
| 1.region | string | A valid server name | allowed (`"ASIA"`, `"US"`, `"EU"`) | - | - |
| 1.x | integer | - | - | - | - |
| 1.y | integer | - | - | - | - |

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
| (root) | tuple<string, object, ...optional<any>> | - | - | - | **additional items are allowed** |
| 0 (index) | string | The name of the event | const (`"entities"`) | - | - |
| 1 (index) | object | All surrounding entities | - | - | **additional properties are allowed** |
| 1.in | string | A valid game map | allowed (`"main"`, `"winterland"`) | - | - |
| 1.map | string | A valid game map | allowed (`"main"`, `"winterland"`) | - | - |
| 1.players | array<object> | - | - | - | - |
| 1.players.afk | string | Control method of the player | allowed (`"code"`, `"manual"`) | - | - |
| 1.players.age | integer | Age in days of player | - | - | - |
| 1.players.angle | number | Angle of the player | - | - | - |
| 1.players.armor | integer | The players armour score | - | - | - |
| 1.players.attack | integer | the players attack score | - | - | - |
| 1.players.c | object | An object containing abilities the player is channeling | - | - | **additional properties are allowed** |
| 1.players.cid | integer | - | - | - | - |
| 1.players.controller | string | - | - | - | - |
| 1.players.ctype | string | The players class type | allowed (`"mage"`, `"warrior"`, `"priest"`, `"rogue"`, `"paladin"`, `"archer"`, `"merchant"`) | - | - |
| 1.players.cx | object | An object containing the player applied customisations | - | - | **additional properties are allowed** |
| 1.players.focus | integer | The focus target ID of the player | - | - | - |
| 1.players.frequency | integer | The players frequency score | - | - | - |
| 1.players.hp | integer | The players current Health Points | - | - | - |
| 1.players.id | string | The players id (Doubles as the player name) | - | - | - |
| 1.players.level | integer | The players current level | - | - | - |
| 1.players.max_hp | integer | The players maximum Health Points | - | - | - |
| 1.players.max_mp | integer | The players maximum Mana Points | - | - | - |
| 1.players.mp | integer | The players current Mana Points | - | - | - |
| 1.players.owner | string | The owner ID of this player | - | - | - |
| 1.players.party | string | The player ID of the players party leader | - | - | - |
| 1.players.pdps | number | The players DPS share whilst in the players current party | - | - | - |
| 1.players.q | object | - | - | - | **additional properties are allowed** |
| 1.players.q.compound | object | - | - | - | **additional properties are allowed** |
| 1.players.q.compound.len | number | - | - | - | - |
| 1.players.q.compound.ms | number | - | - | - | - |
| 1.players.q.compound.num | number | - | - | - | - |
| 1.players.q.compound.nums | array<number> | - | - | - | - |
| 1.players.q.compound.nums (single item) | number | - | - | - | - |
| 1.players.q.upgrade | object | - | - | - | **additional properties are allowed** |
| 1.players.q.upgrade.len | number | - | - | - | - |
| 1.players.q.upgrade.ms | number | - | - | - | - |
| 1.players.q.upgrade.num | number | - | - | - | - |
| 1.players.q.exchange | object | - | - | - | **additional properties are allowed** |
| 1.players.q.exchange.len | number | - | - | - | - |
| 1.players.q.exchange.ms | number | - | - | - | - |
| 1.players.range | integer | The players attack range | - | - | - |
| 1.players.resistance | integer | The players resistance score | - | - | - |
| 1.players.rip | boolean | Denotes whether the character is currently dead | - | - | - |
| 1.players.s | object anyOf | An object containing the players applied effects | - | - | **additional properties are allowed** |
| 1.players.s.0 (anyOf item) | object | - | - | - | **additional properties are allowed** |
| 1.players.s.0.ms | number | The time in milliseconds remaining of the buff | - | - | - |
| 1.players.s.0.f | string | The player ID who applied the buff | - | - | - |
| 1.players.s.0.strong | boolean | Denotes whether this buff is `strong` meaning it cannot be replaced with an identical buff from another player | - | - | - |
| 1.players.skin | string | The ID of the skin applied to the player | - | - | - |
| 1.players.slots | object | All currently equipped items on the player | - | - | **additional properties are allowed** |
| 1.players.slots.itemName | object | A standard item object | - | - | **additional properties are allowed** |
| 1.players.slots.itemName.name | string | - | - | - | - |
| 1.players.slots.itemName.level | integer | - | - | - | - |
| 1.players.slots.itemName.stat_type | string | The current stat type applied to the item from a scroll | allowed (`"int"`, `"str"`, `"dex"`, `"vit"`) | - | - |
| 1.players.slots.itemName.acc | integer | The items achievement progress | - | - | - |
| 1.players.slots.itemName.ach | string | The items applied achievement name | - | - | - |
| 1.players.slots.itemName.expires | string | A timestamp that when reached, the item will be deleted | - | - | - |
| 1.players.slots.itemName.gf | string | The character that gifted the item to the player | - | - | - |
| 1.players.slots.itemName.grace | integer | An integer that denotes how likely a player is to success when attempting to upgrade or compound the item. A higher number means a higher change to succeed | - | - | - |
| 1.players.slots.itemName.l | string | Denotes whether the item is (l)ocked, (s)ealed or (u)nlocking | allowed (`"l"`, `"s"`, `"u"`) | - | - |
| 1.players.slots.itemName.ps | array<string> | An array of applicable titles for this item | - | - | - |
| 1.players.slots.itemName.ps (single item) | string | - | - | - | - |
| 1.players.speed | integer | The characters speed score | - | - | - |
| 1.players.target | string | The ID of the players current target | - | - | - |
| 1.players.x | number | The players x coordinate | - | - | - |
| 1.players.xp | integer | The players accumulated xp at the current level | - | - | - |
| 1.players.y | number | The players y coordinate | - | - | - |
| 1.monsters | array<object> | - | - | - | - |
| 1.monsters.abs | boolean | - | - | - | - |
| 1.monsters.angle | number | Angle of the monster | - | - | - |
| 1.monsters.armor | integer | The monsters armour score | - | - | - |
| 1.monsters.cid | integer | - | - | - | - |
| 1.monsters.going_x | number | The x coordinate on the monsters `map` the monster is currently moving to | - | - | - |
| 1.monsters.going_y | number | The y coordinate on the monsters `map` the monster is currently moving to | - | - | - |
| 1.type | string | - | allowed (`"all"`, `"xy"`) | - | - |

> Examples of payload _(generated)_

```json
[
  "entities",
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
]
```


#### Message `action`

*An action by a character in the rendered area*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | tuple<string, object, ...optional<any>> | - | - | - | **additional items are allowed** |
| 0 (index) | string | The name of the event | const (`"action"`) | - | - |
| 1 (index) | object | A standard action | - | - | **additional properties are allowed** |
| 1.attacker | string | The ID of the player performing the action | - | - | - |
| 1.damage | integer | The amount of damage the action has calculated | - | - | - |
| 1.eta | integer | - | - | - | - |
| 1.m | integer | - | - | - | - |
| 1.pid | string | The actions unique identifier | - | - | - |
| 1.projectile | string | The type of projectile for this action (if any) | - | - | - |
| 1.source | string | The origin or trigger of this action | - | - | - |
| 1.target | string | the target ID of this action | - | - | - |
| 1.type | string | The type of this action | - | - | - |
| 1.x | number | The origin X coordinate of this action | - | - | - |
| 1.y | number | The origin Y coordinate of this action | - | - | - |

> Examples of payload _(generated)_

```json
[
  "action",
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
]
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
| (root) | tuple<string, object, ...optional<any>> | - | - | - | **additional items are allowed** |
| 0 (index) | string | The name of the event | const (`"hit"`) | - | - |
| 1 (index) | object | A standard hit event | - | - | **additional properties are allowed** |
| 1.anim | string | The name of the animation | - | - | - |
| 1.damage | integer | The damage applied to the target `hid` | - | - | - |
| 1.hid | string | The ID of the entity effected by the hit | - | - | - |
| 1.kill | boolean | Denotes whether this hit killed the target `hid` | - | - | - |
| 1.lifesteal | integer | Life stolen by this hit | - | - | - |
| 1.pid | string | The unique identifier of this hit event | - | - | - |
| 1.projectile | string | The name of the projectile sprite to use for this hit | - | - | - |
| 1.source | string | The source that triggered this hit | - | - | - |

> Examples of payload _(generated)_

```json
[
  "hit",
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
]
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
| (root) | tuple<string, object, ...optional<any>> | - | - | - | **additional items are allowed** |
| 0 (index) | string | The name of the event | const (`"ping_ack"`) | - | - |
| 1 (index) | object | - | - | - | **additional properties are allowed** |
| 1.id | string | - | - | - | - |

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
| (root) | tuple<string, object, ...optional<any>> | - | - | - | **additional items are allowed** |
| 0 (index) | string | The name of the event | const (`"death"`) | - | - |
| 1 (index) | object | - | - | - | **additional properties are allowed** |
| 1.id | string | The ID of the entity that died | - | - | - |

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



