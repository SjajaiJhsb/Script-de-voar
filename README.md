-- Script de voo para executor de scripts em Roblox

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local mouse = player:GetMouse()

local flying = false
local flySpeed = 50

-- Função para iniciar o voo
local function startFlying()
    flying = true
    humanoid.PlatformStand = true
    while flying do
        humanoid:Move(Vector3.new(0, flySpeed, 0), true)
        wait(0.1)
    end
end

-- Função para parar o voo
local function stopFlying()
    flying = false
    humanoid.PlatformStand = false
end

-- Ativar/desativar voo ao pressionar a tecla "F"
mouse.KeyDown:Connect(function(key)
    if key == "f" then
        if flying then
            stopFlying()
        else
            startFlying()
        end
    end
end)
