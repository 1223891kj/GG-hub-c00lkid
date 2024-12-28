-- Configurações do Hub
local hubName = "GG Hub"
local buttonColor = Color3.fromRGB(255, 0, 0) -- Vermelho
local espColor = Color3.fromRGB(255, 255, 0) -- Amarelo
local backgroundColor = Color3.fromRGB(0, 0, 0) -- Preto
local optionColor = Color3.fromRGB(255, 0, 0) -- Vermelho

-- Função para criar o botão de abrir/fechar o Hub
local function createToggleButton()
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0, 50, 0, 50)
    button.Position = UDim2.new(0, 10, 0, 10)
    button.BackgroundColor3 = buttonColor
    button.Text = ""
    button.Parent = game.CoreGui
    return button
end

-- Função para criar o Hub
local function createHub()
    local hub = Instance.new("ScreenGui")
    hub.Name = hubName
    hub.Parent = game.CoreGui

    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(0, 300, 0, 400)
    frame.Position = UDim2.new(0.5, -150, 0.5, -200)
    frame.BackgroundColor3 = backgroundColor
    frame.Parent = hub

    local title = Instance.new("TextLabel")
    title.Size = UDim2.new(1, 0, 0, 50)
    title.BackgroundColor3 = backgroundColor
    title.TextColor3 = optionColor
    title.Text = hubName
    title.Parent = frame

    local playerListButton = Instance.new("TextButton")
    playerListButton.Size = UDim2.new(1, -20, 0, 50)
    playerListButton.Position = UDim2.new(0, 10, 0, 60)
    playerListButton.BackgroundColor3 = backgroundColor
    playerListButton.TextColor3 = optionColor
    playerListButton.Text = "Ver Jogadores"
    playerListButton.Parent = frame

    local espButton = Instance.new("TextButton")
    espButton.Size = UDim2.new(1, -20, 0, 50)
    espButton.Position = UDim2.new(0, 10, 0, 120)
    espButton.BackgroundColor3 = backgroundColor
    espButton.TextColor3 = optionColor
    espButton.Text = "ESP"
    espButton.Parent = frame

    local updateButton = Instance.new("TextButton")
    updateButton.Size = UDim2.new(1, -20, 0, 50)
    updateButton.Position = UDim2.new(0, 10, 0, 180)
    updateButton.BackgroundColor3 = backgroundColor
    updateButton.TextColor3 = optionColor
    updateButton.Text = "Atualizar Lista"
    updateButton.Parent = frame

    return hub
end

-- Função para ativar o ESP
local function activateESP()
    for _, player in pairs(game.Players:GetPlayers()) do
        if player ~= game.Players.LocalPlayer then
            local esp = Instance.new("BillboardGui", player.Character.Head)
            esp.Size = UDim2.new(0, 100, 0, 100)
            esp.AlwaysOnTop = true

            local nameLabel = Instance.new("TextLabel", esp)
            nameLabel.Size = UDim2.new(1, 0, 1, 0)
            nameLabel.BackgroundTransparency = 1
            nameLabel.TextColor3 = espColor
            nameLabel.Text = player.Name
        end
    end
end

-- Função para atualizar a lista de jogadores
local function updatePlayerList()
    -- Código para atualizar a lista de jogadores
end

-- Inicialização
local toggleButton = createToggleButton()
local hub = createHub()

toggleButton.MouseButton1Click:Connect(function()
    hub.Enabled = not hub.Enabled
end)

playerListButton.MouseButton1Click:Connect(function()
    -- Código para ver jogadores
end)

espButton.MouseButton1Click:Connect(function()
    activateESP()
end)

updateButton.MouseButton1Click:Connect(function()
    updatePlayerList()
end)

