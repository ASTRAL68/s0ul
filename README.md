local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "Animal Simulator  s0ul HUB",
   Icon = 0, -- Icon in Topbar. Can use Lucide Icons (string) or Roblox Image (number). 0 to use no icon (default).
   LoadingTitle = "s0ul ON TOP",
   LoadingSubtitle = "",
   Theme = "Default", -- Check https://docs.sirius.menu/rayfield/configuration/themes

   ToggleUIKeybind = "V", -- The keybind to toggle the UI visibility (string like "K" or Enum.KeyCode)

   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false, -- Prevents Rayfield from warning when the script has a version mismatch with the interface

   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "Big Hub"
   },

   Discord = {
      Enabled = false, -- Prompt the user to join your Discord server if their executor supports it
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },

   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided", -- Use this to tell the user how to get a key
      FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})

local FarmTab = Window:CreateTab("Farm", 4483362458) -- Title, Image

local FreeTab = Window:CreateTab("Free Tool", 4483362458) -- Title, Image

local Button = FarmTab:CreateButton({
   Name = "Anti AFK",
   Callback = function()
while true do
    wait(300) -- Attendre 5 minutes
    local player = game.Players.LocalPlayer
    if player and player.Character then
        player.Character:Move(Vector3.new(0, 0, 0)) -- Simulation de mouvement
    end
end
   -- The function that takes place when the button is pressed
   end,
})

local Section = FarmTab:CreateSection("-Grind Farm-") -- Section Title

local Toggle = FarmTab:CreateToggle({
   Name = "Farming Grind 5k/Spawn",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
		isHitting = Value
		if isHitting then
			task.spawn(function()
				while isHitting do
					local player = game:GetService("Players").LocalPlayer
					local level = player:FindFirstChild("leaderstats") and player.leaderstats:FindFirstChild("Level") and player.leaderstats.Level.Value
					
					if level and level < 5000 then
						local dummy = workspace:FindFirstChild("MAP") and workspace.MAP:FindFirstChild("dummies") and workspace.MAP.dummies:FindFirstChild("Dummy")
						if dummy and dummy:FindFirstChild("Humanoid") and dummy:FindFirstChild("HumanoidRootPart") then
							local hrp = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
							if hrp then
								hrp.CFrame = dummy.HumanoidRootPart.CFrame + Vector3.new(0, 0, 5)
							end
							local args = {
								dummy.Humanoid,
								2
							}
							game:GetService("ReplicatedStorage"):WaitForChild("jdskhfsIIIllliiIIIdchgdIiIIIlIlIli"):FireServer(unpack(args))
						end
					else
						local dummy2 = workspace:FindFirstChild("MAP") and workspace.MAP:FindFirstChild("5k_dummies") and workspace.MAP["5k_dummies"]:FindFirstChild("Dummy2")
						if dummy2 and dummy2:FindFirstChild("Humanoid") then
							local hrp = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
							if hrp and dummy2:FindFirstChild("HumanoidRootPart") then
								hrp.CFrame = dummy2.HumanoidRootPart.CFrame + Vector3.new(0, 0, 5)
							end
							local args = {
								dummy2.Humanoid,
								2
							}
							game:GetService("ReplicatedStorage").jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(unpack(args))
						end
					end
					task.wait()
				end
			end)
		end
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})

local Toggle = FarmTab:CreateToggle({
   Name = "NewLightningball Grind 5k/Spawn",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
    		isHitting = Value
		if isHitting then
			task.spawn(function()
				while isHitting do
					local player = game:GetService("Players").LocalPlayer
					local level = player:FindFirstChild("leaderstats") and player.leaderstats:FindFirstChild("Level") and player.leaderstats.Level.Value

					local dummy = nil
					if level and level < 5000 then
						dummy = workspace:FindFirstChild("MAP") and workspace.MAP:FindFirstChild("dummies") and workspace.MAP.dummies:FindFirstChild("Dummy")
					else
						dummy = workspace:FindFirstChild("MAP") and workspace.MAP:FindFirstChild("5k_dummies") and workspace.MAP["5k_dummies"]:FindFirstChild("Dummy2")
					end

					if dummy and dummy:FindFirstChild("HumanoidRootPart") then
						local args = {
							dummy.HumanoidRootPart.Position,
							"NewLightningball"
						}
						game:GetService("ReplicatedStorage").SkillsInRS.RemoteEvent:FireServer(unpack(args))
					end

					task.wait()
				end
			end)
		end
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})

