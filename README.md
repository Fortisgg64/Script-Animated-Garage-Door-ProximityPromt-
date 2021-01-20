local frame = script.Parent
local Frame = game.Workspace.Door.DoorFrame
local openSound = frame:WaitForChild("DoorOpen")
local closeSound = frame:WaitForChild("DoorClose")
local proximityprompt = Frame:WaitForChild("ProximityPrompt")
local model = frame.Parent
local frameClose = model:WaitForChild("Door-Close")
local frameOpen = model:WaitForChild("Door-Open")
local opened = model:WaitForChild("Opened")
local tweenService = game:GetService("TweenService")

local debounce = true
proximityprompt.Triggered:Connect(function()
	if debounce == true then
		debounce = false
		if opened.Value == true then
			opened.Value = false

			closeSound:Play()
			tweenService:Create(frame,TweenInfo.new(.35),{CFrame = frameClose.CFrame}):Play()
		else
			opened.Value = true

			openSound:Play()
			tweenService:Create(frame,TweenInfo.new(.35),{CFrame = frameOpen.CFrame}):Play()
		end

		wait(.35)
		debounce = true
	end
end)
