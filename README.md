# Module-Runner Docs
Hi, and thank you for using my model. 
And yes you can criticise my code of how I made it.
Anyways, onto the docs

(These docs where rushed and prob suck, so dont blame me lol)

## How do I use it?
How to install the Module Runner is like doing 3 things
1. Install the Model on roblox
2. Move the "Loader" file in __ServerScriptSerivce__

![image](https://user-images.githubusercontent.com/96776358/154376281-7d21432e-c9ee-4fb0-aaee-4191241b9cd1.png)

3. Edit the Settings file and put in anyone's id inside there. __USERID__ *NOT* __USERNAME__
Simple like that, you are done.

(Additional Information)

There are a few modules inside of the Folder by defualt

![image](https://user-images.githubusercontent.com/96776358/154379796-da472707-d9f0-47d6-8fb2-6a747714577f.png)

To run a module, do .run [path of module] (Path of module is like [Module Name / Aliases Name] or [Module.Folder.Folder. ...]) [args] (To do different args, do this [arg1, arg2, arg3, ...] or to run long strings, do "whatever this is")

Now, you are wondering how are you going to add "Aliases". Its very simple, you just add a __String Value__ inside the module and name it to what ever to be the alias of the Module. You can add multiple Aliases to it by adding more __String Values__ Example of one:

![image](https://user-images.githubusercontent.com/96776358/154379990-e6d69c1f-7b78-4fe0-ae4e-d2f2a6fb761b.png)

Example of .run | .run debug.server.getplayerinfo Player1 

Or if you want to re-run the last module you did, do .runprev

If you like to change the prefix, go into the Settings file, change ["Prefix"] to whatever you want EX: / or ~

## How do I add modules for me to run?
A very easy thing to do.
Inside the folder Modules, you can create folders and add Modules.

__I WILL SAY THIS NOW, BUT DO NOT ADD SPACES TO THE FOLDER OR THE MODULES. THIS WILL NOT WORK IF YOU DID__

Create a Module, and inside the module the code will look like this.
```lua
local Run = {}

function Run:RunModule(args, client, clientFunc)
  return "Return whatever here."
end

return Run
```
### the Args could will look like:
```json
{
  "a"
  "b"
  "c"
  ...
  "y"
  "z"
}
```
**Or**
```json
{
  "Player1"
  "Hello World"
}
```
The Client is the player who sent the request to run the module.
And lastly the clientFunc is the RemoteFunction to run client stuff like printing on the client side.

## How to add client functions for the server to run
Go to the Client Folder, and edit the ClientFunctions.Main script

And add this peice of code inside of it
```lua
FunctionTable.FunctionName = function(arguments)
  -- Whatever
end
```
Should look like 
```lua
...

FunctionTable.FunctionName = function(arguments)
  -- Whatever
end

ModuleRunner.OnClientInvoke = function(Func, ...)
  FunctionTable[Func](...)
end
```
For the module to run this client function, you would add this inside of it
```lua
...
clientFunc:InvokeClient(client , "FunctionName" , arguments)
...
```
