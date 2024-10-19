-- Script in StarterGui to create the input box GUI, handle input, and add an exit button

-- Create the ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "InputBoxGui"
screenGui.Parent = game.Players.LocalPlayer.PlayerGui
screenGui.ResetOnSpawn = false

-- Create the main frame for the input box
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 300, 0, 200)
frame.Position = UDim2.new(0.5, -150, 0.5, -100)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Parent = screenGui

-- Create the exit button in the top-left corner
local exitButton = Instance.new("TextButton")
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

-- Create the input label
local label = Instance.new("TextLabel")
label.Size = UDim2.new(0, 280, 0, 50)
label.Position = UDim2.new(0, 10, 0, 10)
label.BackgroundTransparency = 1
label.Text = "Enter 1 or 2 and press 'Submit':"
label.TextColor3 = Color3.fromRGB(255, 255, 255)
label.TextSize = 18
label.Parent = frame

-- Create the TextBox for player input
local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(0, 260, 0, 50)
textBox.Position = UDim2.new(0, 10, 0, 60)
textBox.PlaceholderText = "Enter 1 or 2"
textBox.TextColor3 = Color3.fromRGB(255, 255, 255)
textBox.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
textBox.TextSize = 24
textBox.Parent = frame

-- Create the Submit button
local submitButton = Instance.new("TextButton")
submitButton.Size = UDim2.new(0, 100, 0, 50)
submitButton.Position = UDim2.new(0.5, -50, 0, 130)
submitButton.Text = "Submit"
submitButton.TextColor3 = Color3.fromRGB(255, 255, 255)
submitButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
submitButton.TextSize = 24
submitButton.Parent = frame

-- Function to execute the script based on input
local function executeScript(input)
    if input == "1" then
        -- Execute the first script
        print("lunx on top")
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Alexisisback/Universall/refs/heads/main/Testblade.lua", true))()
        print("by pierre and ....")
    elseif input == "2" then
        -- Execute the second script
        print("fade/lnar on top")
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Akirascripts/Lunar/refs/heads/main/LuanrOnTop"))()
        print("by pierre and xhall/sanc owner")
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
