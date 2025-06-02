-- 完整可注入的飞行脚本（带音频启动效果）
local TweenService = game:GetService("TweenService")
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")
local SoundService = game:GetService("SoundService")

-- 检查是否已播放过启动效果（确保只播放一次）
if not _G.huangdougaoAudioPlayed then
    _G.huangdougaoAudioPlayed = true
else
    -- 如果已经播放过，直接初始化飞行脚本
    local function initializeFlyScript()
        -- 飞行脚本GUI代码
        local main = Instance.new("ScreenGui")
        local Frame = Instance.new("Frame")
        local up = Instance.new("TextButton")
        local down = Instance.new("TextButton")
        local onof = Instance.new("TextButton")
        local TextLabel = Instance.new("TextLabel")
        local plus = Instance.new("TextButton")
        local speed = Instance.new("TextLabel")
        local mine = Instance.new("TextButton")
        local closebutton = Instance.new("TextButton")
        local mini = Instance.new("TextButton")
        local mini2 = Instance.new("TextButton")
        
        main.Name = "main"
        main.Parent = playerGui
        main.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
        main.ResetOnSpawn = false
        
        Frame.Parent = main
        Frame.BackgroundColor3 = Color3.fromRGB(163, 255, 137)
        Frame.BorderColor3 = Color3.fromRGB(103, 221, 213)
        Frame.Position = UDim2.new(0.100320168, 0, 0.379746825, 0)
        Frame.Size = UDim2.new(0, 190, 0, 57)
        
        up.Name = "上"
        up.Parent = Frame
        up.BackgroundColor3 = Color3.fromRGB(79, 255, 152)
        up.Size = UDim2.new(0, 44, 0, 28)
        up.Font = Enum.Font.SourceSans
        up.Text = "上"
        up.TextColor3 = Color3.fromRGB(0, 0, 0)
        up.TextSize = 14.000
        
        down.Name = "下"
        down.Parent = Frame
        down.BackgroundColor3 = Color3.fromRGB(215, 255, 121)
        down.Position = UDim2.new(0, 0, 0.491228074, 0)
        down.Size = UDim2.new(0, 44, 0, 28)
        down.Font = Enum.Font.SourceSans
        down.Text = "下"
        down.TextColor3 = Color3.fromRGB(0, 0, 0)
        down.TextSize = 14.000
        
        onof.Name = "onof"
        onof.Parent = Frame
        onof.BackgroundColor3 = Color3.fromRGB(255, 249, 74)
        onof.Position = UDim2.new(0.702823281, 0, 0.491228074, 0)
        onof.Size = UDim2.new(0, 56, 0, 28)
        onof.Font = Enum.Font.SourceSans
        onof.Text = "飞起来"
        onof.TextColor3 = Color3.fromRGB(0, 0, 0)
        onof.TextSize = 14.000
        
        TextLabel.Parent = Frame
        TextLabel.BackgroundColor3 = Color3.fromRGB(242, 60, 255)
        TextLabel.Position = UDim2.new(0.469327301, 0, 0, 0)
        TextLabel.Size = UDim2.new(0, 100, 0, 28)
        TextLabel.Font = Enum.Font.SourceSans
        TextLabel.Text = "huangdougao"
        TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
        TextLabel.TextScaled = true
        TextLabel.TextSize = 14.000
        TextLabel.TextWrapped = true
        
        plus.Name = "plus"
        plus.PParent = Frame
        plus.BackgroundColor3 = Color3.fromRGB(133, 145, 255)
        plus.Position = UDim2.new(0.231578946, 0, 0, 0)
        plus.Size = UDim2.new(0, 45, 0, 28)
        plus.Font = Enum.Font.SourceSans
        plus.Text = "+"
        plus.TextColor3 = Color3.fromRGB(0, 0, 0)
        plus.TextScaled = true
        plus.TextSize = 14.000
        plus.TextWrapped = true
        
        speed.Name = "speed"
        speed.Parent = Frame
        speed.BackgroundColor3 = Color3.fromRGB(255, 85, 0)
        speed.Position = UDim2.new(0.468421042, 0, 0.491228074, 0)
        speed.Size = UDim2.new(0, 44, 0, 28)
        speed.Font = Enum.Font.SourceSans
        speed.Text = "1"
        speed.TextColor3 = Color3.fromRGB(0, 0, 0)
        speed.TextScaled = true
        speed.TextSize = 14.000
        speed.TextWrapped = true
        
        mine.Name = "mine"
        mine.Parent = Frame
        mine.BackgroundColor3 = Color3.fromRGB(123, 255, 247)
        mine.Position = UDim2.new(0.231578946, 0, 0.491228074, 0)
        mine.Size = UDim2.new(0, 45, 0, 29)
        mine.Font = Enum.Font.SourceSans
        mine.Text = "-"
        mine.TextColor3 = Color3.fromRGB(0, 0, 0)
        mine.TextScaled = true
        mine.TextSize = 14.000
        mine.TextWrapped = true
        
        closebutton.Name = "Close"
        closebutton.Parent = Frame
        closebutton.BackgroundColor3 = Color3.fromRGB(225, 25, 0)
        closebutton.Font = "SourceSans"
        closebutton.Size = UDim2.new(0, 45, 0, 28)
        closebutton.Text = "关闭"
        closebutton.TextSize = 30
        closebutton.Position = UDim2.new(0, 0, -1, 27)
        
        mini.Name = "minimize"
        mini.Parent = Frame
        mini.BackgroundColor3 = Color3.fromRGB(192, 150, 230)
        mini.Font = "SourceSans"
        mini.Size = UDim2.new(0, 45, 0, 28)
        mini.Text = "最小化"
        mini.TextSize = 30
        mini.Position = UDim2.new(0, 44, -1, 27)
        
        mini2.Name = "minimize2"
        mini2.Parent = Frame
        mini2.BackgroundColor3 = Color3.fromRGB(192, 150, 230)
        mini2.Font = "SourceSans"
        mini2.Size = UDim2.new(0, 45, 0, 28)
        mini2.Text = "最小化"
        mini2.TextSize = 30
        mini2.Position = UDim2.new(0, 44, -1, 57)
        mini2.Visible = false
        
        local speeds = 1
        local speaker = game:GetService("Players").LocalPlayer
        local nowe = false
        
        Frame.Active = true
        Frame.Draggable = true
        
        onof.MouseButton1Down:Connect(function()
            if nowe == true then
                nowe = false
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Climbing, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Flying, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Freefall, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Landed, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Physics, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.PlatformStanding, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Running, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.RunningNoPhysics, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.StrafingNoPhysics, true)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Swimming, true)
                speaker.Character.Humanoid:ChangeState(Enum.HumanoidStateType.RunningNoPhysics)
            else
                nowe = true
                for i = 1, speeds do
                    spawn(function()
                        local hb = game:GetService("RunService").Heartbeat
                        local tpwalking = true
                        local chr = game.Players.LocalPlayer.Character
                        local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")
                        while tpwalking and hb:Wait() and chr and hum and hum.Parent do
                            if hum.MoveDirection.Magnitude > 0 then
                                chr:TranslateBy(hum.MoveDirection)
                            end
                        end
                    end)
                end
                game.Players.LocalPlayer.Character.Animate.Disabled = true
                local Char = game.Players.LocalPlayer.Character
                local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")
                
                for i, v in next, Hum:GetPlayingAnimationTracks() do
                    v:AdjustSpeed(0)
                end
                
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Climbing, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Flying, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Freefall, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Landed, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Physics, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.PlatformStanding, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Running, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.RunningNoPhysics, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.StrafingNoPhysics, false)
                speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Swimming, false)
                speaker.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Swimming)
            end
        end)
        
        local tis
        up.MouseButton1Down:Connect(function()
            tis = up.MouseEnter:Connect(function()
                while tis do
                    wait()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 1, 0)
                end
            end)
        end)
        
        up.MouseLeave:Connect(function()
            if tis then
                tis:Disconnect()
                tis = nil
            end
        end)
        
        local dis
        down.MouseButton1Down:Connect(function()
            dis = down.MouseEnter:Connect(function()
                while dis do
                    wait()
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, -1, 0)
                end
            end)
        end)
        
        down.MouseLeave:Connect(function()
            if dis then
                dis:Disconnect()
                dis = nil
            end
        end)
        
        game:GetService("Players").LocalPlayer.CharacterAdded:Connect(function(char)
            wait(0.7)
            game.Players.LocalPlayer.Character.Humanoid.PlatformStand = false
            game.Players.LocalPlayer.Character.Animate.Disabled = false
        end)
        
        plus.MouseButton1Down:Connect(function()
            speeds = speeds + 1
            speed.Text = speeds
            if nowe == true then
                -- 重新初始化飞行
            end
        end)
        
        mine.MouseButton1Down:Connect(function()
            if speeds == 1 then
                speed.Text = 'flyno1'
                wait(1)
                speed.Text = speeds
            else
                speeds = speeds - 1
                speed.Text = speeds
                if nowe == true then
                    -- 重新初始化飞行
                end
            end
        end)
        
        closebutton.MouseButton1Click:Connect(function()
            main:Destroy()
        end)
        
        mini.MouseButton1Click:Connect(function()
            up.Visible = false
            down.Visible = false
            onof.Visible = false
            plus.Visible = false
            speed.Visible = false
            mine.Visible = false
            mini.Visible = false
            mini2.Visible = true
            Frame.BackgroundTransparency = 1
            closebutton.Position = UDim2.new(0, 0, -1, 57)
        end)
        
        mini2.MouseButton1Click:Connect(function()
            up.Visible = true
            down.Visible = true
            onof.Visible = true
            plus.Visible = true
            speed.Visible = true
            mine.Visible = true
            mini.Visible = true
            mini2.Visible = false
            Frame.BackgroundTransparency = 0
            closebutton.Position = UDim2.new(0, 0, -1, 27)
        end)
    end
    
    initializeFlyScript()
    return
