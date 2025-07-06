	local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
	local Window = Rayfield:CreateWindow({
		Name = "Farm Hub",
		Icon = 0, -- Icon in Topbar. Can use Lucide Icons (string) or Roblox Image (number). 0 to use no icon (default).
		LoadingTitle = "s0ul On top",
		LoadingSubtitle = "by Sirius",
		ShowText = "Rayfield", -- for mobile users to unhide rayfield, change if you'd like
		Theme = "Default", -- Check https://docs.sirius.menu/rayfield/configuration/themes

		ToggleUIKeybind = "v", -- The keybind to toggle the UI visibility (string like "K" or Enum.KeyCode)

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
end)

local FarmTab = Window:CreateTab("Farm", 4483362458) -- Title, Image
local PvPTab = Window:CreateTab("PvP", 4483362458) -- Title, Image
local ToolTab = Window:CreateTab("Free Tool", 4483362458) -- Title, Image

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
