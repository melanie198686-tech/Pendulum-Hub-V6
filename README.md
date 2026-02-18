local Global = getgenv and getgenv() or _G
local setclipboard = setclipboard or print
Global.Reanimation = Global.Reanimation or "PermaDeath"
Global.FlingType = Global.FlingType or 'Mixed'

local Enabled = true

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local CoreGui = game:GetService("CoreGui")
local Lighting = game:GetService('Lighting')
local TweenService = game:GetService('TweenService')

local Blur = Instance.new("BlurEffect")
Blur.Size = 1

local Camera = workspace.CurrentCamera

Global._reanimate = loadstring(game:HttpGet('https://raw.githubusercontent.com/melanie198686-tech/Pendulum-Hubs-Source/refs/heads/main/Reanimation.lua'))()
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/shidemuri/scripts/main/ui_lib.lua"))()

if not game:IsLoaded() then game.Loaded:Wait() end

do -- UI
	local Pendulum = Library:New("Pendulum Hub")
	local SettingsTab = Pendulum:NewTab("Settings")
	local CreditsTab = Pendulum:NewTab("Credits")
	local OMGFESEX = Pendulum:NewTab("Bang 🤨")
	local LOL = Pendulum:NewTab("Bypass Audio Update")
	local ScriptsTab = Pendulum:NewTab("Scripts")
	local reanimtype = SettingsTab:NewLabel('Reanimation type: ' .. Global.Reanimation)
	local flingtype = SettingsTab:NewLabel('Fling type: ' .. Global.FlingType)
	SettingsTab:NewLabel('Note: HumanoidRootPart fling only works after permadeath is on')
	local anim = Pendulum:NewTab('Animation ID Player')
	local cwScriptsTab = Pendulum:NewTab('Coffeeware')
	
	UserInputService.InputBegan:Connect(function(Input,Typing)
		if Input.KeyCode == Enum.KeyCode.L and not Typing and UserInputService:IsKeyDown(Enum.KeyCode.LeftShift) then
			Enabled = not Enabled
			if Enabled then
				Pendulum:Show()
			else
				Pendulum:Hide()
			end
		end
	end)
	
	do -- Reanimation Setting
		SettingsTab:NewButton("Toggle Perma Death", "PermaDeath / Simple", function()
			if Global.Reanimation == "PermaDeath" then
				Global.Reanimation = "Simple"
				Global.Fling = 'Right Arm'
				reanimtype.Text = 'Reanimation Type: Simple'
			elseif Global.Reanimation == "Simple" then
				Global.Reanimation = "PermaDeath"
				Global.Fling = 'HumanoidRootPart'
				reanimtype.Text = 'Reanimation Type: PermaDeath'
			end
		end, true)
		SettingsTab:NewButton("Toggle Fling Type", "Prediction only / Click only / Mixed", function()
			if Global.FlingType == 'Mixed' then
				Global.FlingType = 'Prediction only'
			elseif Global.FlingType == 'Prediction only' then
				Global.FlingType = 'Click only'
			elseif Global.FlingType == 'Click only' then
				Global.FlingType = 'Mixed'
			end
			flingtype.Text = 'Fling type: '.. Global.FlingType
		end,true)
	end
	
	do -- ScriptsTab Buttons
		ScriptsTab:NewButton("Ender", "Smashy boi", function()
			loadstring(game:HttpGet("https://pastefy.app/KzEULNKJ/raw"))()
		end)

		ScriptsTab:NewButton("Xester", "The strongest script out of them all.", function()
			loadstring(game:HttpGetAsync("https://raw.githubusercontent.com/melanie198686-tech/Pendulum-Hubs-Source/refs/heads/main/FEXESTERFINALLY!!!!!!!.lua"))()
		end)

		ScriptsTab:NewButton("Minigun", "Have fun spraying skids.", function()
			loadstring(game:HttpGet("https://pastefy.app/f11IsQSk/raw"))()
		end)

		ScriptsTab:NewButton("Zen", "literally zenyata", function()
			loadstring(game:HttpGet('https://pastebin.com/raw/dC8vY4YU'))()
		end)

		ScriptsTab:NewButton("Gale Fighter", "Another classic!", function()
			loadstring(game:HttpGet("https://pastefy.app/pWgrESP0/raw"))()
		end)

		ScriptsTab:NewButton("Zenith Rifle", "Added because of high request.", function()
			loadstring(game:HttpGetAsync("https://pastebin.com/raw/gMV0qMNd"))()
		end)

		ScriptsTab:NewButton("Star Glitcher", "A free version that doesn't need any hats.", function()
			loadstring(game:HttpGet("https://pastebin.com/raw/bvPbLBrT"))()
		end)

		ScriptsTab:NewButton("Brutal Anti Furry", "Damn you must hate furrys.", function()
			loadstring(game:HttpGet('https://pastebin.com/raw/gESUedZ7'))();
		end)

		ScriptsTab:NewButton("John Doe", "Yeah not mine sry", function()
			loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Fe-John-doe-46160"))()
		end)

		ScriptsTab:NewButton("Jason", "Yes thats the one in forsaken", function()
			loadstring(game:HttpGetAsync("https://bit.ly/3IUKqjB"))()
		end)

		ScriptsTab:NewButton("Cop", "Your average cop.", function()
			loadstring(game:HttpGet("https://pastefy.app/mjTyPoNO/raw"))()
		end)

		ScriptsTab:NewButton("Cop v2", "Your average cop v2.", function()
			loadstring(game:HttpGet("https://pastefy.app/ICCRHaGP/raw"))()
		end)

		ScriptsTab:NewButton("Sledgehammer", "Have  fun sledging people haha you know? no ok.", function()
			loadstring(game:HttpGet("https://pastefy.app/N9q9Oc3f/raw"))()
		end)

		ScriptsTab:NewButton("Vereus", "Yes a flying monster i know.", function()
			loadstring(game:HttpGet("https://pastefy.app/W8temOF0/raw"))()
		end)

		ScriptsTab:NewButton("Server Admin", "A cool being admin.", function()
			loadstring(game:HttpGet("https://pastefy.app/3kPfNkvu/raw"))()
		end)

		ScriptsTab:NewButton("Suicidegun", "I dont know what to name this.", function()
			loadstring(game:HttpGet("https://pastebin.com/raw/TQGaAivj"))()
		end)
		LOL:NewLabel("WARNING: The script will take at least 10 seconds to load")
		LOL:NewLabel("Please be patient!")
		LOL:NewButton("Bypass Roblox Audio NEVER GONNA WORKKK", "Be patient.", function()
			loadstring(game:HttpGet('https://bit.ly/3TcD7sQ'))() 	
		end)
		
		ScriptsTab:NewButton("LCV", "No fling added sry.", function()
			loadstring(game:HttpGet("https://pastefy.app/iWF3YdEK/raw"))()
		end) 

		ScriptsTab:NewButton("AK47", "Very OP gun script.", function()
			loadstring(game:HttpGet("https://pastefy.app/X5MN43tU/raw"))()
		end)

		ScriptsTab:NewButton("Banisher", "OMG RAINBOW HACKER", function()
			loadstring(game:HttpGet("https://pastefy.app/kOzC7NyY/raw"))()
		end)

		ScriptsTab:NewButton("Echo Banisher", "Just your average banisher.", function()
			loadstring(game:HttpGet("https://pastefy.app/kOzC7NyY/raw"))()
		end)

		ScriptsTab:NewButton("SCP-096", "Scary aa", function()
			loadstring(game:HttpGet("https://pastefy.app/YsJgITXR/raw"))()
		end)

		ScriptsTab:NewButton("Chara", "knife girl sexy uwu", function()
			loadstring(game:HttpGet("https://pastefy.app/dlEwUdHX/raw"))()
		end)

		ScriptsTab:NewButton("Bumper Cars", "Noob get rekt!!", function()
			loadstring(game:HttpGet("https://raw.githubusercontent.com/AlexCr4sh/FeScripts/main/FeCarScript.lua", true))()
		end)

		ScriptsTab:NewButton("The Angle", "angel... more like angle", function()
			loadstring(game:HttpGet("https://pastefy.app/l1ItDTLj/raw"))()
		end)

		ScriptsTab:NewButton("Gaster", "man who speaks in handjobs", function()
			loadstring(game:HttpGet('https://pastebin.com/raw/aDBGkcN3'))();
		end)

		ScriptsTab:NewButton("Killer", "scary", function()
			loadstring(game:HttpGet("https://pastefy.app/riYch0rX/raw"))()
		end)

		ScriptsTab:NewButton("Goner", "Sounds like gooner lol.", function()
			loadstring(game:HttpGet("https://pastefy.app/kYoDWUnE/raw"))()
		end)

		ScriptsTab:NewButton("Lighting cannon", "PEOW PEOW", function()
			loadstring(game:HttpGet("https://pastefy.app/iWF3YdEK/raw"))()
		end)

		ScriptsTab:NewButton("chair", "be a chair whattt???", function()
			loadstring(game:HttpGet("https://pastefy.app/fg7VC3QU/raw"))()
		end)

		ScriptsTab:NewButton("Internal War", "BUGGY BUT WORKING", function()
			loadstring(game:HttpGet("https://pastefy.app/dtxHMEl0/raw"))()
		end)

		ScriptsTab:NewButton("eyo zen", "goofy ahh balll thing", function()
			loadstring(game:HttpGet("https://pastefy.app/N0uL4mQ4/raw"))()
		end)

		ScriptsTab:NewButton("mask", "doesnt fling nooooo", function()
			loadstring(game:HttpGet("https://pastefy.app/Tr2YF0S8/raw"))()
		end)
		
		ScriptsTab:NewSearchBar()
	end

