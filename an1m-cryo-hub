-- Services
local TweenService = game:GetService("TweenService")
local Players = game:GetService("Players")

local localPlayer = Players.LocalPlayer
local playerGui = localPlayer:WaitForChild("PlayerGui")

-- 0. Nettoyage : Supprime l'ancienne interface si elle existe déjà
local GUI_NAME = "CRYO_HUB_INTRO"
local oldGui = playerGui:FindFirstChild(GUI_NAME)
if oldGui then
	oldGui:Destroy()
end

-- Config globale de durée
local ANIMATION_DURATION = 4 -- Durée fixée à 4 secondes

-- 1. Création de l'interface (ScreenGui & CanvasGroup)
local screenGui = Instance.new("ScreenGui")
screenGui.Name = GUI_NAME
screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
screenGui.Parent = playerGui

local startHub = Instance.new("CanvasGroup")
startHub.Name = "Start Hub"
startHub.ZIndex = 10
startHub.BorderSizePixel = 0
startHub.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
startHub.BackgroundTransparency = 1
startHub.AnchorPoint = Vector2.new(0.5, 0.5)
startHub.Position = UDim2.new(0.5, 0, 0.5, 0)
startHub.Size = UDim2.new(1, 0, 1, 0)
startHub.AutomaticSize = Enum.AutomaticSize.XY
startHub.Parent = screenGui

-- 2. Création des Frames "HOME START"
local homeStart1 = Instance.new("Frame")
homeStart1.Name = "HOME START"
homeStart1.BorderSizePixel = 0
homeStart1.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
homeStart1.AnchorPoint = Vector2.new(0.5, 0.5)
homeStart1.Position = UDim2.new(0.5, 0, 0.5, 0)
homeStart1.Size = UDim2.new(0.2, 0, 0.45, 0)
homeStart1.Parent = startHub

local homeStart2 = Instance.new("Frame")
homeStart2.Name = "HOME START"
homeStart2.ZIndex = 0
homeStart2.BorderSizePixel = 0
homeStart2.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
homeStart2.AnchorPoint = Vector2.new(0.5, 0.5)
homeStart2.Position = UDim2.new(0.5, 0, 0.5, 0)
homeStart2.Size = UDim2.new(0.2, 0, 0.45, 0)
homeStart2.Rotation = 45
homeStart2.Parent = startHub

-- 3. Création du titre
local nameLabel = Instance.new("TextLabel")
nameLabel.Name = "name"
nameLabel.Text = "CRYO HUB"
nameLabel.TextSize = 14
nameLabel.TextScaled = true
nameLabel.TextWrapped = true
nameLabel.RichText = true
nameLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
nameLabel.FontFace = Font.new("rbxasset://fonts/families/Creepster.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
nameLabel.BorderSizePixel = 0
nameLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
nameLabel.BackgroundTransparency = 1
nameLabel.AnchorPoint = Vector2.new(0.5, 0.5)
nameLabel.Position = UDim2.new(0.5, 0, 0.5, 0)
nameLabel.Size = UDim2.new(0.2, 0, 0.2, 0)
nameLabel.Parent = startHub

--------------------------------------------------------------------------------
-- Fonctions d'animation
--------------------------------------------------------------------------------

-- Animation pour les Frames
local function animateFadeAndRotate(frame: GuiObject, targetRotation: number, duration: number)
	local tweenInfo = TweenInfo.new(duration, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)

	local tween = TweenService:Create(frame, tweenInfo, {
		Rotation = targetRotation,
		BackgroundTransparency = 1
	})

	for _, child in ipairs(frame:GetDescendants()) do
		if child:IsA("TextLabel") or child:IsA("TextButton") then
			TweenService:Create(child, tweenInfo, { TextTransparency = 1, BackgroundTransparency = 1 }):Play()
		elseif child:IsA("ImageLabel") or child:IsA("ImageButton") then
			TweenService:Create(child, tweenInfo, { ImageTransparency = 1, BackgroundTransparency = 1 }):Play()
		end
	end

	tween:Play()
	return tween
end

-- Animation spécifique pour le TextLabel
local function animateLabel(label: TextLabel, duration: number, targetRotation: number)
	local tweenInfo = TweenInfo.new(duration, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)

	local frameTween = TweenService:Create(label, tweenInfo, {
		Rotation = targetRotation,
		BackgroundTransparency = 1,
		TextTransparency = 1
	})

	frameTween:Play()

	for _, child in ipairs(label:GetDescendants()) do
		if child:IsA("TextLabel") or child:IsA("TextButton") then
			TweenService:Create(child, tweenInfo, {
				Rotation = -targetRotation,
				TextTransparency = 1,
				TextStrokeTransparency = 1,
				BackgroundTransparency = 1
			}):Play()
		elseif child:IsA("ImageLabel") or child:IsA("ImageButton") then
			TweenService:Create(child, tweenInfo, {
				ImageTransparency = 1,
				BackgroundTransparency = 1
			}):Play()
		end
	end

	return frameTween
end

--------------------------------------------------------------------------------
-- Lancement des animations & Nettoyage final
--------------------------------------------------------------------------------

local mainTween = animateFadeAndRotate(homeStart1, 360, ANIMATION_DURATION)
animateFadeAndRotate(homeStart2, 360, ANIMATION_DURATION)
animateLabel(nameLabel, ANIMATION_DURATION, 0)

-- Une fois l'animation principale terminée, on détruit tout le ScreenGui
mainTween.Completed:Connect(function()
	screenGui:Destroy()
end)

return screenGui, require
