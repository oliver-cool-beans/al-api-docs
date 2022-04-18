# Adventure Land - The Code MMORPG 1.0 documentation

* Support: [Adventure Land](http://www.adventure.land/)

[Find more info here.](http://adventure.land/docs)

Unofficial Documentation for Adventure Land

Want to contribute? Check out the [Github](https://github.com/oliver-cool-beans/al-api-docs)

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
  * [PUB /](#pub--operation)
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

### PUB `/` Operation

*Game messages that can be emitted via `socket.emit(eventName, (...args) => {})`
*

Accepts **one of** the following messages:

#### Message `exchange_buy`

*Purchase an item using exchangeable items*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| num | integer | - | - | - | - |
| name | string | The name of the item being purchased | - | - | - |
| q | integer | The quantity being purchased | - | - | - |

> Examples of payload _(generated)_

```json
{
  "num": 0,
  "name": "string",
  "q": 0
}
```


#### Message `ping_trig`

*A ping that requests a `ping_ack` response from the server. Can be used to determine latency*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| id | string | A unique identifier used to identify the ping event. | - | - | - |

> Examples of payload _(generated)_

```json
{
  "id": "string"
}
```


#### Message `transport`

*Request a transport to another map*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| to | string | A valid game map | - | - | - |
| s | integer | - | - | - | - |

> Examples of payload _(generated)_

```json
{
  "to": "string",
  "s": 0
}
```


#### Message `property`

*Set a player property on the server*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| afk | boolean | - | - | - | - |

> Examples of payload _(generated)_

```json
{
  "afk": true
}
```


#### Message `move`

*Move the player to coordinates*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| x | number | The origin X coordinate of the move | - | - | - |
| y | number | The origin Y coordinate of the move | - | - | - |
| going_x | number | The destination X coordinate of the move | - | - | - |
| going_y | number | The destination Y coordinate of the move | - | - | - |
| m | integer | - | - | - | - |

> Examples of payload _(generated)_

```json
{
  "x": 0,
  "y": 0,
  "going_x": 0,
  "going_y": 0,
  "m": 0
}
```


#### Message `bank`

*Perform operations at the bank*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| operation | string | The operation being performed at the bank | allowed (`"swap"`) | - | - |
| inv | integer | The player inventory slot to swap | - | - | - |
| str | integer | The bank slot to swap | - | - | - |
| pack | string | A valid bank pack name | allowed (`"items0"`, `"items1"`, `"items2"`, `"items3"`) | - | - |

> Examples of payload _(generated)_

```json
{
  "operation": "swap",
  "inv": 0,
  "str": 0,
  "pack": "items0"
}
```


#### Message `buy`

*Purchase an item*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| name | string | A valid item name | - | - | - |
| quantity | integer | The quantity to purchase | - | - | - |

> Examples of payload _(generated)_

```json
{
  "name": "string",
  "quantity": 0
}
```


#### Message `target`

*Target an entity*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| id | string | A valid entity id | - | - | - |
| xid | string | The id of the player performing the target | - | - | - |

> Examples of payload _(generated)_

```json
{
  "id": "string",
  "xid": "string"
}
```


#### Message `lostandfound_info`

*Lost and found (goblin) operations. Provide no payload to request lostandfound items*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | string | - | allowed (`"info"`) | - | - |

> Examples of payload _(generated)_

```json
"info"
```


#### Message `sbuy`

*Second hand buy an item*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| rid | string | The unique identifier of teh item | - | - | - |
| f | boolean | - | - | - | - |

> Examples of payload _(generated)_

```json
{
  "rid": "string",
  "f": true
}
```


#### Message `loaded`

*An event sent when the client has finished loading*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| success | integer | - | allowed (`0`, `1`) | - | - |
| width | integer | The resolution width | - | - | - |
| height | integer | The resolution height | - | - | - |
| scale | integer | The game scale | - | - | - |

> Examples of payload _(generated)_

```json
{
  "success": 0,
  "width": 0,
  "height": 0,
  "scale": 0
}
```


#### Message `auth`

*An event sent to authenticate the game session*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| auth | string | The auth secret | - | - | - |
| character | string | The unique character game ID | - | - | - |
| code_slot | string | The unique code_slot game ID | - | - | - |

> Examples of payload _(generated)_

```json
{
  "auth": "string",
  "character": "string",
  "code_slot": "string"
}
```



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
| map | string | A valid game map | - | - | - |
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
| in | string | A valid game map | - | - | - |
| map | string | A valid game map | - | - | - |
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
  "in": "string",
  "map": "string",
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

*A ping acknowledgement from the server, triggered from `ping_trig`*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| id | string | A unique identifier for the ping specified in the `ping_trig` request | - | - | - |

> Examples of payload

_ping_ack_

Example of a standard ping_ack

```json
{
  "type": "object",
  "id": "L3MpF"
}
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
{
  "type": "object",
  "id": "7250984"
}
```


#### Message `server_info`

*Information about available events on the server*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object oneOf | - | - | - | **additional properties are allowed** |
| 0 (oneOf item) | - | Information about all available events on the server | - | - | **additional properties are allowed** |
| hp | integer | The event boss's current HP | - | - | - |
| live | boolean | Denotes whether the event is live | - | - | - |
| map | string | A valid game map | - | - | - |
| max_hp | integer | The event boss's maximum hp | - | - | - |
| x | number | The event boss's X coordinate location on the map | - | - | - |
| y | number | The event boss's Y coordinate location on the map | - | - | - |
| spawn | string | The server time of the next event start time | - | - | - |
| 1 (oneOf item) | object | Key value pairs used for server wide events | - | - | **additional properties are allowed** |
| 1.^S_ (pattern property) | boolean | - | - | - | - |

> Examples of payload _(generated)_

```json
{
  "hp": 0,
  "live": true,
  "map": "string",
  "max_hp": 0,
  "x": 0,
  "y": 0,
  "spawn": "string"
}
```


#### Message `disappear`

*A character has disappeared from the map*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | A character has disappeared | - | - | **additional properties are allowed** |
| id | string | The id of the character that has disappeared | - | - | - |
| reason | string | - | allowed (`"transport"`) | - | - |
| s | integer | Count of applied effects to the transport | - | - | - |
| to | string | A valid game map | - | - | - |
| effect | string | - | allowed (`"blink"`) | - | - |

> Examples of payload _(generated)_

```json
{
  "id": "string",
  "reason": "transport",
  "s": 0,
  "to": "string",
  "effect": "blink"
}
```


#### Message `disappearing_text`

*An event that is sent when disappearing text appears above a character*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| args | object | - | - | - | **additional properties are allowed** |
| args.c | string | The HEX color value of the text | - | - | - |
| args.s | string | The disappearing text effect | - | - | - |
| id | string | The character the disappearing text is applied to | - | - | - |
| message | string | The disappearing text value | - | - | - |
| x | number | The X coordinate the text appears at | - | - | - |
| y | number | The Y coordinate the text appears at | - | - | - |

> Examples of payload _(generated)_

```json
{
  "args": {
    "c": "string",
    "s": "string"
  },
  "id": "string",
  "message": "string",
  "x": 0,
  "y": 0
}
```


#### Message `new_map`

*A new map has beeen loaded*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | A new map has been loaded | - | - | **additional properties are allowed** |
| direction | integer | - | - | - | - |
| effect | integer | - | - | - | - |
| entities | object | All surrounding entities | - | - | **additional properties are allowed** |
| entities.in | string | A valid game map | - | - | - |
| entities.map | string | A valid game map | - | - | - |
| entities.players | array<object> | - | - | - | - |
| entities.players.afk | string | Control method of the player | allowed (`"code"`, `"manual"`) | - | - |
| entities.players.age | integer | Age in days of player | - | - | - |
| entities.players.angle | number | Angle of the player | - | - | - |
| entities.players.armor | integer | The players armour score | - | - | - |
| entities.players.attack | integer | the players attack score | - | - | - |
| entities.players.c | object | An object containing abilities the player is channeling | - | - | **additional properties are allowed** |
| entities.players.cid | integer | - | - | - | - |
| entities.players.controller | string | - | - | - | - |
| entities.players.ctype | string | The players class type | allowed (`"mage"`, `"warrior"`, `"priest"`, `"rogue"`, `"paladin"`, `"archer"`, `"merchant"`) | - | - |
| entities.players.cx | object | An object containing the player applied customisations | - | - | **additional properties are allowed** |
| entities.players.focus | integer | The focus target ID of the player | - | - | - |
| entities.players.frequency | integer | The players frequency score | - | - | - |
| entities.players.hp | integer | The players current Health Points | - | - | - |
| entities.players.id | string | The players id (Doubles as the player name) | - | - | - |
| entities.players.level | integer | The players current level | - | - | - |
| entities.players.max_hp | integer | The players maximum Health Points | - | - | - |
| entities.players.max_mp | integer | The players maximum Mana Points | - | - | - |
| entities.players.mp | integer | The players current Mana Points | - | - | - |
| entities.players.owner | string | The owner ID of this player | - | - | - |
| entities.players.party | string | The player ID of the players party leader | - | - | - |
| entities.players.pdps | number | The players DPS share whilst in the players current party | - | - | - |
| entities.players.q | object | - | - | - | **additional properties are allowed** |
| entities.players.q.compound | object | - | - | - | **additional properties are allowed** |
| entities.players.q.compound.len | number | - | - | - | - |
| entities.players.q.compound.ms | number | - | - | - | - |
| entities.players.q.compound.num | number | - | - | - | - |
| entities.players.q.compound.nums | array<number> | - | - | - | - |
| entities.players.q.compound.nums (single item) | number | - | - | - | - |
| entities.players.q.upgrade | object | - | - | - | **additional properties are allowed** |
| entities.players.q.upgrade.len | number | - | - | - | - |
| entities.players.q.upgrade.ms | number | - | - | - | - |
| entities.players.q.upgrade.num | number | - | - | - | - |
| entities.players.q.exchange | object | - | - | - | **additional properties are allowed** |
| entities.players.q.exchange.len | number | - | - | - | - |
| entities.players.q.exchange.ms | number | - | - | - | - |
| entities.players.range | integer | The players attack range | - | - | - |
| entities.players.resistance | integer | The players resistance score | - | - | - |
| entities.players.rip | boolean | Denotes whether the character is currently dead | - | - | - |
| entities.players.s | object anyOf | An object containing the players applied effects | - | - | **additional properties are allowed** |
| entities.players.s.0 (anyOf item) | object | - | - | - | **additional properties are allowed** |
| entities.players.s.0.ms | number | The time in milliseconds remaining of the buff | - | - | - |
| entities.players.s.0.f | string | The player ID who applied the buff | - | - | - |
| entities.players.s.0.strong | boolean | Denotes whether this buff is `strong` meaning it cannot be replaced with an identical buff from another player | - | - | - |
| entities.players.skin | string | The ID of the skin applied to the player | - | - | - |
| entities.players.slots | object | All currently equipped items on the player | - | - | **additional properties are allowed** |
| entities.players.slots.itemName | object | A standard item object | - | - | **additional properties are allowed** |
| entities.players.slots.itemName.name | string | - | - | - | - |
| entities.players.slots.itemName.level | integer | - | - | - | - |
| entities.players.slots.itemName.stat_type | string | The current stat type applied to the item from a scroll | allowed (`"int"`, `"str"`, `"dex"`, `"vit"`) | - | - |
| entities.players.slots.itemName.acc | integer | The items achievement progress | - | - | - |
| entities.players.slots.itemName.ach | string | The items applied achievement name | - | - | - |
| entities.players.slots.itemName.expires | string | A timestamp that when reached, the item will be deleted | - | - | - |
| entities.players.slots.itemName.gf | string | The character that gifted the item to the player | - | - | - |
| entities.players.slots.itemName.grace | integer | An integer that denotes how likely a player is to success when attempting to upgrade or compound the item. A higher number means a higher change to succeed | - | - | - |
| entities.players.slots.itemName.l | string | Denotes whether the item is (l)ocked, (s)ealed or (u)nlocking | allowed (`"l"`, `"s"`, `"u"`) | - | - |
| entities.players.slots.itemName.ps | array<string> | An array of applicable titles for this item | - | - | - |
| entities.players.slots.itemName.ps (single item) | string | - | - | - | - |
| entities.players.speed | integer | The characters speed score | - | - | - |
| entities.players.target | string | The ID of the players current target | - | - | - |
| entities.players.x | number | The players x coordinate | - | - | - |
| entities.players.xp | integer | The players accumulated xp at the current level | - | - | - |
| entities.players.y | number | The players y coordinate | - | - | - |
| entities.monsters | array<object> | - | - | - | - |
| entities.monsters.abs | boolean | - | - | - | - |
| entities.monsters.angle | number | Angle of the monster | - | - | - |
| entities.monsters.armor | integer | The monsters armour score | - | - | - |
| entities.monsters.cid | integer | - | - | - | - |
| entities.monsters.going_x | number | The x coordinate on the monsters `map` the monster is currently moving to | - | - | - |
| entities.monsters.going_y | number | The y coordinate on the monsters `map` the monster is currently moving to | - | - | - |
| entities.type | string | - | allowed (`"all"`, `"xy"`) | - | - |
| eval | string | - | - | - | - |
| in | string | A valid game map | - | - | - |
| info | object | - | - | - | **additional properties are allowed** |
| name | string | The new map name | - | - | - |
| m | integer | - | - | - | - |
| x | integer | The new X coordinate of the character | - | - | - |
| y | integer | The new Y coordinate of the character | - | - | - |

> Examples of payload _(generated)_

```json
{
  "direction": 0,
  "effect": 0,
  "entities": {
    "in": "string",
    "map": "string",
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
  },
  "eval": "string",
  "in": "string",
  "info": {},
  "name": "string",
  "m": 0,
  "x": 0,
  "y": 0
}
```


#### Message `start`

*An inital message upon character login containing player data*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | A standard player object | - | - | **additional properties are allowed** |
| afk | string | Control method of the player | allowed (`"code"`, `"manual"`) | - | - |
| age | integer | Age in days of player | - | - | - |
| angle | number | Angle of the player | - | - | - |
| armor | integer | The players armour score | - | - | - |
| attack | integer | the players attack score | - | - | - |
| c | object | An object containing abilities the player is channeling | - | - | **additional properties are allowed** |
| cid | integer | - | - | - | - |
| controller | string | - | - | - | - |
| ctype | string | The players class type | allowed (`"mage"`, `"warrior"`, `"priest"`, `"rogue"`, `"paladin"`, `"archer"`, `"merchant"`) | - | - |
| cx | object | An object containing the player applied customisations | - | - | **additional properties are allowed** |
| focus | integer | The focus target ID of the player | - | - | - |
| frequency | integer | The players frequency score | - | - | - |
| hp | integer | The players current Health Points | - | - | - |
| id | string | The players id (Doubles as the player name) | - | - | - |
| level | integer | The players current level | - | - | - |
| max_hp | integer | The players maximum Health Points | - | - | - |
| max_mp | integer | The players maximum Mana Points | - | - | - |
| mp | integer | The players current Mana Points | - | - | - |
| owner | string | The owner ID of this player | - | - | - |
| party | string | The player ID of the players party leader | - | - | - |
| pdps | number | The players DPS share whilst in the players current party | - | - | - |
| q | object | - | - | - | **additional properties are allowed** |
| q.compound | object | - | - | - | **additional properties are allowed** |
| q.compound.len | number | - | - | - | - |
| q.compound.ms | number | - | - | - | - |
| q.compound.num | number | - | - | - | - |
| q.compound.nums | array<number> | - | - | - | - |
| q.compound.nums (single item) | number | - | - | - | - |
| q.upgrade | object | - | - | - | **additional properties are allowed** |
| q.upgrade.len | number | - | - | - | - |
| q.upgrade.ms | number | - | - | - | - |
| q.upgrade.num | number | - | - | - | - |
| q.exchange | object | - | - | - | **additional properties are allowed** |
| q.exchange.len | number | - | - | - | - |
| q.exchange.ms | number | - | - | - | - |
| range | integer | The players attack range | - | - | - |
| resistance | integer | The players resistance score | - | - | - |
| rip | boolean | Denotes whether the character is currently dead | - | - | - |
| s | object anyOf | An object containing the players applied effects | - | - | **additional properties are allowed** |
| s.0 (anyOf item) | object | - | - | - | **additional properties are allowed** |
| s.0.ms | number | The time in milliseconds remaining of the buff | - | - | - |
| s.0.f | string | The player ID who applied the buff | - | - | - |
| s.0.strong | boolean | Denotes whether this buff is `strong` meaning it cannot be replaced with an identical buff from another player | - | - | - |
| skin | string | The ID of the skin applied to the player | - | - | - |
| slots | object | All currently equipped items on the player | - | - | **additional properties are allowed** |
| slots.itemName | object | A standard item object | - | - | **additional properties are allowed** |
| slots.itemName.name | string | - | - | - | - |
| slots.itemName.level | integer | - | - | - | - |
| slots.itemName.stat_type | string | The current stat type applied to the item from a scroll | allowed (`"int"`, `"str"`, `"dex"`, `"vit"`) | - | - |
| slots.itemName.acc | integer | The items achievement progress | - | - | - |
| slots.itemName.ach | string | The items applied achievement name | - | - | - |
| slots.itemName.expires | string | A timestamp that when reached, the item will be deleted | - | - | - |
| slots.itemName.gf | string | The character that gifted the item to the player | - | - | - |
| slots.itemName.grace | integer | An integer that denotes how likely a player is to success when attempting to upgrade or compound the item. A higher number means a higher change to succeed | - | - | - |
| slots.itemName.l | string | Denotes whether the item is (l)ocked, (s)ealed or (u)nlocking | allowed (`"l"`, `"s"`, `"u"`) | - | - |
| slots.itemName.ps | array<string> | An array of applicable titles for this item | - | - | - |
| slots.itemName.ps (single item) | string | - | - | - | - |
| speed | integer | The characters speed score | - | - | - |
| target | string | The ID of the players current target | - | - | - |
| x | number | The players x coordinate | - | - | - |
| xp | integer | The players accumulated xp at the current level | - | - | - |
| y | number | The players y coordinate | - | - | - |

> Examples of payload _(generated)_

```json
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
```


#### Message `upgrade`

*Upgrade result message*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | object | - | - | - | **additional properties are allowed** |
| type | string | - | allowed (`"upgrade"`, `"exchange"`) | - | - |
| success | integer | - | allowed (`0`, `1`) | - | - |

> Examples of payload _(generated)_

```json
{
  "type": "upgrade",
  "success": 0
}
```


#### Message `ui`

*UI text*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | oneOf | - | - | - | **additional properties are allowed** |
| 0 (oneOf item) | object | Sent when something is purchased or sold to a vendor | - | - | **additional properties are allowed** |
| type | string | - | const (`"+$"`) | - | - |
| id | string | The ID of the player or entity triggering the UI text | - | - | - |
| name | string | The id of the player that triggered the UI Text | - | - | - |
| item | object | - | - | - | **additional properties are allowed** |
| item.name | string | The item name | - | - | - |
| item.q | integer | The quantity of the item | - | - | - |
| 1 (oneOf item) | object | Sent when a player is mlucked | - | - | **additional properties are allowed** |
| 1.from | string | The player ID of the player casting mluck | - | - | - |
| 1.to | string | The payer ID of the player targeted by the mluck cast | - | - | - |
| 2 (oneOf item) | object | Sent when gold is sent to a player | - | - | **additional properties are allowed** |
| 2.type | string | - | const (`"gold_sent"`) | - | - |
| 2.receiver | string | The player ID of the player receiving the gold | - | - | - |
| 2.sender | string | The player ID of the player sending the gold | - | - | - |
| 2.gold | string | The amount of gold transferred | - | - | - |

> Examples of payload _(generated)_

```json
{
  "type": "+$",
  "id": "string",
  "name": "string",
  "item": {
    "name": "string",
    "q": 0
  }
}
```


#### Message `lostandfound`

*An event containing lostandfound items after being requested*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | array<object> | - | - | - | - |
| rid | string | The unique identifier of the item | - | - | - |
| name | string | The item name | - | - | - |
| level | integer | The items level | - | - | - |

> Examples of payload _(generated)_

```json
[
  {
    "rid": "string",
    "name": "string",
    "level": 0
  }
]
```


#### Message `game_response`

*Responses to actions performed within the game*

##### Payload

| Name | Type | Description | Value | Constraints | Notes |
|---|---|---|---|---|---|
| (root) | oneOf | - | - | - | **additional properties are allowed** |
| 0 (oneOf item) | string | A resonse returned when lostandfound is requested, but the required donation has not been provided | const (`"lostandfound_donate"`) | - | - |
| 1 (oneOf item) | object | A response returned when lostandfound info is requested | - | - | **additional properties are allowed** |
| 1.response | string | - | const (`"lostandfound_info"`) | - | - |
| 1.gold | number | The amount of gold lostandfound has | - | - | - |

> Examples of payload _(generated)_

```json
"lostandfound_donate"
```



