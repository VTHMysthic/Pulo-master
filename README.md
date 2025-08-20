-- // Script Local Lua Roblox
-- Interface Super Pulo v1.0
-- Feito para todos os executores (copie e cole no executor)

-- Criar ScreenGui
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

-- Variável de toggle interface
local aberto = true

-- Criar botão bola 🛸
local ToggleBtn = Instance.new("TextButton")
ToggleBtn.Parent = ScreenGui
ToggleBtn.Size = UDim2.new(0, 50, 0, 50)
ToggleBtn.Position = UDim2.new(0, 20, 0.5, -25)
ToggleBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
ToggleBtn.Text = "🛸"
ToggleBtn.TextSize = 28
ToggleBtn.TextColor3 = Color3.fromRGB(255,255,255)
ToggleBtn.BorderSizePixel = 2
ToggleBtn.BorderColor3 = Color3.fromRGB(0, 170, 255)
ToggleBtn.Font = Enum.Font.SourceSansBold
ToggleBtn.AutoButtonColor = true
ToggleBtn.ClipsDescendants = true
ToggleBtn.TextStrokeTransparency = 0 -- borda no emoji
ToggleBtn.TextStrokeColor3 = Color3.fromRGB(0,0,0)
ToggleBtn.ZIndex = 10
ToggleBtn.BackgroundTransparency = 0
ToggleBtn.AnchorPoint = Vector2.new(0,0)

ToggleBtn.TextXAlignment = Enum.TextXAlignment.Center
ToggleBtn.TextYAlignment = Enum.TextYAlignment.Center
ToggleBtn.TextWrapped = true
ToggleBtn.TextScaled = true
ToggleBtn.TextStrokeTransparency = 0
ToggleBtn.TextStrokeColor3 = Color3.fromRGB(0,0,0)
ToggleBtn.TextStrokeTransparency = 0

ToggleBtn.UICorner = Instance.new("UICorner", ToggleBtn)
ToggleBtn.UICorner.CornerRadius = UDim.new(1,0)

-- Criar frame principal
local MainFrame = Instance.new("Frame")
MainFrame.Parent = ScreenGui
MainFrame.Size = UDim2.new(0, 300, 0, 180)
MainFrame.Position = UDim2.new(0.5, -150, 0.5, -90)
MainFrame.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
MainFrame.BorderSizePixel = 0

local UICorner = Instance.new("UICorner", MainFrame)
UICorner.CornerRadius = UDim.new(0, 15)

-- Gradient animado
local UIGradient = Instance.new("UIGradient", MainFrame)
UIGradient.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(0,255,255)),
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(0,0,255)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0,0,139))
}
UIGradient.Rotation = 0

-- Animação do degrade
task.spawn(function()
    while task.wait(0.05) do
        UIGradient.Rotation = (UIGradient.Rotation + 1) % 360
    end
end)

-- Título
local Title = Instance.new("TextLabel", MainFrame)
Title.Size = UDim2.new(1,0,0,40)
Title.Position = UDim2.new(0,0,0,0)
Title.BackgroundTransparency = 1
Title.Text = "super pulo v1.0"
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.Font = Enum.Font.Fantasy
Title.TextSize = 26
Title.TextStrokeTransparency = 0
Title.TextStrokeColor3 = Color3.fromRGB(0,0,0)

-- Caixa de texto para força do pulo
local JumpBox = Instance.new("TextBox", MainFrame)
JumpBox.Size = UDim2.new(0.8,0,0,40)
JumpBox.Position = UDim2.new(0.1,0,0.5,-20)
JumpBox.PlaceholderText = "Digite a força do pulo"
JumpBox.Text = ""
JumpBox.Font = Enum.Font.SourceSansBold
JumpBox.TextSize = 18
JumpBox.TextColor3 = Color3.fromRGB(0,0,0)
JumpBox.BackgroundColor3 = Color3.fromRGB(255,255,255)

local CornerJump = Instance.new("UICorner", JumpBox)
CornerJump.CornerRadius = UDim.new(0,10)

-- Botão de aplicar
local ApplyBtn = Instance.new("TextButton", MainFrame)
ApplyBtn.Size = UDim2.new(0.5,0,0,40)
ApplyBtn.Position = UDim2.new(0.25,0,0.8,-20)
ApplyBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
ApplyBtn.Text = "Aplicar Pulo"
ApplyBtn.TextSize = 20
ApplyBtn.TextColor3 = Color3.fromRGB(255,255,255)
ApplyBtn.Font = Enum.Font.SourceSansBold

local CornerApply = Instance.new("UICorner", ApplyBtn)
CornerApply.CornerRadius = UDim.new(0,10)

-- Função aplicar força do pulo
ApplyBtn.MouseButton1Click:Connect(function()
    local valor = tonumber(JumpBox.Text)
    if valor and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
        game.Players.LocalPlayer.Character.Humanoid.UseJumpPower = true
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = valor
    end
end)

-- Função abrir/fechar com botão 🛸
ToggleBtn.MouseButton1Click:Connect(function()
    aberto = not aberto
    MainFrame.Visible = aberto
end)
