# Loop Manager Example:
```lua
getgenv().LoopModule = loadstring(game:HttpGet("https://raw.githubusercontent.com/FlamesW/LoopManager/home/Module.luau"))();

LoopModule.WhileLoop(1,function()
    print("[Loop Manager]: Loop 1");
end,"Loop1Second")

task.wait(3);
LoopModule:Kill();
```

---------------------------------------------------------------------------------------------------------------------------------------------------------------

# How you would control it:
```lua
shared.Settings = {
    ["AimbotChecks"] = {
        WallCheck = (true), -- // Defaults to true~
    },
};

local LoopModule = loadstring(game:HttpGet("https://raw.githubusercontent.com/FlamesW/LoopManager/home/Module.luau"))();

-- // Obsidian Lib UI
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/deividcomsono/Obsidian/main/Library.lua"))();

local Window = Library:CreateWindow({
	Title = "Floops (Example)",
	Footer = "Internal Version e.127.exe | By @hikari_kuroi",
	Icon = 72133521375266,
	NotifySide = "Right",
	ShowCustomCursor = false,
})

local Tabs = {
    Main = Window:AddTab("Aimbot","sticker"),
}

local AimbotOptionsGroup = Tabs.Main:AddLeftGroupbox("Aimbot Options","file-code-2");

-- // Obsidian Lib Components.
LoopModule.WhileLoop(1,function()
    if shared.Settings.AimbotChecks.WallCheck then
        print("Wall Checking.");
    end
end,"AimbotWallCheckToggle")

AimbotOptionsGroup:AddToggle("AimbotWallCheckToggle",{
    Text = "Wall Check",
    Default = shared.Settings.AimbotChecks.WallCheck,
    Tooltip = "Will not target people behind a wall",
    Callback = function(Value)
        shared.Settings.AimbotChecks.WallCheck = Value;
    end
})
```

# Docs: 

- Set up
```lua
local LoopModule = loadstring(game:HttpGet("https://raw.githubusercontent.com/FlamesW/LoopManager/home/Module.luau"))();
```

```lua
-- // Optionals
-- LoopModule.Debug = true;
-- LoopModule.SafeCall = false;
```

- While Loop
```lua
LoopModule.WhileLoop(1,function()
    print("Hi:)");
end,"HiFLoop")
```

```lua
LoopModule.WhileLoop(2,function()
    print("Bye:(");
end,"ByeFLoop",true) -- // Will wait 2 seconds before the print starts.
```

--------------------

- Render Stepped/ HeartBeat /Stepped
```lua
LoopModule.RenderStep(function(dt)
    print("Render:", dt);
end,"RenderStepLoop")
```

```lua
LoopModule.HeartBeat(function(dt)
    print("Render:", dt);
end,"HeartBeatLoop")
```

```lua
LoopModule.Stepped(function(dt)
    print("Render:", dt);
end,"SteppedLoop")
```

- Bind Render (BindToRenderStep)
```lua
LoopModule.BindRender(function(dt)
    print("Render:", dt);
end,"PriorityRender",Enum.RenderPriority.Camera.Value)
```

----------------------------------
- Add Task (Connections)

```lua
LoopModule:AddTask(game.Players.LocalPlayer.CharacterAdded,function(v)
    warn(v.Name);
end,"RespawnCharacter")
```

# Misc:

- Get function
```lua
-- // nil, true, false
print(LoopModule:Get("Test"));
```

- Task Spesifics

```lua
-- // Stops and deletes spesific task.
LoopModule:StopTask("MyTask");
```

```lua
-- // Restarts spesific task.
LoopModule:RestartTask("MyTask");
```

- Stop Floops
```lua
-- // Stops the loop.
LoopModule:ForceStop("MyFLoop");
```

- Start Floops
```lua
LoopModule:ForceStart("MyFLoop");
```

## Behold, Za WAURODOOO!!

```lua
 -- // Stops everything
LoopModule.Toggle(true);

 -- // Time has begun to move again.
LoopModule.Toggle(false);
```
## Kills Everything (KYS)
```lua
LoopModule:Kill(); -- // Bye:)~ <3
```
