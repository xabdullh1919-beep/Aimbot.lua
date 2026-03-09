local _K = string.char(51, 78, 74, 48, 89)
local _D = string.char(104, 116, 116, 112, 115, 58, 47, 47, 100, 105, 115, 99, 111, 114, 100, 46, 103, 103, 47, 89, 81, 78, 90, 116, 89, 88, 81, 110)

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local localPlayer = Players.LocalPlayer

local function Notify(title, text)
    local notifyGui = Instance.new("ScreenGui", localPlayer.PlayerGui)
    local nFrame = Instance.new("Frame", notifyGui)
    nFrame.Size = UDim2.new(0, 250, 0, 60)
    nFrame.Position = UDim2.new(1, 30, 0.75, 0) -- Raised position
    nFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
    nFrame.BorderSizePixel = 0
    Instance.new("UICorner", nFrame)
    
    local line = Instance.new("Frame", nFrame)
    line.Size = UDim2.new(0, 4, 1, 0)
    line.BackgroundColor3 = Color3.fromRGB(0, 255, 150)
    line.BorderSizePixel = 0
    Instance.new("UICorner", line)

    local t1 = Instance.new("TextLabel", nFrame)
    t1.Size = UDim2.new(1, -15, 0.5, 0)
    t1.Position = UDim2.new(0, 10, 0, 5)
    t1.Text = title
    t1.TextColor3 = Color3.new(1, 1, 1)
    t1.Font = Enum.Font.GothamBold
    t1.TextSize = 14
    t1.TextXAlignment = "Left"
    t1.BackgroundTransparency = 1

    local t2 = Instance.new("TextLabel", nFrame)
    t2.Size = UDim2.new(1, -15, 0.5, 0)
    t2.Position = UDim2.new(0, 10, 0.4, 5)
    t2.Text = text
    t2.TextColor3 = Color3.fromRGB(200, 200, 200)
    t2.Font = Enum.Font.Gotham
    t2.TextSize = 12
    t2.TextXAlignment = "Left"
    t2.BackgroundTransparency = 1

    nFrame:TweenPosition(UDim2.new(1, -260, 0.75, 0), "Out", "Quart", 0.5, true)
    task.wait(3)
    nFrame:TweenPosition(UDim2.new(1, 30, 0.75, 0), "In", "Quart", 0.5, true)
    task.delay(0.6, function() notifyGui:Destroy() end)
end

local KeyGui = Instance.new("ScreenGui")
KeyGui.Name = "BC9_AUTH"
KeyGui.Parent = localPlayer:WaitForChild("PlayerGui")

local KeyFrame = Instance.new("Frame", KeyGui)
KeyFrame.Size = UDim2.new(0, 300, 0, 180)
KeyFrame.Position = UDim2.new(0.5, -150, 0.5, -90)
KeyFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
KeyFrame.Active = true
KeyFrame.Draggable = true
Instance.new("UICorner", KeyFrame)

local KeyTitle = Instance.new("TextLabel", KeyFrame)
KeyTitle.Size = UDim2.new(1, 0, 0, 40)
KeyTitle.Text = "BC9 HUB - KEY SYSTEM"
KeyTitle.TextColor3 = Color3.new(1, 1, 1)
KeyTitle.Font = Enum.Font.GothamBold
KeyTitle.BackgroundTransparency = 1

local KeyInput = Instance.new("TextBox", KeyFrame)
KeyInput.Size = UDim2.new(0.8, 0, 0, 40)
KeyInput.Position = UDim2.new(0.1, 0, 0.3, 0)
KeyInput.PlaceholderText = "Enter Key Here..."
KeyInput.Text = ""
KeyInput.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
KeyInput.TextColor3 = Color3.new(1, 1, 1)
Instance.new("UICorner", KeyInput)

local SubmitBtn = Instance.new("TextButton", KeyFrame)
SubmitBtn.Size = UDim2.new(0.35, 0, 0, 35)
SubmitBtn.Position = UDim2.new(0.1, 0, 0.65, 0)
SubmitBtn.Text = "SUBMIT"
SubmitBtn.BackgroundColor3 = Color3.fromRGB(0, 150, 0)
SubmitBtn.TextColor3 = Color3.new(1, 1, 1)
Instance.new("UICorner", SubmitBtn)

local DiscordBtn = Instance.new("TextButton", KeyFrame)
DiscordBtn.Size = UDim2.new(0.35, 0, 0, 35)
DiscordBtn.Position = UDim2.new(0.55, 0, 0.65, 0)
DiscordBtn.Text = "COPY DISCORD"
DiscordBtn.BackgroundColor3 = Color3.fromRGB(88, 101, 242)
DiscordBtn.TextColor3 = Color3.new(1, 1, 1)
Instance.new("UICorner", DiscordBtn)

