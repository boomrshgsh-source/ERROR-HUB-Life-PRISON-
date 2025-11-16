local SoundService = game:GetService("SoundService")
local loadSound = Instance.new("Sound")
loadSound.SoundId = "rbxassetid://98797174600699"
loadSound.Volume = 1
loadSound.Parent = SoundService
loadSound:Play()
game.Debris:AddItem(loadSound, 3)

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/x2zu/OPEN-SOURCE-UI-ROBLOX/refs/heads/main/X2ZU%20UI%20ROBLOX%20OPEN%20SOURCE/DummyUi-leak-by-x2zu/fetching-main/Tools/Framework.luau"))()

local Window = Library:Window({
    Title = "ERROR HUB",
    Desc = "PRISON LIFE",
    Icon = 87372447687978,
    Theme = "Dark",
    Config = {
        Keybind = Enum.KeyCode.LeftControl,
        Size = UDim2.new(0, 350, 0, 300)  -- ปรับขนาด UI ให้เล็กลง
    },
    CloseUIButton = {
        Enabled = true,
        Text = "ERROR PRISON"
    }
})

local Players = game:GetService("Players")
local plr = Players.LocalPlayer

local buffEnabled = false

local function BuffGun(tool)
    if not buffEnabled then return end
    if tool:IsA("Tool") then
        task.wait(0.1)
        tool:SetAttribute("AutoFire", true)
        tool:SetAttribute("FireRate", 0.001)
        tool:SetAttribute("Damage", 999)
        tool:SetAttribute("IsReloading", false)
    end
end

local function ClearBuff(tool)
    if tool:IsA("Tool") then
        task.wait(0.1)
        tool:SetAttribute("AutoFire", false)
        tool:SetAttribute("FireRate", nil)
        tool:SetAttribute("Damage", nil)
        tool:SetAttribute("IsReloading", nil)
    end
end

local function HandleBuffOnTool(tool)
    if buffEnabled then
        BuffGun(tool)
    else
        ClearBuff(tool)
    end
end

local function ConnectCharacter(char)
    char.ChildAdded:Connect(HandleBuffOnTool)
end

plr.CharacterAdded:Connect(function(char)
    ConnectCharacter(char)
end)

if plr.Character then
    ConnectCharacter(plr.Character)
end

for _, tool in pairs(plr.Backpack:GetChildren()) do
    HandleBuffOnTool(tool)
end

plr.Backpack.ChildAdded:Connect(HandleBuffOnTool)

local Tab = Window:Tab({Title = "Main", Icon = "star"})
Tab:Section({Title = ""})

Tab:Toggle({
    Title = "บัพปืน",
    Value = false,
    Callback = function(val)
        buffEnabled = val
        if buffEnabled then
            for _, tool in pairs(plr.Backpack:GetChildren()) do
                BuffGun(tool)
            end
            if plr.Character then
                for _, tool in pairs(plr.Character:GetChildren()) do
                    BuffGun(tool)
                end
            end
        else
            for _, tool in pairs(plr.Backpack:GetChildren()) do
                ClearBuff(tool)
            end
            if plr.Character then
                for _, tool in pairs(plr.Character:GetChildren()) do
                    ClearBuff(tool)
                end
            end
        end
    end
})