local Toggle = FarmTab:CreateToggle({
   Name = "Auto Coin",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
    isHitting = Value
    
            if isHitting then
                -- Lancer une boucle non bloquante
                task.spawn(function()
                    while isHitting do
game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("CoinEvent"):FireServer()
task.wait(0.1) -- Pause
    end
                end)
            end
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})

local ToggleActive = false  --variable

local ToggleActive = false

-- Liste
local BossList = {
    "CRABBOSS",
    "CENTAUR",
    "BOSSBEAR",
    "BOSSDEER",
    "DragonGiraffe",
    "Griffin",
    "LavaGorilla",
}

local hitvalue= {
    CRABBOSS = 1,  
    CENTAUR = 1, 
    BOSSBEAR = 1, 
    BOSSDEER = 1,
    DragonGiraffe = 1,  
    Griffin = 1,
    LavaGorilla = 1,
}

local Toggle = FarmTab:CreateToggle({
    Name = "Farming No tp Boss",
    CurrentValue = false,
    Flag = "AutoAttackBoss",
    Callback = function(Value)
        ToggleActive = Value
        
        while ToggleActive do
            for _, bossName in ipairs(BossList) do
                local bossNPC = workspace.NPC:FindFirstChild(bossName)
                if bossNPC and bossNPC:FindFirstChild("Humanoid") then
                    local damage = hitvalue[bossName] or 1
                    
                    game:GetService("ReplicatedStorage").jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(
                        bossNPC.Humanoid,
                        damage
                    )
                end
            end
            wait()
        end
    end,
})

local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "Animal Simulator  s0ul HUB",
   Icon = 0, -- Icon in Topbar. Can use Lucide Icons (string) or Roblox Image (number). 0 to use no icon (default).
   LoadingTitle = "s0ul ON TOP",
   LoadingSubtitle = "",
   Theme = "Default", -- Check https://docs.sirius.menu/rayfield/configuration/themes

   ToggleUIKeybind = "V", -- The keybind to toggle the UI visibility (string like "K" or Enum.KeyCode)

   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false, -- Prevents Rayfield from warning when the script has a version mismatch with the interface

   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "Big Hub"
   },

   Discord = {
      Enabled = false, -- Prompt the user to join your Discord server if their executor supports it
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },

   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided", -- Use this to tell the user how to get a key
      FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})

local FarmTab = Window:CreateTab("Farm", 4483362458) -- Title, Image

local FreeTab = Window:CreateTab("Free Tool", 4483362458) -- Title, Image

local Button = FarmTab:CreateButton({
   Name = "Anti AFK",
   Callback = function()
while true do
    wait(300) -- Attendre 5 minutes
    local player = game.Players.LocalPlayer
    if player and player.Character then
        player.Character:Move(Vector3.new(0, 0, 0)) -- Simulation de mouvement
    end
end
   -- The function that takes place when the button is pressed
   end,
})

local Section = FarmTab:CreateSection("-Grind Farm-") -- Section Title

