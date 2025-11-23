local Players = game:GetService("Players")
local StarterGui = game:GetService("StarterGui")
local player = Players.LocalPlayer

-- Criar tela preta
local screenGui = Instance.new("ScreenGui")
screenGui.IgnoreGuiInset = true
screenGui.ResetOnSpawn = false
screenGui.Parent = player:WaitForChild("PlayerGui")

local blackFrame = Instance.new("Frame")
blackFrame.BackgroundColor3 = Color3.new(0, 0, 0)
blackFrame.Size = UDim2.new(1, 0, 1, 0)
blackFrame.Parent = screenGui

-- Desabilitar controles
local function disableControls()
	local controls = require(player.PlayerScripts:WaitForChild("PlayerModule")):GetControls()
	controls:Disable()
end

local function enableControls()
	local controls = require(player.PlayerScripts:WaitForChild("PlayerModule")):GetControls()
	controls:Enable()
end

disableControls()

-- Esperar 4.5 segundos
task.wait(4.5)

-- Ação após o tempo (escolha uma)
--  Kick legítimo:
player:Kick("Você foi desconectado.")

-- Se quiser outra ação, posso trocar: teleporte, reset, morte, fade, etc.