end

-- 创建启动音频
local startupSound = Instance.new("Sound")
startupSound.SoundId = "rbxassetid://139688831958891"
startupSound.Volume = 0.7
startupSound.Parent = SoundService

-- 创建启动动画的GUI
local splashScreenGui = Instance.new("ScreenGui")
splashScreenGui.Name = "SplashScreen"
splashScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
splashScreenGui.ResetOnSpawn = false
splashScreenGui.Parent = playerGui

-- 创建动画图片框
local splashImage = Instance.new("ImageLabel")
splashImage.Name = "SplashImage"
splashImage.BackgroundTransparency = 1
splashImage.Size = UDim2.new(0, 300, 0, 300)
splashImage.Position = UDim2.new(0.5, 0, 0, -310)
splashImage.AnchorPoint = Vector2.new(0.5, 0)
splashImage.Image = "rbxassetid://74629553034096"
splashImage.Parent = splashScreenGui

-- 初始化原始飞行脚本的标志
local flyScriptInitialized = false

-- 创建原始飞行脚本的函数
local function initializeFlyScript()
    if flyScriptInitialized then return end
    flyScriptInitialized = true

    -- 飞行脚本GUI代码（完整版）
    local main = Instance.new("ScreenGui")
    local Frame = Instance.new("Frame")
    local up = Instance.new("TextButton")
    local down = Instance.new("TextButton")
    local onof = Instance.new("TextButton")
    local TextLabel = Instance.new("TextLabel")
    local plus = Instance.new("TextButton")
    local speed = Instance.new("TextLabel")
    local mine = Instance.new("TextButton")
    local closebutton = Instance.new("TextButton")
    local mini = Instance.new("TextButton")
    local mini2 = Instance.new("TextButton")
    
    main.Name = "main"
    main.Parent = playerGui
    main.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    main.ResetOnSpawn = false
    
    Frame.Parent = main
    Frame.BackgroundColor3 = Color3.fromRGB(163, 255, 137)
    Frame.BBorderColor3 = Color3.fromRGB(103, 221, 213)
    Frame.Position = UDim2.new(0.100320168, 0, 0.379746825, 0)
    Frame.Size = UDim2.new(0, 190, 0, 57)
    
    up.Name = "up"
    up.Parent = Frame
    up.BackgroundColor3 = Color3.fromRGB(79, 255, 152)
    up.Size = UDim2.new(0, 44, 0, 28)
    up.Font = Enum.Font.SourceSans
    up.Text = "up"
    up.TextColor3 = Color3.fromRGB(0, 0, 0)
    up.TextSize = 14.000
    
    down.Name = "down"
    down.PParent = Frame
    down.BackgroundColor3 = Color3.fromRGB(215, 255, 121)
    down.Position = UDim2.new(0, 0, 0.491228074, 0)
    down.Size = UDim2.new(0, 44, 0, 28)
    down.Font = Enum.Font.SourceSans
    down.Text = "down"
    down.TextColor3 = Color3.fromRGB(0, 0, 0)
    down.TextSize = 14.000
    
    onof.Name = "onof"
    onof.PParent = Frame
    onof.BackgroundColor3 = Color3.fromRGB(255, 249, 74)
    onof.Position = UDim2.new(0.702823281, 0, 0.491228074, 0)
    onof.Size = UDim2.new(0, 56, 0, 28)
    onof.Font = Enum.Font.SourceSans
    onof.Text = "飞起来"
    onof.TextColor3 = Color3.fromRGB(0, 0, 0)
    onof.TextSize = 14.000
    
    TextLabel.Parent = Frame
    TextLabel.BackgroundColor3 = Color3.fromRGB(242, 60, 255)
    TextLabel.Position = UDim2.new(0.469327301, 0, 0, 0)
    TextLabel.Size = UDim2.new(0, 100, 0, 28)
    TextLabel.Font = Enum.Font.SourceSans
    TextLabel.Text = "huangdougao"
    TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
    TextLabel.TextScaled = true
    TextLabel.TextSize = 14.000
    TextLabel.TextWrapped = true
    
    plus.Name = "plus"
    plus.PParent = Frame
    plus.BackgroundColor3 = Color3.fromRGB(133, 145, 255)
    plus.Position = UDim2.new(0.231578946, 0, 0, 0)
    plus.Size = UDim2.new(0, 45, 0, 28)
    plus.Font = Enum.Font.SourceSans
    plus.Text = "+"
    plus.TextColor3 = Color3.fromRGB(0, 0, 0)
    plus.TextScaled = true
    plus.TextSize = 14.000
    plus.TextWrapped = true
    
    speed.Name = "speed"
    speed.PParent = Frame
    speed.BackgroundColor3 = Color3.fromRGB(255, 85, 0)
    speed.Position = UDim2.new(0.468421042, 0, 0.491228074, 0)
    speed.Size = UDim2.new(0, 44, 0, 28)
    speed.Font = Enum.Font.SourceSans
    speed.Text = "1"
    speed.TextColor3 = Color3.fromRGB(0, 0, 0)
    speed.TextScaled = true
    speed.TextSize = 14.000
    speed.TextWrapped = true
    
    mine.Name = "mine"
    mine.PParent = Frame
    mine.BackgroundColor3 = Color3.fromRGB(123, 255, 247)
    mine.Position = UDim2.new(0.231578946, 0, 0.491228074, 0)
    mine.Size = UDim2.new(0, 45, 0, 29)
    mine.Font = Enum.Font.SourceSans
    mine.Text = "-"
    mine.TextColor3 = Color3.fromRGB(0, 0, 0)
    mine.TextScaled = true
    mine.TextSize = 14.000
    mine.TextWrapped = true
    
    closebutton.Name = "Close"
    closebutton.PParent = Frame
    closebutton.BackgroundColor3 = Color3.fromRGB(225, 25, 0)
    closebutton.Font = "SourceSans"
    closebutton.Size = UDim2.new(0, 45, 0, 28)
    closebutton.Text = "X"
    closebutton.TextSize = 30
    closebutton.Position = UDim2.new(0, 0, -1, 27)
    
    mini.Name = "minimize"
    mini.Parent = Frame
    mini.BackgroundColor3 = Color3.fromRGB(192, 150, 230)
    mini.Font = "SourceSans"
    mini.Size = UDim2.new(0, 45, 0, 28)
    mini.Text = "T"
    mini.TextSize = 30
    mini.Position = UDim2.new(0, 44, -1, 27)
    
    mini2.Name = "minimize2"
    mini2.Parent = Frame
    mini2.BackgroundColor3 = Color3.fromRGB(192, 150, 230)
    mini2.Font = "SourceSans"
    mini2.Size = UDim2.new(0, 45, 0, 28)
    mini2.Text = "T"
    mini2.TextSize = 30
    mini2.Position = UDim2.new(0, 44, -1, 57)
    mini2.Visible = false
    
    local speeds = 1
    local speaker = game:GetService("Players").LocalPlayer
    local nowe = false
    
    Frame.Active = true
    Frame.Draggable = true
    
    onof.MouseButton1Down:Connect(function()
        if nowe == true then
            nowe = false
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Climbing, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Flying, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Freefall, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Landed, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Physics, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.PlatformStanding, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Running, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.RunningNoPhysics, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.StrafingNoPhysics, true)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Swimming, true)
            speaker.Character.Humanoid:ChangeState(Enum.HumanoidStateType.RunningNoPhysics)
        else
            nowe = true
            for i = 1, speeds do
                spawn(function()
                    local hb = game:GetService("RunService").Heartbeat
                    local tpwalking = true
                    local chr = game.Players.LocalPlayer.Character
                    local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")
                    while tpwalking and hb:Wait() and chr and hum and hum.Parent do
                        if hum.MoveDirection.Magnitude > 0 then
                            chr:TranslateBy(hum.MoveDirection)
                        end
                    end
                end)
            end
            game.Players.LocalPlayer.Character.Animate.Disabled = true
            local Char = game.Players.LocalPlayer.Character
            local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")
            
            for i, v in next, Hum:GetPlayingAnimationTracks() do
                v:AdjustSpeed(0)
            end
            
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Climbing, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Flying, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Freefall, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Landed, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Physics, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.PlatformStanding, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Running, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.RunningNoPhysics, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.StrafingNoPhysics, false)
            speaker.Character.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Swimming, false)
            speaker.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Swimming)
        end
    end)
    
    local tis
    up.MouseButton1Down:Connect(function()
        tis = up.MouseEnter:Connect(function()
            while tis do
                wait()
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 1, 0)
            end
        end)
    end)
    
    up.MouseLeave:Connect(function()
        if tis then
            tis:Disconnect()
            tis = nil
        end
    end)
    
    local dis
    down.MouseButton1Down:Connect(function()
        dis = down.MouseEnter:Connect(function()
            while dis do
                wait()
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, -1, 0)
            end
        end)
    end)
    
    down.MouseLeave:Connect(function()
        if dis then
            dis:Disconnect()
            dis = nil
        end
    end)
    
    game:GetService("Players").LocalPlayer.CharacterAdded:Connect(function(char)
        wait(0.7)
        game.Players.LocalPlayer.Character.Humanoid.PlatformStand = false
        game.Players.LocalPlayer.Character.Animate.Disabled = false
    end)
    
    plus.MouseButton1Down:Connect(function()
        speeds = speeds + 1
        speed.Text = speeds
        if nowe == true then
            -- 重新初始化飞行
        end
    end)
    
    mine.MouseButton1Down:Connect(function()
        if speeds == 1 then
            speed.Text = 'flyno1'
            wait(1)
            speed.Text = speeds
        else
            speeds = speeds - 1
            speed.Text = speeds
            if nowe == true then
                -- 重新初始化飞行
            end
        end
    end)
    
    closebutton.MouseButton1Click:Connect(function()
        main:Destroy()
    end)
    
    mini.MouseButton1Click:Connect(function()
        up.Visible = false
        down.Visible = false
        onof.Visible = false
        plus.Visible = false
        speed.Visible = false
        mine.Visible = false
        mini.Visible = false
        mini2.Visible = true
        Frame.BackgroundTransparency = 1
        closebutton.Position = UDim2.new(0, 0, -1, 57)
    end)
    
    mini2.MouseButton1Click:Connect(function()
        up.Visible = true
        down.Visible = true
        onof.Visible = true
        plus.Visible = true
        speed.Visible = true
        mine.Visible = true
        mini.Visible = true
        mini2.Visible = false
        Frame.BackgroundTransparency = 0
        closebutton.Position = UDim2.new(0, 0, -1, 27)
    end)