local Toggle = FarmTab:CreateToggle({
   Name = "Farming Grind 5k/Spawn",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
		isHitting = Value
		if isHitting then
			task.spawn(function()
				while isHitting do
					local player = game:GetService("Players").LocalPlayer
					local level = player:FindFirstChild("leaderstats") and player.leaderstats:FindFirstChild("Level") and player.leaderstats.Level.Value
					
					if level and level < 5000 then
						local dummy = workspace:FindFirstChild("MAP") and workspace.MAP:FindFirstChild("dummies") and workspace.MAP.dummies:FindFirstChild("Dummy")
						if dummy and dummy:FindFirstChild("Humanoid") and dummy:FindFirstChild("HumanoidRootPart") then
							local hrp = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
							if hrp then
								hrp.CFrame = dummy.HumanoidRootPart.CFrame + Vector3.new(0, 0, 5)
							end
							local args = {
								dummy.Humanoid,
								2
							}
							game:GetService("ReplicatedStorage"):WaitForChild("jdskhfsIIIllliiIIIdchgdIiIIIlIlIli"):FireServer(unpack(args))
						end
					else
						local dummy2 = workspace:FindFirstChild("MAP") and workspace.MAP:FindFirstChild("5k_dummies") and workspace.MAP["5k_dummies"]:FindFirstChild("Dummy2")
						if dummy2 and dummy2:FindFirstChild("Humanoid") then
							local hrp = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
							if hrp and dummy2:FindFirstChild("HumanoidRootPart") then
								hrp.CFrame = dummy2.HumanoidRootPart.CFrame + Vector3.new(0, 0, 5)
							end
							local args = {
								dummy2.Humanoid,
								2
							}
							game:GetService("ReplicatedStorage").jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(unpack(args))
						end
					end
					task.wait()
				end
			end)
		end
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})

local Toggle = FarmTab:CreateToggle({
   Name = "NewLightningball Grind 5k/Spawn",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
    		isHitting = Value
		if isHitting then
			task.spawn(function()
				while isHitting do
					local player = game:GetService("Players").LocalPlayer
					local level = player:FindFirstChild("leaderstats") and player.leaderstats:FindFirstChild("Level") and player.leaderstats.Level.Value

					local dummy = nil
					if level and level < 5000 then
						dummy = workspace:FindFirstChild("MAP") and workspace.MAP:FindFirstChild("dummies") and workspace.MAP.dummies:FindFirstChild("Dummy")
					else
						dummy = workspace:FindFirstChild("MAP") and workspace.MAP:FindFirstChild("5k_dummies") and workspace.MAP["5k_dummies"]:FindFirstChild("Dummy2")
					end

					if dummy and dummy:FindFirstChild("HumanoidRootPart") then
						local args = {
							dummy.HumanoidRootPart.Position,
							"NewLightningball"
						}
						game:GetService("ReplicatedStorage").SkillsInRS.RemoteEvent:FireServer(unpack(args))
					end

					task.wait()
				end
			end)
		end
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})

local Toggle = FarmTab:CreateToggle({
   Name = "Auto Coin",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
    isHitting = Value
    
            if isHitting then
                -- Lancer une boucle non bloquante
                task.spawn(function()
                    while isHitting do
game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("CoinEvent"):FireServer()
task.wait(0.1) -- Pause
    end
                end)
            end
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})

local ToggleActive = false  --variable

local ToggleActive = false

-- Liste
local BossList = {
    "CRABBOSS",
    "CENTAUR",
    "BOSSBEAR",
    "BOSSDEER",
    "DragonGiraffe",
    "Griffin",
    "LavaGorilla",
}

local hitvalue= {
    CRABBOSS = 1,  
    CENTAUR = 1, 
    BOSSBEAR = 1, 
    BOSSDEER = 1,
    DragonGiraffe = 1,  
    Griffin = 1,
    LavaGorilla = 1,
}

local Toggle = FarmTab:CreateToggle({
    Name = "Farming No tp Boss",
    CurrentValue = false,
    Flag = "AutoAttackBoss",
    Callback = function(Value)
        ToggleActive = Value
        
        while ToggleActive do
            for _, bossName in ipairs(BossList) do
                local bossNPC = workspace.NPC:FindFirstChild(bossName)
                if bossNPC and bossNPC:FindFirstChild("Humanoid") then
                    local damage = hitvalue[bossName] or 1
                    
                    game:GetService("ReplicatedStorage").jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(
                        bossNPC.Humanoid,
                        damage
                    )
                end
            end
            wait()
        end
    end,
})

local PvPTab = Window:CreateTab("PvP", 4483362458) -- Title, Image

local isHitting = false
local players = game:GetService("Players")
local replicatedStorage = game:GetService("ReplicatedStorage")
local player = players.LocalPlayer

