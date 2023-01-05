---
title: Create Command
nav_order: 1
parent: Commands
---

Please create a folder inside of your module named `commands`

For this guide we will pretend the folder/module name is `example`

Every command gets it's own folder. The folder name has to match the main command file name. 

For example if we had `example/commands/test` the main command file would be `example/commands/test/test.ts`

# Command Class
| Properties | Methods |
| ---------- | ------- |
| name | execute |
| description | autocomplete |
| enabled | button |
| ownerOnly | modal |
| type | selectMenu |
| --- | setName |
| --- | setDescription |
| --- | setEnabled | 
| --- | setOwnerOnly | 

## Properties

| Property | Description | Type |
| --- | --- | --- |
| name | The command name | string | 
| description | The command description | string |
| enabled | Is the command enabled | boolean |
| ownerOnly | Is the command module-owner only | boolean |
| type | The command type | CommandType |

## Methods
| Method | Description | Arguments | Returns |
| --- | --- | --- | --- |
| execute, autocomplete, button, modal, selectMenu | Set the function to run when a command is run, a button gets clicked, etc. for that command | data: Function | void |
| setName | Set the name of the command | name: string | void |
| setDescription | Set the description of the command | description: string | void |
| setEnabled | Set if the command is enabled or not | enabled: boolean | void |
| setOwnerOnly | Set if the command is module-owner only or not | ownerOnly: boolean | void |

## Command Constructor
Argument: `data: CommandConstructorArguments`

### CommandConstructorArguments
```ts
name?: string | null

description?: string | null

enabled?: boolean | null

ownerOnly?: boolean | null
```

## CommandType
CommandType is an enum with the following options
| Number | Name |
| --- | --- |
| 0 | SLASH |
| 1 | MESSAGE |

# Slash Command extends Command
| Properties | Methods |
| --- | --- |
| options | setOptions |

## Properties
| Property | Description | Type |
| --- | --- | --- |
| options | Discord slash command arguments | Discord.ApplicationCommandOption[] |

## Methods
| Method | Description | Arguments | Return |
| --- | --- | --- | --- |
| setOptions | Set the discord slash command arguments | options: Discord.ApplicationCommandOption[] | void |

## Slash Command Constructor
Argument: `data: SlashCommandConstructorArguments`

### SlashCommandConstructorArguments extends CommandConstructorArguments
```ts
options?: ApplicationCommandOption[]
```

# Creating a Slash Command

example/commands/test/test.ts
```ts
import { CommandInteraction, Message } from "discord.js";
import SlashCommand from "../../Types/Classes/SlashCommand.js";

function run(data: CommandInteraction) {
  data.reply("test");
}

let command = new SlashCommand({
  name: "test",
  description: "test slash command",
});

command.execute(run);

export default command;
```