end

-- 启动动画和音频函数
local function playStartAnimation()
    -- 播放音频
    startupSound:Play()
    
    -- 从上方滑入动画
    local slideIn = TweenService:Create(
        splashImage,
        TweenInfo.new(1.2, Enum.EasingStyle.Quint, Enum.EasingDirection.Out),
        {Position = UDim2.new(0.5, 0, 0.4, 0)}
    )
    slideIn:Play()
    
    -- 等待动画完成并初始化飞行脚本
    slideIn.Completed:Wait()
    initializeFlyScript()
    
    -- 等待2秒展示动画
    wait(2)
    
    -- 从下方滑出动画
    local slideOut = TweenService:Create(
        splashImage,
        TweenInfo.new(1, Enum.EasingStyle.Quint, Enum.EasingDirection.In),
        {Position = UDim2.new(0.5, 0, 1.5, 0)}
    )
    slideOut:Play()
    
    -- 动画完成后移除启动界面和音频
    slideOut.Completed:Connect(function()
        startupSound:Destroy()
        splashScreenGui:Destroy()
    end)
end

-- 播放启动动画和音频
playStartAnimation()

-- 发送通知
game:GetService("StarterGui"):SetCore("SendNotification", { 
    Title = "huangdougao",
    Text = "欢迎使用此脚本uwu～",
    Icon = "rbxthumb://type=Asset&id=5107182114&w=150&h=150",
    Duration = 5
})
