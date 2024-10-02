-- Script para invocar Sea Beasts em Blox Fruits
-- Este script é apenas um exemplo e deve ser usado com responsabilidade

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local SeaBeastTool = ReplicatedStorage:WaitForChild("SeaBeastTool")

-- Função para invocar Sea Beasts
local function summonSeaBeasts(player)
    if player:FindFirstChild("SeaBeastTool") then
        for i = 1, 3 do
            local seaBeast = SeaBeastTool:Clone()
            seaBeast.Parent = workspace
            seaBeast.Position = player.Character.HumanoidRootPart.Position + Vector3.new(math.random(-50, 50), 0, math.random(-50, 50))
        end
    end
end

-- Criar painel
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Button = Instance.new("TextButton")

ScreenGui.Parent = Players.LocalPlayer:WaitForChild("PlayerGui")
Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0.3, 0, 0.3, 0)
Frame.Position = UDim2.new(0.35, 0, 0.35, 0)
Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Frame.BackgroundTransparency = 0.5

Button.Parent = Frame
Button.Size = UDim2.new(0.8, 0, 0.2, 0)
Button.Position = UDim2.new(0.1, 0, 0.4, 0)
Button.Text = "Invocar Sea Beasts"
Button.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
Button.TextColor3 = Color3.fromRGB(255, 255, 255)

Button.MouseButton1Click:Connect(function()
    summonSeaBeasts(Players.LocalPlayer)
end)