-- Fonction pour obtenir le joueur le plus proche
local function getClosestPlayer()
    local closestPlayer = nil
    local shortestDistance = math.huge  -- Une valeur initiale infinie

    -- Parcours de tous les joueurs
    for _, targetPlayer in pairs(players:GetPlayers()) do
        if targetPlayer ~= player and targetPlayer.Character and targetPlayer.Character:FindFirstChild("HumanoidRootPart") then
            local targetPosition = targetPlayer.Character.HumanoidRootPart.Position
            local playerPosition = player.Character.HumanoidRootPart.Position
            local distance = (targetPosition - playerPosition).Magnitude  -- Calcul de la distance

            -- Si cette distance est plus courte que la précédente, on met à jour
            if distance < shortestDistance then
                closestPlayer = targetPlayer
                shortestDistance = distance
            end
        end
    end

    return closestPlayer
end

local function startKillAura()
    isHitting = true
    while isHitting do
        local closestPlayer = getClosestPlayer()  -- Récupère le joueur le plus proche
        if closestPlayer and closestPlayer.Character and closestPlayer.Character:FindFirstChild("Humanoid") then
            local args = {
                [1] = closestPlayer.Character.Humanoid,
                [2] = 1  -- Valeur à envoyer au serveur, peut être ajustée si nécessaire
            }
            -- Appelez la fonction sur le serveur
            replicatedStorage.jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(unpack(args))  -- Vérifiez ce nom
        end
        task.wait()  -- Ajoutez une petite attente pour éviter de trop solliciter le serveur
    end
end

local function stopKillAura()
    isHitting = false
end

-- Création du Toggle pour activer/désactiver le kill aura
local Toggle = PvPTab:CreateToggle({
    Name = "kill aura",
    CurrentValue = false,
    Flag = "Toggle1", 
    Callback = function(Value)
        if Value then
            task.spawn(startKillAura)
        else
            stopKillAura()
        end
    end,
})

local Section = FreeTab:CreateSection("Weapon premium giver") -- Section Title

local Button = FreeTab:CreateButton({
   Name = "S7",
   Callback = function()
    local args = {
    "S7"
}
game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("WeaponEvent"):FireServer(unpack(args))
   -- The function that takes place when the button is pressed
   end,
})

local Button = FreeTab:CreateButton({
   Name = "S8",
   Callback = function()
    local args = {
    "S8"
}
game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("WeaponEvent"):FireServer(unpack(args))
   -- The function that takes place when the button is pressed
   end,
})

local Button = FreeTab:CreateButton({
   Name = "SSSS1",
   Callback = function()
    local args = {
    "SSSS1"
}
game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("WeaponEvent"):FireServer(unpack(args))
   -- The function that takes place when the button is pressed
   end,
})

local Button = FreeTab:CreateButton({
   Name = "SSSS2",
   Callback = function()
    local args = {
    "SSSS2"
}
game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("WeaponEvent"):FireServer(unpack(args))
   -- The function that takes place when the button is pressed
   end,
})

local Button = FreeTab:CreateButton({
   Name = "SSSSSS2",
   Callback = function()
    local args = {
    "SSSSSSS2"
}
game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("WeaponEvent"):FireServer(unpack(args))
   -- The function that takes place when the button is pressed
   end,
})

local Button = FreeTab:CreateButton({
   Name = "SSSSSSS4",
   Callback = function()
    local args = {
    "SSSSSSS4"
}
game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("WeaponEvent"):FireServer(unpack(args))
   -- The function that takes place when the button is pressed
   end,
})

local Section = FarmTab:CreateSection("Event")

local Button = FarmTab:CreateButton({
   Name = "Get All Cow in shop",
   Callback = function()
    		local ReplicatedStorage = game:GetService("ReplicatedStorage")
local SkinClickEvent = ReplicatedStorage:WaitForChild("Events"):WaitForChild("SkinClickEvent")

for i = 1, 11 do
    local args = {
        "COW" .. i,
        "v2"
    }
    SkinClickEvent:FireServer(unpack(args))
    task.wait(0.1)
end
   -- The function that takes place when the button is pressed
   end,
})

