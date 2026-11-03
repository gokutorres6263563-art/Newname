
local Players = game:GetService("Players")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "DELTA_BLUE_TRAINING"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

local main = Instance.new("Frame")
main.Size = UDim2.new(0, 300, 0, 300)
main.Position = UDim2.new(0.5, -150, 0.5, -150)
main.BackgroundColor3 = Color3.fromRGB(12, 16, 30)
main.Active = true
main.Draggable = true
main.Parent = gui

local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 12)
corner.Parent = main

local stroke = Instance.new("UIStroke")
stroke.Color = Color3.fromRGB(0, 140, 255)
stroke.Thickness = 2
stroke.Parent = main

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 45)
title.BackgroundColor3 = Color3.fromRGB(0, 75, 160)
title.Text = "DELTA BLUE | TRAINING"
title.TextColor3 = Color3.new(1, 1, 1)
title.TextSize = 16
title.Font = Enum.Font.GothamBold
title.Parent = main

local function createButton(name, y, callback)
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0, 250, 0, 42)
    button.Position = UDim2.new(0, 25, 0, y)
    button.BackgroundColor3 = Color3.fromRGB(20, 40, 75)
    button.TextColor3 = Color3.new(1, 1, 1)
    button.Text = name .. " : OFF"
    button.Font = Enum.Font.GothamBold
    button.TextSize = 14
    button.Parent = main

    local c = Instance.new("UICorner")
    c.CornerRadius = UDim.new(0, 8)
    c.Parent = button

    local enabled = false

    button.MouseButton1Click:Connect(function()
        enabled = not enabled

        button.Text = name .. (enabled and " : ON" or " : OFF")

        button.BackgroundColor3 = enabled
            and Color3.fromRGB(0, 110, 200)
            or Color3.fromRGB(20, 40, 75)

        callback(enabled)
    end)

    return button
end

-- Aim assist visual de entrenamiento
createButton("AIM TRAINING", 65, function(enabled)
    print("Aim Training:", enabled)
end)

-- ESP para objetivos de práctica
local espFolder = Instance.new("Folder")
espFolder.Name = "TrainingESP"
espFolder.Parent = gui

local espEnabled = false

local function updateESP()
    espFolder:ClearAllChildren()

    if not espEnabled then
        return
    end

    local targets = workspace:FindFirstChild("TrainingTargets")
    if not targets then return end

    for _, target in ipairs(targets:GetChildren()) do
        if target:IsA("Model") then
            local highlight = Instance.new("Highlight")
            highlight.FillColor = Color3.fromRGB(0, 140, 255)
            highlight.OutlineColor = Color3.fromRGB(255, 255, 255)
            highlight.Adornee = target
            highlight.Parent = espFolder
        end
    end
end

createButton("ESP TRAINING", 115, function(enabled)
    espEnabled = enabled
    updateESP()
    print("Training ESP:", enabled)
end)

createButton("SENSITIVITY", 165, function(enabled)
    print("Sensitivity:", enabled)
end)

-- Minimizar
local minimized = false

local minimize = Instance.new("TextButton")
minimize.Size = UDim2.new(0, 35, 0, 30)
minimize.Position = UDim2.new(1, -75, 0, 7)
minimize.Text = "-"
minimize.Parent = main

minimize.MouseButton1Click:Connect(function()
    minimized = not minimized

    for _, obj in ipairs(main:GetChildren()) do
        if obj:IsA("TextButton") and obj ~= minimize then
            obj.Visible = not minimized
        end
    end

    main.Size = minimized
        and UDim2.new(0, 300, 0, 45)
        or UDim2.new(0, 300, 0, 300)
end)

-- Cerrar
local close = Instance.new("TextButton")
close.Size = UDim2.new(0, 35, 0, 30)
close.Position = UDim2.new(1, -38, 0, 7)
close.Text = "X"
close.BackgroundColor3 = Color3.fromRGB(180, 30, 45)
close.TextColor3 = Color3.new(1, 1, 1)
close.Parent = main

close.MouseButton1Click:Connect(function()
    gui:Destroy()
end)

print("DELTA BLUE TRAINING cargado")
