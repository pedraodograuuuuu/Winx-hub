-- JAPA HUB - Blue Lock Script
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local AutoFarm = Instance.new("TextButton")
local TeleportBola = Instance.new("TextButton")
local Speed = Instance.new("TextButton")
local Close = Instance.new("TextButton")

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.Name = "JAPA_HUB"

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.Position = UDim2.new(0.05, 0, 0.2, 0)
Frame.Size = UDim2.new(0, 200, 0, 220)

UICorner.Parent = Frame

local function createButton(name, position, text, func)
	local button = Instance.new("TextButton")
	button.Name = name
	button.Parent = Frame
	button.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	button.Position = position
	button.Size = UDim2.new(0, 180, 0, 40)
	button.Font = Enum.Font.GothamBold
	button.Text = text
	button.TextColor3 = Color3.fromRGB(255, 255, 255)
	button.TextSize = 14
	button.MouseButton1Click:Connect(func)
	local corner = Instance.new("UICorner", button)
	return button
end

createButton("AutoFarm", UDim2.new(0, 10, 0, 10), "Auto Farm", function()
	getgenv().AutoFarm = true
	while getgenv().AutoFarm do
		task.wait(0.1)
		local ball = workspace:FindFirstChild("Ball")
		if ball then
			game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = ball.CFrame * CFrame.new(0, 0, -3)
		end
	end
end)

createButton("TeleportBola", UDim2.new(0, 10, 0, 60), "Teleportar na Bola", function()
	local ball = workspace:FindFirstChild("Ball")
	if ball then
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = ball.CFrame * CFrame.new(0, 0, -3)
	end
end)

createButton("Speed", UDim2.new(0, 10, 0, 110), "Speed x3", function()
	local human = game.Players.LocalPlayer.Character
