--// Script Local Roblox: "O Pulo Master💥"
-- Feito para executores (LocalScript)

-- Serviços
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()
local humanoid = char:WaitForChild("Humanoid")

--// GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "PuloMasterGui"
ScreenGui.Parent = game.CoreGui

-- Janela principal
local MainFrame = Instance.new("Frame")
MainFrame.Size = UDim2.new(0, 300, 0, 180)
MainFrame.Position = UDim2.new(0.5, -150, 0.5, -90)
MainFrame.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
MainFrame.BorderSizePixel = 0
MainFrame.Parent = ScreenGui

-- Gradient animado
local UIGradient = Instance.new("UIGradient", MainFrame)
UIGradient.Rotation = 45
UIGradient.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 255, 255)), -- azul ciano
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(0, 100, 255)), -- azul normal
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 0, 139)) -- azul escuro
}

-- Loop para animar gradiente
task.spawn(function()
    while task.wait(0.05) do
        UIGradient.Rotation = (UIGradient.Rotation + 1) % 360
    end
end)

-- Título
local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0, 50)
Title.BackgroundTransparency = 1
Title.Text = "o pulo master💥"
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.Font = Enum.Font.Cartoon
Title.TextScaled = true
Title.Parent = MainFrame

-- Botão de ativar pulo alto
local JumpButton = Instance.new("TextButton")
JumpButton.Size = UDim2.new(0.8, 0, 0, 40)
JumpButton.Position = UDim2.new(0.1, 0, 0.45, 0)
JumpButton.BackgroundColor3 = Color3.fromRGB(0,0,0)
JumpButton.BackgroundTransparency = 0.3
JumpButton.Text = "Ativar Pulo Alto"
JumpButton.Font = Enum.Font.Cartoon
JumpButton.TextScaled = true
JumpButton.TextColor3 = Color3.fromRGB(255,255,0)
JumpButton.Parent = MainFrame

-- Função do botão de pulo
local jumpActive = false
JumpButton.MouseButton1Click:Connect(function()
    if jumpActive then
        humanoid.UseJumpPower = true
        humanoid.JumpPower = 50 -- normal
        JumpButton.Text = "Ativar Pulo Alto"
        jumpActive = false
    else
        humanoid.UseJumpPower = true
        humanoid.JumpPower = 150 -- alto
        JumpButton.Text = "Desativar Pulo Alto"
        jumpActive = true
    end
end)

-- Botão de abrir/fechar
local ToggleButton = Instance.new("TextButton")
ToggleButton.Size = UDim2.new(0, 120, 0, 40)
ToggleButton.Position = UDim2.new(0.5, -60, 1, 10)
ToggleButton.BackgroundColor3 = Color3.fromRGB(30,30,30)
ToggleButton.Text = "Fechar Menu"
ToggleButton.Font = Enum.Font.Cartoon
ToggleButton.TextScaled = true
ToggleButton.TextColor3 = Color3.fromRGB(255,255,255)
ToggleButton.Parent = MainFrame

-- Função abrir/fechar
local open = true
ToggleButton.MouseButton1Click:Connect(function()
    if open then
        MainFrame.Visible = false
        ToggleButton.Text = "Abrir Menu"
        ToggleButton.Parent = ScreenGui
        ToggleButton.Position = UDim2.new(0.5, -60, 0.9, 0)
        open = false
    else
        MainFrame.Visible = true
        ToggleButton.Text = "Fechar Menu"
        ToggleButton.Parent = MainFrame
        ToggleButton.Position = UDim2.new(0.5, -60, 1, 10)
        open = true
    end
end)