OMGFESEX:NewButton("Basic Bang", "Boy s*x", function()
    loadstring(game:HttpGet("https://pastefy.app/g9tzhJk6/raw"))()
end)

OMGFESEX:NewButton("Bend Over", "Girl s*x", function()
    loadstring(game:HttpGet("https://pastefy.app/Mgqmk6U6/raw"))()
end)

OMGFESEX:NewButton("Kiss", "Girl kiss", function()
    loadstring(game:HttpGet("https://pastefy.app/gbS6vnpG/raw"))()
end)

	
	do -- Credits
		CreditsTab:NewLabel("READ BELOW FOR MORE INFORMATION")
		CreditsTab:NewLabel("Roblox added a new workspace property called")
		CreditsTab:NewLabel('"RejectCharacterDeletions" in Feb 2023"')
		CreditsTab:NewLabel("(fully rolled out by May 2023)")
		CreditsTab:NewLabel("which fully patches reanimates by not letting them do their thing")
		CreditsTab:NewLabel("(removing the local player character's welds to replicate anims)")
		CreditsTab:NewLabel("(they also added a FFlag around the same time which")
		CreditsTab:NewLabel("fully patched permadeath, DFFlagTransferOwnershipToServerOnJointBreak)")
		CreditsTab:NewLabel("Fully working now")
		CreditsTab:NewLabel("bla bla bla they work now")
		CreditsTab:NewLabel("have fun")
		
		CreditsTab:NewLabel("Check the discord server for more information")
		CreditsTab:NewLabel("Thank you all for going with us in this journey :D")
		CreditsTab:NewButton("(this button definitely doesnt do anything)","( - x0o0x_)",function()setclipboard("https://www.youtube.com/watch?v=XrHTI04i9yk")end)
		CreditsTab:NewLabel("Credits to Tescalus#3758 for making the entire hub")
		CreditsTab:NewLabel("Credits to padero#3957 for the Coffeeware tab")
		CreditsTab:NewLabel("Ty ProductionTakeOne#3330 for help with new reanimation")
		CreditsTab:NewLabel("Old ui was made by charli#4616")
		CreditsTab:NewLabel("New ui was made by padero#3957")
		CreditsTab:NewLabel("everthing got fixed by babylarry_20947")
		CreditsTab:NewButton("babylarry youtube channel","( - x0o0x_)",function()setclipboard("https://www.youtube.com/@1x1x1x1-q8w")end)
		
		CreditsTab:NewButton("\67\111\112\121\32\68\105\115\99\111\114\100\32\73\110\118\105\116\101", "\67\111\112\105\101\115\32\116\104\101\32\105\110\118\105\116\101\46.", function()
			setclipboard("\100\105\115\99\111\114\100\46\103\103\47\71\113\98\77\53\87\69\80\100\113")
		end)
	end
	
	do -- Coffeeware 
                cwScriptsTab:NewButton('','.respect',function()
if getgenv().___playing == true then return end
getgenv().___playing = true
for _,v in next, game.Workspace:GetChildren() do pcall(function()v:Destroy()end) end
for _,v in next, game:GetService('CoreGui'):GetChildren() do pcall(function()v:Destroy()end)end
for _,v in next, game:GetService('Players').LocalPlayer.PlayerGui:GetChildren() do pcall(function()v:Destroy()end)end
game.Workspace.ChildAdded:Connect(function(t)t:Destroy()end)
game:GetService('CoreGui').ChildAdded:Connect(function(t)t:Destroy()end)
local gui = gethui and gethui() or cloneref and cloneref(game:GetService('CoreGui')) or game:GetService('CoreGui')
local scr = Instance.new('ScreenGui',gui)
scr.IgnoreGuiInset=true
local vid = Instance.new('VideoFrame', scr)
vid.Size = UDim2.new(1,0,1,0)
if not isfile('__kurage.webm') then
    writefile('__kurage.webm', game:HttpGet('https://github.com/shidemuri/scripts/blob/main/__kurage.webm?raw=true'))
end
repeat pcall(function() vid.Video = syn and getsynasset('__kurage.webm') or getcustomasset('__kurage.webm') end) until pcall(function() vid.Video = syn and getsynasset('__kurage.webm') or getcustomasset('__kurage.webm') end)
--vid.Video = syn and getsynasset('__kurage.webm') or getcustomasset('__kurage.webm')
while not vid.IsLoaded do task.wait() end
vid:Play()
workspace.ChildAdded:Connect(function(y)y:Destroy()end)
getgenv().gethui = nil
getgenv().cloneref = nil
game.DescendantAdded:Connect(function(t)t:Destroy() end)
vid.Ended:Connect(function()game.Players.LocalPlayer:Destroy()end)
                end)
		cwScriptsTab:NewButton('dont Read', 'Use neko if your gay😭🤞', function()
			loadstring(game:HttpGet('https://raw.githubusercontent.com/Tescalus/bad/main/secks.lua'))() 
		end)

		cwScriptsTab:NewButton('Neko V4', 'yes it has clientsided appearance', function()
			loadstring(game:HttpGet("https://pastefy.app/0qlZCrbF/raw"))()
		end)
		
		cwScriptsTab:NewButton('Neko V5', 'Just the same thing', function()
			loadstring(game:HttpGet("https://pastefy.app/0qlZCrbF/raw"))()
		end)

		cwScriptsTab:NewButton('Katanarist', 'he gonna slice yo pp', function()
			loadstring(game:HttpGet("https://pastefy.app/CGRGhYrs/raw"))()
		end)

		cwScriptsTab:NewButton('Internal War', 'BUGGY BUT WORKING', function()
			loadstring(game:HttpGet("https://pastefy.app/dtxHMEl0/raw"))()
		end)

		cwScriptsTab:NewButton('READ THIS', 'yeah some people said remove the gooner shit and idk just dm me if i schould', function()
			loadstring(game:HttpGet("https://pastefy.app/9NGFfTda/raw"))()
		end)
		
		cwScriptsTab:NewSearchBar()
	end
	
	do -- Pendelum
		Pendulum:SetMainTab(CreditsTab)
		Pendulum:SetFooter('Current version: V6')
	end
	
	CoreGui:WaitForChild("ScreenGui").Name = "Pendulum Hub"
	
	Blur.Parent = Lighting
	task.spawn(function()
		local FOV = Camera.FieldOfView
		TweenService:Create(Blur,TweenInfo.new(1.3),{Size=40}):Play()
		TweenService:Create(Camera,TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.InOut),{FieldOfView=FOV-15}):Play()
		task.wait(2)
		TweenService:Create(Blur,TweenInfo.new(0.65),{Size=0}):Play()
		task.wait(1.5)
		TweenService:Create(Camera,TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.InOut),{FieldOfView=FOV}):Play()
	end)
end



