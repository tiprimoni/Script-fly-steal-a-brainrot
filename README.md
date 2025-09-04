-- Criar ScreenGui
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UIStroke = Instance.new("UIStroke")
local UICorner = Instance.new("UICorner")
local UIListLayout = Instance.new("UIListLayout")

local Button1 = Instance.new("TextButton")
local Button2 = Instance.new("TextButton")

ScreenGui.Parent = game:GetService("CoreGui")

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Frame.Position = UDim2.new(0.3, 0, 0.3, 0)
Frame.Size = UDim2.new(0, 200, 0, 150)
Frame.Active = true
Frame.Draggable = true

UICorner.Parent = Frame
UIStroke.Parent = Frame
UIStroke.Thickness = 2
UIStroke.Color = Color3.fromRGB(255, 255, 255)

UIListLayout.Parent = Frame
UIListLayout.Padding = UDim.new(0, 5)
UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
UIListLayout.VerticalAlignment = Enum.VerticalAlignment.Top

local function CreateButton(name, parent)
    local btn = Instance.new("TextButton")
    btn.Parent = parent
    btn.Text = name
    btn.Size = UDim2.new(0, 180, 0, 40)
    btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.Font = Enum.Font.SourceSansBold
    btn.TextSize = 18
    local corner = Instance.new("UICorner")
    corner.Parent = btn
    return btn
end

Button1 = CreateButton("Modo Gravidade Zero", Frame)
Button2 = CreateButton("Outro Botão", Frame)

-- BOTÃO 1 → Gravidade 0 + Velocidade Alta
Button1.MouseButton1Click:Connect(function()
    local player = game.Players.LocalPlayer
    local char = player.Character or player.CharacterAdded:Wait()
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    workspace.Gravity = 0
    if humanoid then
        humanoid.WalkSpeed = 200
        humanoid.JumpPower = 100
    end
end)

-- BOTÃO 2 (ainda vazio, só exemplo)
Button2.MouseButton1Click:Connect(function()
    print("Botão 2 clicado")
end)
