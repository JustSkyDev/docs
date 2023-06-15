<!-- DOCUMENTATION MARKDOWN OF BEDROCK-API (https://JustSkyDev/Bedrock-API -->

<!-- LOGO -->
<div align="center">

  ![Bedrock-API](https://socialify.git.ci/JustSkyDev/Bedrock-API/image?description=1&descriptionEditable=Minecraft%20Bedrock%20Custom%20Scripting%20API&font=Source%20Code%20Pro&forks=1&issues=1&logo=https%3A%2F%2Fraw.githubusercontent.com%2FJustSkyDev%2FBedrock-API%2Fmain%2Fpack_icon.png&name=1&owner=1&pattern=Circuit%20Board&pulls=1&stargazers=1&theme=Light)

  <h3 align="center"><u>Bedrock API Documentation</u></h3>

  <p align="center">
    Bedrock API is a library built using Minecraft Bedrock Scripting API. This library will help you keep your code clean and make it easier to interact with the Scripting API, while including a lot of new classes/functions/methods for you to use! and some built-in custom command
    <br />
    <br />
    <a href="https://github.com/JustSkyDev/Bedrock-API">View</a>
    ·
    <a href="https://github.com/JustSkyDev/Bedrock-API/issues">Bug Report</a>
    ·
    <a href="https://github.com/JustSkyDev/Bedrock-API/issues">Feature Request</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  
  <p>
    <h2> 🛠️ Classes </h2>
  </p>
  <ul>
    <li>
      <h3> Custom commands </h3>
    </li>
    <li>
      <a href="#commandclass" style="text-decoration: none"> CommandClass </a>
    </li>
    <li>
      <a href="#commandregistration" style="text-decoration: none"> CommandRegistration </a>
    </li>
    <li>
      <h3> Cooldown (Pre-release)</h3>
    </li>
    <li>
      <a href="#cooldownclass" style="text-decoration: none"> CooldownClass </a>
    </li>
    <li>
      <h3> Data saves </h3>
    </li>
    <li>
      <a href="#collection" style="text-decoration: none"> Collection </a>
    </li>
    <li>
      <a href="#database" style="text-decoration: none"> Database </a>
    </li>
    <li>
      <h3> Events </h3>
    </li>
    <li>
      <a href="#afterevents" style="text-decoration: none"> AfterEvents </a>
    </li>
    <li>
      <a href="#beforeevents" style="text-decoration: none"> BeforeEvents </a>
    </li>
    <li>
      <a href="#systemevents" style="text-decoration: none"> SystemEvents </a>
    </li>
    <li>
      <h3> Entities </h3>
    </li>
    <li>
      <a href="#entityclass" style="text-decoration: none"> EntityClass </a>
    </li>
    <li>
      <a href="#playerclass" style="text-decoration: none"> PlayerClass </a>
    </li>
    <li>
      <h3> Form builder </h3>
    </li>
    <li>
      <a href="#formclass" style="text-decoration: none"> FormClass </a>
    </li>
    <li>
      <h3> Messages </h3>
    </li>
    <li>
      <a href="#chatclass" style="text-decoration: none"> ChatClass </a>
    </li>
    <li>
      <a href="#errorclass" style="text-decoration: none"> ErrorClass </a>
    </li>
    <li>
      <a href="#failedclass" style="text-decoration: none"> FailedClass </a>
    </li>
  </ul>
  
  <p> 
    <h2> ⚙️ Functions </h2>
  </p>
  <ul>
    <li>
      <a href="#form" style="text-decoration: none"> Form </a>
    </li>
    <li>
      <a href="#formatter" style="text-decoration: none"> Formatter </a>
    </li>
    <li>
      <a href="#ms" style="text-decoration: none"> MS </a>
    </li>
    <li>
      <a href="#timer" style="text-decoration: none"> Timer </a>
    </li>
    <li>
      <a href="#validation" style="text-decoration: none"> Validation </a>
    </li>
    <li>
      <a href="#world" style="text-decoration: none"> World </a>
    </li>
  </ul>
</details>

## Information
`Default command Prefix is: "!"`

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
### CooldownClass
```javascript
/**
 * Create new cooldown 
 * name : Set cooldown name
 */
const cd = new CooldownClass(name);

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

### Collection
```javascript
/**
 * Map extension 
 * name : Collection name 
 */
new Collection(name);
```

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
 * Get data from Database
 * key : Data key
 */
db.get(key);
```