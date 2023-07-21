<!-- DOCUMENTATION MARKDOWN OF BEDROCK-API (https://JustSkyDev/Bedrock-API -->

<!-- LOGO -->
<div align="center">

  <img src="https://socialify.git.ci/JustSkyDev/Bedrock-API/image?description=1&descriptionEditable=Minecraft%20Bedrock%20Custom%20Scripting%20API&font=Source%20Code%20Pro&forks=1&issues=1&logo=https%3A%2F%2Fraw.githubusercontent.com%2FJustSkyDev%2FBedrock-API%2Fmain%2Fpack_icon.png&name=1&owner=1&pattern=Circuit%20Board&pulls=1&stargazers=1&theme=Light" alt="Bedrock-API" />

  <h3 align="center"><u>Bedrock API Documentation</u></h3>

  <p align="center">
    Bedrock API is a library built using Minecraft Bedrock Scripting API. This library will help you keep your code clean and make it easier to interact with the Scripting API, while including a lot of new classes/functions/methods for you to use! and some built-in custom command
    <br />
    <br />
    <a href="https://github.com/JustSkyDev/Bedrock-API">Repository</a>
    ·
    <a href="https://github.com/JustSkyDev/Bedrock-API/issues">Bug Report</a>
    ·
    <a href="https://github.com/JustSkyDev/Bedrock-API/issues">Feature Request</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  
  <ul>
    <li> 
      <a href="#information"> Information </a>
    </li>
    <li> 
      <a href="#import-guide"> Import guide </a>
    </li>
  </ul>

  <p>
    <h2> 🛠️ Classes </h2>
  </p>
  <ul>
    <li>
      <h3> Custom commands </h3>
    </li>
    <li>
      <a href="#commandclass"> CommandClass </a>
    </li>
    <li>
      <a href="#commandregistration"> CommandRegistration </a>
    </li>
    <li>
      <h3> Cooldown (Pre-release)</h3>
    </li>
    <li>
      <a href="#cooldownclass"> CooldownClass </a>
    </li>
    <li>
      <h3> Data saves </h3>
    </li>
    <li>
      <a href="#collection"> Collection </a>
    </li>
    <li>
      <a href="#database"> Database </a>
    </li>
    <li>
      <h3> Events </h3>
    </li>
    <li>
      <a href="#afterevents"> AfterEvents </a>
    </li>
    <li>
      <a href="#beforeevents"> BeforeEvents </a>
    </li>
    <li>
      <a href="#systemevents"> SystemEvents </a>
    </li>
    <li>
      <h3> Entities </h3>
    </li>
    <li>
      <a href="#entityclass"> EntityClass </a>
    </li>
    <li>
      <a href="#playerclass"> PlayerClass </a>
    </li>
    <li>
      <h3> Form builder </h3>
    </li>
    <li>
      <a href="#formclass"> FormClass </a>
    </li>
    <li>
      <h3> Messages </h3>
    </li>
    <li>
      <a href="#chatclass"> ChatClass </a>
    </li>
    <li>
      <a href="#errorclass"> ErrorClass </a>
    </li>
    <li>
      <a href="#failedclass"> FailedClass </a>
    </li>
  </ul>
  
  <p> 
    <h2> ⚙️ Functions </h2>
  </p>
  <ul>
    <li>
      <a href="#form"> Form </a>
    </li>
    <li>
      <a href="#formatter"> Formatter </a>
    </li>
    <li>
      <a href="#ms"> MS </a>
    </li>
    <li>
      <a href="#timer"> Timer </a>
    </li>
    <li>
      <a href="#validation"> Validation </a>
    </li>
    <li>
      <a href="#world"> World </a>
    </li>
  </ul>
</details>

## Information
I have included all the modules here in the `@modules.js` file in the `plugins` folder or you can also call them directly from `modules.js` in the `@modules` folder.

`Default command Prefix is: "!"`

<br />

## Import guide
- from `@modules.js`

```javascript
/**
 * Replace className with the name of the module you want to add 
 */
import { className } from "./@modules";
```
- from `@modules/modules.js`

```javascript
/**
 * Replace className with the name of the module you want to add 
 */
import { className } from "./@modules/modules";
```

<br />

## 🛠️ Classes
### CommandClass
```javascript
/**
 * BuildCommand
 * registration is from CommandRegistration
 * callback is a function 
 * callback.inputs : Get input
 * callback.raw : Get raw packets from ChatSendEvent
 * callback.DB : Get used database (GlobalDB)
 * callback.allCommandRegistration : Get all command registration
 * callback.sender : Get sender player
 * callback.config : Get config from config.js
 */
Command.BuildCommand(registration, callback);

/**
 * getPrefix
 * Get current prefix
 */
Command.getPrefix();

/**
 * setPrefix()
 * Set command prefix, don't forget to run /reload after updating prefix
 * prefix : What prefix want you use (string)
 */
Command.setPrefix(prefix);
```

<br />

### CommandRegistration

```javascript
/**
 * Register command 
 * setName : Set command name - Required 
 * setDescription : Set command description - Optional
 * setCategory : Set command category - Optional
 * setPrivate : If true, only player with OP perm can access it - Optional 
 * setRequireTags : Only players with certain tags can access it - Optional
 * setAliases : Set command aliases - Optional
 * setUsage : How to use the command - Optional
 * setExample : Give example how to use the command - Optional
 * setInputs : Set command inputs, available types "string, boolean, number, playername" - Optional
 */
new CommandRegistration()
  .setName("commandName")
  .setDescription("Command description")
  .setCategory("Category")
  .setPrivate(false)
  .setRequireTags(["tags"])
  .setAliases(["command", "name"])
  .setUsage(["command usage"])
  .setExample(["command example"])
  .setInputs({
    0: ["playername"],
    1: ["boolean"],
  });
```

<br />

### CooldownClass

```javascript
/**
 * Create new cooldown 
 */
const cd = new CooldownClass();

/**
 * Start cooldown 
 * duration : Cooldown duration 
 */
cd.start(duration);

/**
 * Get cooldown status
 */
cd.isActive();

/**
 * Get cooldown remaining time
 */
cd.getCooldown();
```

<br />

### Collection

```javascript
/**
 * Map extension 
 */
const coll = new Collection();

/**
 * With "find" function
 */
coll.find(function () {});
```

<br />

### Database

```javascript
/**
 * Much the same as Map works, but it's scoreboard based
 * name : Database name
 */
const db = new Database(name);

/**
 * Set data to Database
 * key : Data key 
 * value : Data
 */
db.set(key, value);

/**
 * Push new data to database 
 * key : Data key 
 * value : Data
 */
db.push(key, value)

/**
 * Get data from Database
 * key : Data key
 */
db.get(key);

/**
 * Delete data
 * key : Data key
 */
db.delete(key);

/**
 * Reset Database 
 */
db.reset();

/**
 * Get values
 */
db.values();

/**
 * Get keys
 */
db.keys();

/**
 * Has key
 * key : Data key
 */
db.hasKey(key);

/**
 * Get entries 
 */
db.entries();
```

<br />

### AfterEvents
- ### Event list
- blockBreak
- blockExplode
- blockPlace
- buttonPush
- chat
- dataDrivenEntity
- effectAdd
- entityDie
- entityHealthChanged
- entityHitBlock
- entityHitEntity
- entityHurt
- entityRemoved
- entitySpawn
- explosion
- itemCompleteUse
- itemDefinition
- itemReleaseUse
- itemStartUse
- itemStartUseOn
- itemStopUse
- itemStopUseOn
- itemUse
- itemUseOn
- leverAction
- messageReceive
- pistonActivate
- playerJoin
- playerLeave
- playerSpawn
- pressurePlatePop
- pressurePlatePush
- projectileHit
- targetBlockHit
- tripWireTrip
- weatherChange
- worldInitialize

```javascript
/**
 * After events
 * event : Event name 
 * callback : Event callback
 */
AfterEvents.on(event, callback);
```

<br />

### BeforeEvents
- #### Event list
- chat
- dataDrivenEntity
- explosion
- itemDefinition
- itemUse
- itemUseOn
- pistonActivate

```javascript
/**
 * Before events 
 * event : Event name 
 * callback : Event callback
 */
BeforeEvents.on(event, callback);
```

<br />

### SystemEvents
- #### Event list
- watchdogTerminate
- scriptEventReceive

```javascript
/**
 * System events 
 * event : Event name 
 * callback : Event callback
 */
SystemEvents.on(event, callback);
```

<br />

### EntityClass
```javascript
/**
 * Entity class
 * entityObj: Entity object 
 */
const entity = new EntityClass(entityObj);

/**
 * Get tags
 */
entity.getTags();

/**
 * Has tag 
 * tag : Tag name
 */
entity.hasTag(tag);

/**
 * Get specific tag 
 * tag : Tag starts with 
 * example: if you have tag with name "tag: hello world", and set getTagStartsWith("tag:"), it will return "tag: hello world"
 */
entity.getTagStartsWith(tag);
```

<br />

### PlayerClass
- Include [EntityClass](#entityclass) methods

```javascript
/**
 * Player class 
 * playerObj : Player object
 */
const player = new PlayerClass(playerObj);

/**
 * Get scoreboard score 
 * objective : Scoreboard objective name
 */
player.getScore(objective);

/**
 * Get xo level
 */
player.getXpLevel();

/**
 * Check specific player is online or offline
 * pname : Player name
 */
player.isOnline(pname);

/**
 * Get how many inventory slots are still empty
 */
player.getEmptySlots();

/**
 * Gets items in the player right hand
 */
player.getRightItem();

/**
 * Get all items in inventory including air
 */
player.getItems();

/**
 * Get player object from player name
 * pname : Player name
 */
player.getPlayerObjectFromName(pname);

/**
 * Get needed xp to level up
 */
player.needXpToLevelUp();

/**
 * Get earned xp at current level
 */
player.xpEarned();

/**
 * Get inventory component  
 */
player.getInventoryComponent();

/**
 * Get raw component
 */
player.getRawPlayerComponent();

/**
 * Player query
 * Query list:
 * "isClimbing"
 * "isFalling"
 * "isFlying"
 * "isGliding"
 * "isInWater"
 * "isJumping"
 * "isOnGround"
 * "isSneaking"
 * "isSprinting"
 * "isSwimming"
 */
player.Query(query);
```

<br />

### FormClass
- [ServerUI Docs](https://learn.microsoft.com/en-us/minecraft/creator/scriptapi/minecraft/server-ui/minecraft-server-ui)

```javascript
/**
 * Form builder 
 * type : "action", "message", "modal"
 * setTitle : Form title, support all type
 * setBody : Form body, only support "action" and "message" type
 * addButton : Form button, only support "action" and "message" type
 * setButton1 : Form button1, only support "message" type
 * setButton2 : Form button2, only support "message" type
 * addDropdown : Form dropdown, only support "modal" type
 * addSlider : Form slider, only support "modal" type
 * addTextField : Form text field, only support "modal" type
 * addToggle : Form toggle, only support "modal" type
 * note: The way to use it is the same as "server-ui", the only difference is the name 
 */
const form = new FormClass(type)
  .setTitle(title)
  .setBody(body)
  .addButton(button)
  .setButton1(button1)
  .setButton2(button2)
  .addDropdown(dropdown)
  .addSlider(slider)
  .addTextField(textField)
  .addToggle(toggle);
  
 /**
  * Showing the form 
  * playerObj : Player object
  */
 form.sendForm(playerObj);
 
/**
 * Example 
 */
const ui = new FormClass("action")
  .setTitle("title")
  .setBody("body")
  .addButton("button", "icon/path")
  .sendForm(playerObj)
  .then(function (response) {});
```

<br />

### ChatClass

```javascript
/**
 * Chat class 
 */
const chat = new ChatClass();

/**
 * Broadcast 
 * text : Tellraw JSON
 * example: { text: "Hello World" }
 */
chat.broadcast(text);

/**
 * Broadcast to specific player 
 * text : Tellraw JSON
 * pname : Player name
 */
chat.broadcast(text, pname);

/**
 * Run single command 
 * cmd : Minecraft command but without "/"
 */
chat.runCommand(cmd);

/**
 * Run multiple commands
 * cmds : Minecraft command but without "/"
 * example usage : ["say i have apple", "give @a apple 16"]
 */
chat.runCommands(cmds);
```

<br />

### ErrorClass

```javascript
/**
 * Error class 
 */
const error = new ErrorClass();

/**
 * Custom error 
 * classname : Class name 
 * where : Location
 * stack : Error message
 */
error.CustomError(classname, where, stack);
```

<br />

### FailedClass

```javascript
/**
 * Failed class 
 */
const failed = new FailedClass();

/**
 * Invalid command 
 * playerObj : Player object 
 * cname : Command name 
 */
failed.InvalidCommand(playerObj, cname);
```

([Back to Top](#))

<br />

## ⚙️ Functions
### Form 
- `SendActiveForm(formId, player)`

```javascript
/**
 * Send active form
 * formId : Form class
 * playerObj : Player object
 */
const activeForm = Form.SendActiveForm(formId, playerObj);
```

<br />

### Formatter
- `rainbowText(text)`
- `metricNumbers(number)`
- `thousandsSeparator(text)`
- `EncryptText(text)`
- `DecryptText(text)`

```javascript
/**
 * Example 
 */
const raimbow = Formatter.rainbowText("hello world");
```

<br />

### MS
- `Format(number, { compactDuration, fullDuration, avoidDuration })`
- `toMiliseconds(number)`
- `toDuration(number, { compactDuration, fullDuration, avoidDuration })`

```javascript
/**
 * Example 
 */
const ms = MS.Format(1000);
```

<br />

### Timer 
- `setTickInterval(callback, tick)`
- `setTickTimeout(callback, tick)`
- `runInfinityLoop(callback)`
- `runNextTick(callback)`
- `sleep(tick)`
- `clearTick(timerId)`

```javascript
/**
 * Example 
 */
const interval = Timer.setTickInterval(() => {
  // Do something.
}, 20); // 20 means 1 seconds

/**
 * Clear tick 
 * timerId : Timer id
 */
Timer.clearTick(interval);
```

<br />

### Validation
- `isString(string)`
- `isNumber(number)`
- `isInteger(integer)`
- `isBoolean(boolean)`
- `isObject(object)`
- `isArray(array)`
- `isNull(null)`
- `isUndefined(undefined)`
- `isError(Error)`

```javascript
/**
 * Example 
 */
const array = ["hello", "world"];
const obj = { text: "Hello world" };
Validation.isArray(array); // return true
Validation.isArray(obj); // return false
```

<br />

### World
- `getOnlinePlayers()`

```javascript
/**
 * Example, online player counter
 */
World.getOnlinePlayers(); // return Player[] or Array<Player>

/**
 * Example, get online players name 
 */
const onlinePlayer = World.getOnlinePlayers().join(", "); // return "player 1", "player 2", "player 3"...
```

([Back to Top](#))