local ScriptTab = Window:CreateTab("Script", 4483362458) -- Title, Image

local Button = ScriptTab:CreateButton({
   Name = "Counter kils",
   Callback = function()
    -- Gui to Lua
-- Version: 3.2

-- Instances:

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local TextLabel = Instance.new("TextLabel")
local TextLabel_2 = Instance.new("TextLabel")
local TextLabel_3 = Instance.new("TextLabel")
local UICorner_2 = Instance.new("UICorner")
local TextLabel_4 = Instance.new("TextLabel")
local TextButton = Instance.new("TextButton")

--Properties:

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(47, 47, 47)
Frame.BackgroundTransparency = 0.500
Frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.44266054, 0, 0.054502368, 0)
Frame.Size = UDim2.new(0, 216, 0, 103)

UICorner.Parent = Frame

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.BorderSizePixel = 0
TextLabel.Position = UDim2.new(0.537037015, 0, 0.349514574, 0)
TextLabel.Size = UDim2.new(0, 71, 0, 50)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "0"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextSize = 30.000

TextLabel_2.Parent = Frame
TextLabel_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_2.BackgroundTransparency = 1.000
TextLabel_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextLabel_2.BorderSizePixel = 0
TextLabel_2.Position = UDim2.new(0.157407403, 0, 0.349514574, 0)
TextLabel_2.Size = UDim2.new(0, 82, 0, 50)
TextLabel_2.Font = Enum.Font.SourceSans
TextLabel_2.Text = "KILLS:"
TextLabel_2.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_2.TextSize = 30.000

TextLabel_3.Parent = Frame
TextLabel_3.BackgroundColor3 = Color3.fromRGB(76, 76, 76)
TextLabel_3.BackgroundTransparency = 0.200
TextLabel_3.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextLabel_3.BorderSizePixel = 0
TextLabel_3.Size = UDim2.new(0, 216, 0, 36)
TextLabel_3.Font = Enum.Font.SourceSansBold
TextLabel_3.Text = "Kill counter"
TextLabel_3.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_3.TextSize = 35.000

local function updateKillCount()
    local player = game.Players.LocalPlayer
    if player and player:FindFirstChild("otherstats") and player.otherstats:FindFirstChild("Kill") then
        TextLabel.Text = tostring(player.otherstats.Kill.Value)
    else
        TextLabel.Text = "0"
    end
end

updateKillCount()

local killStat
local player = game.Players.LocalPlayer

if player then
    player:WaitForChild("otherstats"):WaitForChild("Kill")
    killStat = player.otherstats.Kill
    killStat:GetPropertyChangedSignal("Value"):Connect(updateKillCount)
end

UICorner_2.Parent = TextLabel_3

TextLabel_4.Parent = Frame
TextLabel_4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_4.BackgroundTransparency = 1.000
TextLabel_4.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextLabel_4.BorderSizePixel = 0
TextLabel_4.Position = UDim2.new(0.666666687, 0, 0.669902921, 0)
TextLabel_4.Size = UDim2.new(0, 72, 0, 34)
TextLabel_4.Font = Enum.Font.SourceSans
TextLabel_4.Text = "By s0ul"
TextLabel_4.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_4.TextSize = 17.000

TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextButton.BackgroundTransparency = 1.000
TextButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton.BorderSizePixel = 0
TextButton.Position = UDim2.new(0.833375692, 0, -0.00730451569, 0)
TextButton.Size = UDim2.new(0, 49, 0, 39)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "X"
TextButton.TextColor3 = Color3.fromRGB(213, 0, 0)
TextButton.TextSize = 20.000

-- Scripts:

local function FFPC_fake_script() -- TextButton.LocalScript 
	local script = Instance.new('LocalScript', TextButton)

	local Frame = script.Parent.Parent
	
	script.Parent.MouseButton1Click:Connect(function()
		Frame.Visible = false
	end)
end
coroutine.wrap(FFPC_fake_script)()

   -- The function that takes place when the button is pressed
   end,
})
