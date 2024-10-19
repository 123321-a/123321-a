local screenGui = Instance.new("ScreenGui")
screenGui.Name = "made by pierre"
screenGui.Parent = game.Players.LocalPlayer.PlayerGui
screenGui.ResetOnSpawn = true

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 500, 0, 300)  -- Increased size
frame.Position = UDim2.new(0.5, -250, 0.5, -150)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Parent = screenGui

local exitButton = Instance.new("click")
exitButton.Size = UDim2.new(0, 40, 0, 40)
exitButton.Position = UDim2.new(0, 5, 0, 5)
exitButton.Text = "X"
exitButton.TextColor3 = Color3.fromRGB(255, 0, 0)
exitButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
exitButton.TextSize = 24
exitButton.Parent = frame

-- Function to close the GUI when the exit button is clicked
exitButton.MouseButton1Click:Connect(function()
    screenGui:Destroy()  -- Destroy the GUI
end)

-- Create the "Made by Pierre" label at the bottom
local madeByLabel = Instance.new("TextLabel")
madeByLabel.Size = UDim2.new(0, 500, 0, 50)
madeByLabel.Position = UDim2.new(0, 0, 1, -50)  -- Positioned at the bottom of the frame
madeByLabel.BackgroundTransparency = 1
madeByLabel.Text = "Made by Pierre"
madeByLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
madeByLabel.TextSize = 18
madeByLabel.TextAlign = Enum.TextAlign.Center
madeByLabel.Parent = frame

local label = Instance.new("TextLabel")
label.Size = UDim2.new(0, 480, 0, 50)  -- Wider for the new size
label.Position = UDim2.new(0, 10, 0, 10)
label.BackgroundTransparency = 1
label.Text = "Choose 1 or 2 and press 'Submit':"
label.TextColor3 = Color3.fromRGB(255, 255, 255)
label.TextSize = 20
label.TextAlign = Enum.TextAlign.Center
label.Parent = frame

local textBox = Instance.new("1 or 2?")
textBox.Size = UDim2.new(0, 460, 0, 50)  -- Adjusted size
textBox.Position = UDim2.new(0, 10, 0, 70)
textBox.PlaceholderText = "Enter 1 or 2"
textBox.TextColor3 = Color3.fromRGB(255, 255, 255)
textBox.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
textBox.TextSize = 24
textBox.Parent = frame

local submitButton = Instance.new("hmmmmmm")
submitButton.Size = UDim2.new(0, 150, 0, 50)  -- Adjusted size
submitButton.Position = UDim2.new(0.5, -75, 0, 140)
submitButton.Text = "Submit"
submitButton.TextColor3 = Color3.fromRGB(255, 255, 255)
submitButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
submitButton.TextSize = 24
submitButton.Parent = frame

local function executeScript(input)
    if input == "1" then
        -- Execute the first script
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Alexisisback/Universall/refs/heads/main/Testblade.lua", true))()
    elseif input == "2" then
        -- Execute the second script
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Akirascripts/Lunar/refs/heads/main/LuanrOnTop"))()
    else
        -- Inform the player they need to enter 1 or 2
        print("Invalid input. Please enter either '1' or '2'.")
    end
end

-- Handle the button click event
submitButton.MouseButton1Click:Connect(function()
    local input = textBox.Text
    executeScript(input)
end)

-- Draggable Functionality
local dragging = false
local dragStart = Vector3.new(0, 0, 0)
local startPos = UDim2.new()

frame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true
        dragStart = input.Position
        startPos = frame.Position
    end
end)

frame.InputChanged:Connect(function(input)
    if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
        local delta = input.Position - dragStart
        frame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = false
    end
end)
