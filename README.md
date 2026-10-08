-- LocalScript (ponlo en StarterGui)

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Crear el ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "HackMenuGui"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

-- ========== BOTÓN ABRIR ==========
local openButton = Instance.new("TextButton")
openButton.Name = "OpenButton"
openButton.Size = UDim2.new(0, 140, 0, 50)
openButton.Position = UDim2.new(0, 20, 0.5, -25)
openButton.BackgroundColor3 = Color3.fromRGB(0, 170, 80)
openButton.Text = "ABRIR"
openButton.TextColor3 = Color3.fromRGB(255, 255, 255)
openButton.Font = Enum.Font.GothamBold
openButton.TextSize = 20
openButton.Parent = screenGui

local openCorner = Instance.new("UICorner")
openCorner.CornerRadius = UDim.new(0, 10)
openCorner.Parent = openButton

-- ========== FRAME DEL CÓDIGO ==========
local codeFrame = Instance.new("Frame")
codeFrame.Name = "CodeFrame"
codeFrame.Size = UDim2.new(0, 320, 0, 180)
codeFrame.Position = UDim2.new(0.5, -160, 0.5, -90)
codeFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
codeFrame.BorderSizePixel = 0
codeFrame.Visible = false
codeFrame.Parent = screenGui

local codeCorner = Instance.new("UICorner")
codeCorner.CornerRadius = UDim.new(0, 12)
codeCorner.Parent = codeFrame

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundTransparency = 1
title.Text = "🔒 CÓDIGO HACK"
title.TextColor3 = Color3.fromRGB(0, 255, 100)
title.Font = Enum.Font.GothamBold
title.TextSize = 22
title.Parent = codeFrame

local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(0.8, 0, 0, 40)
textBox.Position = UDim2.new(0.1, 0, 0.35, 0)
textBox.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
textBox.TextColor3 = Color3.fromRGB(255, 255, 255)
textBox.PlaceholderText = "Escribe el código..."
textBox.Text = ""
textBox.Font = Enum.Font.Gotham
textBox.TextSize = 18
textBox.ClearTextOnFocus = false
textBox.Parent = codeFrame

local boxCorner = Instance.new("UICorner")
boxCorner.CornerRadius = UDim.new(0, 8)
boxCorner.Parent = textBox

local enterButton = Instance.new("TextButton")
enterButton.Size = UDim2.new(0.8, 0, 0, 40)
enterButton.Position = UDim2.new(0.1, 0, 0.65, 0)
enterButton.BackgroundColor3 = Color3.fromRGB(0, 170, 80)
enterButton.Text = "ENTRAR"
enterButton.TextColor3 = Color3.fromRGB(255, 255, 255)
enterButton.Font = Enum.Font.GothamBold
enterButton.TextSize = 18
enterButton.Parent = codeFrame

local enterCorner = Instance.new("UICorner")
enterCorner.CornerRadius = UDim.new(0, 8)
enterCorner.Parent = enterButton

-- ========== MENÚ HACK ==========
local hackFrame = Instance.new("Frame")
hackFrame.Name = "HackFrame"
hackFrame.Size = UDim2.new(0, 350, 0, 380)
hackFrame.Position = UDim2.new(0.5, -175, 0.5, -190)
hackFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
hackFrame.BorderSizePixel = 0
hackFrame.Visible = false
hackFrame.Parent = screenGui

local hackCorner = Instance.new("UICorner")
hackCorner.CornerRadius = UDim.new(0, 12)
hackCorner.Parent = hackFrame

local hackTitle = Instance.new("TextLabel")
hackTitle.Size = UDim2.new(1, 0, 0, 45)
hackTitle.BackgroundTransparency = 1
hackTitle.Text = "⚡ MENÚ HACK"
hackTitle.TextColor3 = Color3.fromRGB(0, 255, 100)
hackTitle.Font = Enum.Font.GothamBold
hackTitle.TextSize = 24
hackTitle.Parent = hackFrame

local function createButton(text, posY, color)
        local btn = Instance.new("TextButton")
        btn.Size = UDim2.new(0.8, 0, 0, 40)
        btn.Position = UDim2.new(0.1, 0, posY, 0)
        btn.BackgroundColor3 = color or Color3.fromRGB(40, 40, 40)
        btn.Text = text
        btn.TextColor3 = Color3.fromRGB(255, 255, 255)
        btn.Font = Enum.Font.GothamBold
        btn.TextSize = 16
        btn.Parent = hackFrame

        local corner = Instance.new("UICorner")
        corner.CornerRadius = UDim.new(0, 8)
        corner.Parent = btn

        return btn
end

local speedButton = createButton("1 - SPEED", 0.15, Color3.fromRGB(0, 140, 255))
local noclipButton = createButton("2 - NOCLIP", 0.28, Color3.fromRGB(180, 0, 255))
local flyButton = createButton("3 - FLY", 0.41, Color3.fromRGB(255, 140, 0))
local closeButton = createButton("SALIR", 0.70, Color3.fromRGB(200, 50, 50))

-- ========== BOTONES DE VUELO PARA MÓVIL ==========
local upButton = Instance.new("TextButton")
upButton.Size = UDim2.new(0, 60, 0, 60)
upButton.Position = UDim2.new(1, -140, 1, -150)
upButton.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
upButton.Text = "↑"
upButton.TextColor3 = Color3.fromRGB(255, 255, 255)
upButton.Font = Enum.Font.GothamBold
upButton.TextSize = 28
upButton.Visible = false
upButton.Parent = screenGui

local upCorner = Instance.new("UICorner")
upCorner.CornerRadius = UDim.new(0, 12)
upCorner.Parent = upButton

