local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- 🪟 Interface
local ScreenGui = Instance.new("ScreenGui", LocalPlayer.PlayerGui)
ScreenGui.Name = "StealerUI"

local Frame = Instance.new("Frame", ScreenGui)
Frame.Size = UDim2.new(0, 350, 0, 300)
Frame.Position = UDim2.new(0.02, 0, 0.3, 0)
Frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)

Instance.new("UICorner", Frame).CornerRadius = UDim.new(0, 12)

local Title = Instance.new("TextLabel", Frame)
Title.Size = UDim2.new(1, 0, 0, 40)
Title.BackgroundTransparency = 1
Title.Text = "🍉 Pet & Fruit Stealer - ThiaguinhoTravasRs"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 22

local Status = Instance.new("TextLabel", Frame)
Status.Size = UDim2.new(1, -20, 0, 30)
Status.Position = UDim2.new(0, 10, 0, 50)
Status.BackgroundTransparency = 1
Status.Text = "Status: Aguardando..."
Status.TextColor3 = Color3.fromRGB(200, 200, 200)
Status.Font = Enum.Font.Gotham
Status.TextSize = 16
Status.TextWrapped = true

-- 🔽 Dropdown de Jogadores
local Dropdown = Instance.new("TextButton", Frame)
Dropdown.Size = UDim2.new(0.9, 0, 0, 40)
Dropdown.Position = UDim2.new(0.05, 0, 0, 90)
Dropdown.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Dropdown.Text = "Selecionar Jogador"
Dropdown.TextColor3 = Color3.fromRGB(255, 255, 255)
Dropdown.Font = Enum.Font.GothamBold
Dropdown.TextSize = 16
Instance.new("UICorner", Dropdown).CornerRadius = UDim.new(0, 8)

local SelectedPlayer = nil

-- Frame da lista de jogadores
local PlayerList = Instance.new("Frame", Frame)
PlayerList.Size = UDim2.new(0.9, 0, 0, 120)
PlayerList.Position = UDim2.new(0.05, 0, 0, 130)
PlayerList.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
PlayerList.Visible = false
Instance.new("UICorner", PlayerList).CornerRadius = UDim.new(0, 8)

local UIListLayout = Instance.new("UIListLayout", PlayerList)
UIListLayout.Padding = UDim.new(0, 4)

-- Preencher lista de jogadores
local function UpdatePlayerList()
    PlayerList:ClearAllChildren()
    UIListLayout.Parent = PlayerList

    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= LocalPlayer then
            local Button = Instance.new("TextButton", PlayerList)
            Button.Size = UDim2.new(1, 0, 0, 30)
            Button.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
            Button.Text = player.Name
            Button.TextColor3 = Color3.fromRGB(255, 255, 255)
            Button.Font = Enum.Font.Gotham
            Button.TextSize = 14
            