local function StartScript()
	KeyGui:Destroy()
    Notify("BC9 HUB", "Successfully Authenticated!")
    
    local RunService = game:GetService("RunService")
    local camera = workspace.CurrentCamera

    local Settings = {
        Aimbot = false, ESP = false,
        Smoothness = 0.6, MaxStuds = 500,
        TargetPart = "Head", Minimized = false
    }

    local screenGui = Instance.new("ScreenGui")
    screenGui.Name = "BC9_HUB_NEW"
    screenGui.ResetOnSpawn = false
    screenGui.Parent = localPlayer:WaitForChild("PlayerGui")

    local mainFrame = Instance.new("Frame", screenGui)
    mainFrame.Size = UDim2.new(0, 200, 0, 180)
    mainFrame.Position = UDim2.new(0.1, 0, 0.2, 0)
    mainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
    mainFrame.Active = true
    mainFrame.Draggable = true
    mainFrame.ClipsDescendants = true
    Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 10)
    local uiStroke = Instance.new("UIStroke", mainFrame)
    uiStroke.Thickness = 2

    local title = Instance.new("Frame", mainFrame)
    title.Size = UDim2.new(1, 0, 0, 40)
    title.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
    Instance.new("UICorner", title)

    local titleText = Instance.new("TextLabel", title)
    titleText.Size = UDim2.new(1, -40, 1, 0)
    titleText.Position = UDim2.new(0, 10, 0, 0)
    titleText.Text = "BC9 HUB NEW"
    titleText.TextColor3 = Color3.new(1, 1, 1)
    titleText.Font = Enum.Font.GothamBold
    titleText.TextSize = 14
    titleText.BackgroundTransparency = 1
    titleText.TextXAlignment = "Left"

    local minBtn = Instance.new("TextButton", title)
    minBtn.Size = UDim2.new(0, 30, 0, 30)
    minBtn.Position = UDim2.new(1, -35, 0, 5)
    minBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    minBtn.Text = "-"
    minBtn.TextColor3 = Color3.new(1, 1, 1)
    minBtn.Font = "GothamBold"
    minBtn.TextSize = 20
    Instance.new("UICorner", minBtn)

    local container = Instance.new("ScrollingFrame", mainFrame)
    container.Size = UDim2.new(1, -20, 1, -50)
    container.Position = UDim2.new(0, 10, 0, 45)
    container.BackgroundTransparency = 1
    container.ScrollBarThickness = 0
    container.CanvasSize = UDim2.new(0, 0, 1.2, 0)

    local uiList = Instance.new("UIListLayout", container)
    uiList.Padding = UDim.new(0, 10)
    uiList.HorizontalAlignment = "Center"

    minBtn.MouseButton1Click:Connect(function()
        Settings.Minimized = not Settings.Minimized
        if Settings.Minimized then
            mainFrame:TweenSize(UDim2.new(0, 200, 0, 40), "Out", "Quart", 0.3, true)
            minBtn.Text = "+"
            container.Visible = false
        else
            mainFrame:TweenSize(UDim2.new(0, 200, 0, 180), "Out", "Quart", 0.3, true)
            minBtn.Text = "-"
            task.delay(0.1, function() container.Visible = true end)
        end
    end)

    local UpdateVisuals = {}
    local function createBtn(text, keyName, keyCodeText)
        local btn = Instance.new("TextButton", container)
        btn.Size = UDim2.new(1, 0, 0, 35)
        btn.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
        btn.TextColor3 = Color3.new(1, 1, 1)
        btn.Font = "GothamSemibold"
        btn.TextSize = 11
        Instance.new("UICorner", btn)
        local function update()
            btn.Text = text .. " ("..keyCodeText.."): " .. (Settings[keyName] and "ON" or "OFF")
            btn.TextColor3 = Settings[keyName] and Color3.fromRGB(0, 255, 180) or Color3.new(1, 1, 1)
        end
        btn.MouseButton1Click:Connect(function() Settings[keyName] = not Settings[keyName] update() end)
        UpdateVisuals[keyName] = update
        update()
    end

    createBtn("AIMBOT", "Aimbot", "R")
    createBtn("SOLID ESP", "ESP", "E")

    local sLabel = Instance.new("TextLabel", container)
    sLabel.Size = UDim2.new(1, 0, 0, 20)
    sLabel.Text = "Smoothness: " .. string.format("%.1f", Settings.Smoothness)
    sLabel.TextColor3 = Color3.new(1, 1, 1)
    sLabel.BackgroundTransparency = 1
    sLabel.TextSize = 12

    local sBack = Instance.new("TextButton", container)
    sBack.Size = UDim2.new(0.9, 0, 0, 14)
    sBack.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    sBack.Text = ""
    Instance.new("UICorner", sBack)

    local sBar = Instance.new("Frame", sBack)
    sBar.Size = UDim2.new(Settings.Smoothness / 2, 0, 1, 0)
    sBar.BackgroundColor3 = Color3.fromRGB(0, 255, 255)
    Instance.new("UICorner", sBar)

    local function updateSlider()
        sBar.Size = UDim2.new(math.clamp(Settings.Smoothness / 2, 0.01, 1), 0, 1, 0)
        sLabel.Text = "Smoothness: " .. string.format("%.1f", Settings.Smoothness)
    end

    local dragging = false
    sBack.InputBegan:Connect(function(i) if i.UserInputType == Enum.UserInputType.MouseButton1 then dragging = true end end)
    UserInputService.InputEnded:Connect(function(i) if i.UserInputType == Enum.UserInputType.MouseButton1 then dragging = false end end)
    UserInputService.InputChanged:Connect(function(i)
        if dragging and i.UserInputType == Enum.UserInputType.MouseMovement then
            local ratio = math.clamp((i.Position.X - sBack.AbsolutePosition.X) / sBack.AbsoluteSize.X, 0, 1)
            Settings.Smoothness = math.round((ratio * 2) * 10) / 10
            updateSlider()
        end
    end)

    local function IsVisible(targetPart)
        local character = localPlayer.Character
        if not character or not targetPart then return false end
        local rayParams = RaycastParams.new()
        rayParams.FilterType = Enum.RaycastFilterType.Exclude
        rayParams.FilterDescendantsInstances = {character, camera}
        local direction = targetPart.Position - camera.CFrame.Position
        local result = workspace:Raycast(camera.CFrame.Position, direction, rayParams)
        if result then return result.Instance:IsDescendantOf(targetPart.Parent) end
        return true
    end

    local function applyESP(player)
        if player == localPlayer then return end
        local box = Instance.new("BoxHandleAdornment", screenGui)
        box.AlwaysOnTop = true
        box.ZIndex = 10
        box.Size = Vector3.new(4, 6, 1)
        box.Transparency = 0.2
        RunService.RenderStepped:Connect(function()
            if Settings.ESP and player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.Humanoid.Health > 0 then
                if player.Team ~= localPlayer.Team or player.Team == nil then
                    box.Adornee = player.Character.HumanoidRootPart
                    box.Color3 = Color3.fromHSV(tick() % 5 / 5, 1, 1)
                else box.Adornee = nil end
            else box.Adornee = nil end
        end)
    end
    for _, p in pairs(Players:GetPlayers()) do applyESP(p) end
    Players.PlayerAdded:Connect(applyESP)

    RunService.RenderStepped:Connect(function()
        uiStroke.Color = Color3.fromHSV(tick() % 5 / 5, 1, 1)
        if Settings.Aimbot then
            local t = nil local d = Settings.MaxStuds
            for _, p in pairs(Players:GetPlayers()) do
                if p ~= localPlayer and p.Character and p.Character:FindFirstChild("Head") and p.Character.Humanoid.Health > 0 then
                    if p.Team ~= localPlayer.Team or p.Team == nil then
                        local _, on = camera:WorldToViewportPoint(p.Character.Head.Position)
                        if on and IsVisible(p.Character.Head) then
                            local m = (localPlayer.Character.HumanoidRootPart.Position - p.Character.Head.Position).Magnitude
                            if m < d then t = p.Character.Head d = m end
                        end
                    end
                end
            end
            if t then 
                camera.CFrame = camera.CFrame:Lerp(CFrame.lookAt(camera.CFrame.Position, t.Position), math.clamp(1.1 - Settings.Smoothness, 0.01, 1)) 
            end
        end
    end)

    UserInputService.InputBegan:Connect(function(input, gpe)
        if gpe then return end
        if input.KeyCode == Enum.KeyCode.R then Settings.Aimbot = not Settings.Aimbot UpdateVisuals.Aimbot()
        elseif input.KeyCode == Enum.KeyCode.E then Settings.ESP = not Settings.ESP UpdateVisuals.ESP()
        elseif input.KeyCode == Enum.KeyCode.RightControl then mainFrame.Visible = not mainFrame.Visible end
    end)
end

SubmitBtn.MouseButton1Click:Connect(function()
	if KeyInput.Text == _K then
		StartScript()
	else
		KeyInput.Text = ""
		KeyInput.PlaceholderText = "RETRY"
        Notify("AUTH ERROR", "Invalid key provided.")
	end
end)

DiscordBtn.MouseButton1Click:Connect(function()
	if setclipboard then setclipboard(_D) Notify("SYSTEM", "Discord link copied!") end
end)
