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
local starterGui = game:GetService("StarterGui")
```

Now, we need to define the camera, and add our hands; These will be the biggest part of the game!
We'll simply create two small parts and use the UserInputService to detect hand movement!

Let's define the camera:
```
character:FindFirstChild("HumanoidRootPart").Anchored = true
workspace.CurrentCamera.CFrame = CFrame.new(workspace.CurrentCamera.CFrame.Position)

camera.CameraType = "Scriptable"
camera.HeadScale = 1

starterGui:SetCore("VRLaserPointerMode", 0)
starterGui:SetCore("VREnableControllerModels", false)
```

Now, lets add the hands:
```
	local rhand = Instance.new("Part")
	rhand.Parent = character
	rhand.CFrame = CFrame.new(0,0,0)
	rhand.Size = Vector3.new(1, 1, 1)
	rhand.Transparency = 0
	rhand.CanCollide = false
	rhand.Anchored = true
	rhand.Name = "RightHand"
  
  local lhand = Instance.new("Part")
	lhand.Parent = character
	lhand.CFrame = CFrame.new(0,0,0)
	lhand.Size = Vector3.new(1, 1, 1)
	lhand.Transparency = 0
	lhand.CanCollide = false
	lhand.Anchored = true
	lhand.Name = "LeftHand"
```

We need to make the hands move with the UserInputService, we can use UserInputService.UserCFrameChanged:
```
uis.UserCFrameChanged:Connect(function(part, move)
		if part == Enum.UserCFrame.LeftHand then
		lhand.CFrame = camera.CFrame*move
		elseif part == Enum.UserCFrame.RightHand then
		rhand.CFrame = camera.CFrame*move
		end
end)
```
