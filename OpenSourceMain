if not game:IsLoaded() then
    game:IsLoaded():Wait()
end

local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "Cheeto Hub Premium | Hoopz"})


-- Variables
local plr = game.Players.LocalPlayer
local char = plr.Character


local cam = workspace.CurrentCamera
local uis = game:GetService("UserInputService")




local Main = Window:MakeTab({
	Name = "Main",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})
local Misc = Window:MakeTab({
	Name = "Misc",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

function closestHoop()
    local dist,hoop = math.huge
    
    for i,v in pairs(game:GetService("Workspace").Courts:GetChildren()) do
        if v:IsA('Model') and v:FindFirstChild('Basketball Hoop') then

                local rim =  v["Basketball Hoop"].rim
                     _G.magnitude = (char.HumanoidRootPart.Position - rim.Position).Magnitude
                    if _G.magnitude < dist then
                        dist = _G.magnitude
                        hoop = v["Basketball Hoop"].rim
            end
        end
    end
    return hoop
end


Main:AddToggle({Name = "Aimbot",Callback = function(value)
      _G.toggle = value


    uis.InputBegan:Connect(function(key,gp)
        if gp then return end;
    
    if key.UserInputType == Enum.UserInputType.MouseButton1 then
            local  magnitude = (char.HumanoidRootPart.Position - closestHoop().Position).Magnitude / (game.Players.LocalPlayer.Power.Value / 22)
            if _G.toggle and game.Players.LocalPlayer.Character then
                 local plusvector = closestHoop().Position.X / Vector3.new(-100,0,0)
                 cam.CFrame = CFrame.new(cam.CFrame.Position, closestHoop().Position + (Vector3.new(0,magnitude,0)))
            end
        end
    end)
end})

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Blissful4992/ESPs/main/3D%20Drawing%20Api.lua"))()

   local Square = Library:New3DSquare()

    
Main:AddToggle({Name = "Aim Assist",Callback = function(value)
    assist = value
    Square.Visible = assist
    Square.ZIndex = 1
    Square.Transparency = 0.5
    Square.Color = Color3.fromRGB(0, 0, 255)
    Square.Thickness = 1
    Square.Filled = false
    Square.Position = Vector3.new(0, 0, 0)
    Square.Size = Vector2.new(5,5)
    
end})
spawn(function()
while true do wait(0.05)
        if assist and closestHoop() then
            if  (char.HumanoidRootPart.Position - closestHoop().Position).Magnitude <= 98 then
            Square.Visible = true
            local  magnitude = (char.HumanoidRootPart.Position - closestHoop().Position).Magnitude / (game.Players.LocalPlayer.Power.Value / 22)
            
            Square.Position = closestHoop().Position + (Vector3.new(0,magnitude,0))
            else
                Square.Visible = false
            end
        end
    end
end)

Main:AddToggle({Name = "Power Assist",Callback = function(value)
    powerassist = value
end})

local assistlabel = Main:AddLabel("Recommended Power:")

spawn(function()
    while true do wait()
       if powerassist and closestHoop() then
            local  magnitude = (char.HumanoidRootPart.Position - closestHoop().Position).Magnitude * 1.5
            if magnitude < 100 then
                local function round(to_round)
                    local divided = to_round / 5
                    local rounded = 5 * math.floor(divided)
                    return rounded
                end
                changed = true
                assistlabel:Change("Recommended Power: "..tostring(round(magnitude)))
                task.wait(0.05)
            end
       end
    if powerassist == false and changed then
        assistlabel:Change("Recommended Power:")
        end
    end
end)

Main:AddToggle({Name = "Auto Power",Callback = function(value)
    autopwr = value
    spawn(function()
    while true do wait()
       if autopwr and closestHoop() then
            local  magnitude = (char.HumanoidRootPart.Position - closestHoop().Position).Magnitude * 1.5
            if magnitude < 100 then
                local function round(to_round)
                    local divided = to_round / 5
                    local rounded = 5 * math.floor(divided)
                    return rounded
                end
                changed = true
                game.Players.LocalPlayer.Power.Value = round(magnitude)
                task.wait(0.05)
                end
           end
        end
    end)
end})
