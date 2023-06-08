# Roblox VR Documentation
### Quoniam

---------------------------------

# The Frameworks

## Playermodel
First and foremost, we need to setup our VR playermodel!
The playermodel is what the player controls and it's what holds all the actions!

Start off by creating a new game in Roblox Studio.
Now, go into the explorer on the right side of the screen.
Head down to *StarterPlayer*
Click the plus on the right of *StarterCharacterScripts*
Look for *LocalScript* and click on it
You will be taken to an empty script editor.

We need to define a couple variables:
The VR Camera
The Player
The VRService
The Character
The RunService
The UserInputService
etc.

Go ahead and insert this code below:
```
local camera = workspace.CurrentCamera
local uis = game:GetService("UserInputService")
local player = game:GetService("Players").LocalPlayer
local char = player.Character
local rs = game:GetService("RunService")
```