local downButton = Instance.new("TextButton")
downButton.Size = UDim2.new(0, 60, 0, 60)
downButton.Position = UDim2.new(1, -140, 1, -80)
downButton.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
downButton.Text = "↓"
downButton.TextColor3 = Color3.fromRGB(255, 255, 255)
downButton.Font = Enum.Font.GothamBold
downButton.TextSize = 28
downButton.Visible = false
downButton.Parent = screenGui

local downCorner = Instance.new("UICorner")
downCorner.CornerRadius = UDim.new(0, 12)
downCorner.Parent = downButton

-- ========== VARIABLES ==========
local CODIGO_CORRECTO = "1234"
local speedActivo = false
local noclipActivo = false
local flyActivo = false
local noclipConnection = nil
local flyConnection = nil
local bodyVelocity = nil
local subiendo = false
local bajando = false

-- ========== FUNCIONES ==========

local function toggleSpeed()
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        if not humanoid then return end

        speedActivo = not speedActivo

        if speedActivo then
                humanoid.WalkSpeed = 50
                speedButton.Text = "1 - SPEED (ON)"
                speedButton.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
        else
                humanoid.WalkSpeed = 16
                speedButton.Text = "1 - SPEED"
                speedButton.BackgroundColor3 = Color3.fromRGB(0, 140, 255)
        end
end

local function toggleNoclip()
        local character = player.Character
        if not character then return end

        noclipActivo = not noclipActivo

        if noclipActivo then
                noclipButton.Text = "2 - NOCLIP (ON)"
                noclipButton.BackgroundColor3 = Color3.fromRGB(0, 200, 100)

                noclipConnection = RunService.Stepped:Connect(function()
                        for _, part in pairs(character:GetDescendants()) do
                                if part:IsA("BasePart") then
                                        part.CanCollide = false
                                end
                        end
                end)
        else
                noclipButton.Text = "2 - NOCLIP"
                noclipButton.BackgroundColor3 = Color3.fromRGB(180, 0, 255)

                if noclipConnection then
                        noclipConnection:Disconnect()
                        noclipConnection = nil
                end

                for _, part in pairs(character:GetDescendants()) do
                        if part:IsA("BasePart") and part.Name \~= "HumanoidRootPart" then
                                part.CanCollide = true
                        end
                end
        end
end

local function toggleFly()
        local character = player.Character
        if not character then return end
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        local rootPart = character:FindFirstChild("HumanoidRootPart")
        if not humanoid or not rootPart then return end

        flyActivo = not flyActivo

        if flyActivo then
                flyButton.Text = "3 - FLY (ON)"
                flyButton.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
                upButton.Visible = true
                downButton.Visible = true

                bodyVelocity = Instance.new("BodyVelocity")
                bodyVelocity.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                bodyVelocity.Velocity = Vector3.new(0, 0, 0)
                bodyVelocity.Parent = rootPart

                humanoid.PlatformStand = true

                flyConnection = RunService.RenderStepped:Connect(function()
                        local camera = workspace.CurrentCamera
                        local direction = Vector3.new(0, 0, 0)
                        local speed = 50

                        local moveDir = humanoid.MoveDirection
                        if moveDir.Magnitude > 0 then
                                direction = direction + (camera.CFrame.LookVector * moveDir.Z * -1) + (camera.CFrame.RightVector * moveDir.X)
                        end

                        if UserInputService:IsKeyDown(Enum.KeyCode.Space) or subiendo then
                                direction = direction + Vector3.new(0, 1, 0)
                        end
                        if UserInputService:IsKeyDown(Enum.KeyCode.LeftControl) or bajando then
                                direction = direction - Vector3.new(0, 1, 0)
                        end

                        if direction.Magnitude > 0 then
                                bodyVelocity.Velocity = direction.Unit * speed
                        else
                                bodyVelocity.Velocity = Vector3.new(0, 0, 0)
                        end
                end)
        else
                flyButton.Text = "3 - FLY"
                flyButton.BackgroundColor3 = Color3.fromRGB(255, 140, 0)
                upButton.Visible = false
                downButton.Visible = false
                subiendo = false
                bajando = false

                if flyConnection then
                        flyConnection:Disconnect()
                        flyConnection = nil
                end

                if bodyVelocity then
                        bodyVelocity:Destroy()
                        bodyVelocity = nil
                end

                humanoid.PlatformStand = false
        end
end

-- Botones de subir/bajar (móvil)
upButton.MouseButton1Down:Connect(function()
        subiendo = true
end)
upButton.MouseButton1Up:Connect(function()
        subiendo = false
end)

downButton.MouseButton1Down:Connect(function()
        bajando = true
end)
downButton.MouseButton1Up:Connect(function()
        bajando = false
end)

-- Conectar botones
speedButton.MouseButton1Click:Connect(toggleSpeed)
noclipButton.MouseButton1Click:Connect(toggleNoclip)
flyButton.MouseButton1Click:Connect(toggleFly)

-- Botón ABRIR
openButton.MouseButton1Click:Connect(function()
        codeFrame.Visible = true
        openButton.Visible = false
end)

enterButton.MouseButton1Click:Connect(function()
        if textBox.Text == CODIGO_CORRECTO then
                codeFrame.Visible = false
                hackFrame.Visible = true
                textBox.Text = ""
        else
                textBox.Text = ""
                textBox.PlaceholderText = "Código incorrecto..."
                task.wait(1.2)
                textBox.PlaceholderText = "Escribe el código..."
        end
end)

closeButton.MouseButton1Click:Connect(function()
        hackFrame.Visible = false
        openButton.Visible = true
end)