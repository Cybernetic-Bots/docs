---
title: Create Module
nav_order: 1
parent: Module
---

To start create a new folder for the module naming the folder what you want the module to be named.

Now create `module.ts` in the folder.

For this guide we will pretend the folder/module name is `example`

example/module.ts
```ts
// This is required
export default {
"description":"Module description",
"ownerID": "User-ID of the module owner (the user that requested you create the module)"
}

// This is an optional method of executing code when the module is loaded
export function onload(client: Discord.Client){}
```

# Onload Function
The bot client is passed to this function and it is executed when the module is loaded. 
The bot will be "ready" when this function is run. 
This function is run **ONE** time.
