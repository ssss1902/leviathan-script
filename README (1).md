local Players = game:GetService("Players")

-- Biến trạng thái
local FlySpeed = 3
local AutoFlyEnabled = false
local AutoStartLeviathan = false
local AutoAttackEnabled = false
local SmartComboEnabled = false
local AutoGetHeart = false
local TeleportToOwner = false
local AutoShootTimer = false
local AutoDriveBack = false
local AutoSitPilot = false
local AutoAvoidDamage = false -- Mới
local UseFrozenDimension = false -- Mới

-- UI Setup
local Window = Rayfield:CreateWindow({
    Name = "Banana Cat Hub - Leviathan System",
    LoadingTitle = "Đang tải Leviathan Module...",
    LoadingSubtitle = "by Obii",
    ConfigurationSaving = {
        Enabled = true,
        FolderName = "BananaCatHub",
        FileName = "LeviathanConfig"
    },
    KeySystem = false,
})

local LeviathanTab = Window:CreateTab("🐉 Leviathan", 4483362458)

-- Tốc độ bay
LeviathanTab:CreateSlider({
    Name = "🚀 Tốc độ bay ra đảo Leviathan",
    Range = {1, 10},
    Increment = 1,
    Suffix = "Speed",
    CurrentValue = FlySpeed,
    Callback = function(Value)
        FlySpeed = Value
    end,
    Description = "Điều chỉnh tốc độ bay của tàu bay tới đảo Leviathan."
})

-- Auto bay ra đảo Leviathan
LeviathanTab:CreateToggle({
    Name = "🛫 Tự động bay ra đảo Leviathan",
    CurrentValue = false,
    Callback = function(Value)
        AutoFlyEnabled = Value
    end,
    Description = "Tự động bay đến tọa độ đảo Leviathan khi bật."
})

-- Auto triệu hồi Leviathan
LeviathanTab:CreateToggle({
    Name = "⚔️ Tự động triệu hồi Leviathan",
    CurrentValue = false,
    Callback = function(Value)
        AutoStartLeviathan = Value
    end,
    Description = "Tự động bắt đầu sự kiện Leviathan khi bạn đã sẵn sàng."
})

-- Auto tấn công Leviathan
LeviathanTab:CreateToggle({
    Name = "🧨 Tự động tấn công Leviathan",
    CurrentValue = false,
    Callback = function(Value)
        AutoAttackEnabled = Value
    end,
    Description = "Tự động spam chiêu hoặc combo vào Leviathan."
})

-- Combo thông minh + né đòn
LeviathanTab:CreateToggle({
    Name = "🤺 Combo thông minh + Né đòn",
    CurrentValue = false,
    Callback = function(Value)
        SmartComboEnabled = Value
    end,
    Description = "Kết hợp combo mạnh và tự tránh skill của Leviathan (dạng evasive)."
})

-- Tự động né sát thương (mới)
LeviathanTab:CreateToggle({
    Name = "🛡️ Auto tránh sát thương",
    CurrentValue = false,
    Callback = function(Value)
        AutoAvoidDamage = Value
    end,
    Description = "Tự động lùi hoặc dash khi Leviathan chuẩn bị tấn công."
})

-- Tự động lấy Heart khi chết
LeviathanTab:CreateToggle({
    Name = "❤️ Auto lấy Leviathan Heart khi chết",
    CurrentValue = false,
    Callback = function(Value)
        AutoGetHeart = Value
    end,
    Description = "Khi chết, sẽ tự tìm Heart và nhặt lại ngay."
})

-- Teleport đến tàu của chủ được chọn
LeviathanTab:CreateToggle({
    Name = "🧍‍♂️ Teleport đến tàu của chủ được chọn",
    CurrentValue = false,
    Callback = function(Value)
        TeleportToOwner = Value
    end,
    Description = "Dịch chuyển bạn đến vị trí của chủ tàu đã chọn trong dropdown."
})

-- Auto ngồi ghế lái (mới)
LeviathanTab:CreateToggle({
    Name = "🪑 Auto ngồi ghế lái tàu",
    CurrentValue = false,
    Callback = function(Value)
        AutoSitPilot = Value
    end,
    Description = "Khi dịch chuyển đến tàu, tự động ngồi vào ghế điều khiển."
})

-- Auto bắn khi gần hết giờ
LeviathanTab:CreateToggle({
    Name = "🕒 Tự bắn khi gần hết thời gian",
    CurrentValue = false,
    Callback = function(Value)
        AutoShootTimer = Value
    end,
    Description = "Nếu Leviathan sắp hết giờ, tự bắn tất cả kỹ năng dồn damage."
})

-- Tự lái về đảo Tiki / Hydra
LeviathanTab:CreateToggle({
    Name = "🏝️ Tự lái về đảo Tiki hoặc Hydra",
    CurrentValue = false,
    Callback = function(Value)
        AutoDriveBack = Value
    end,
    Description = "Sau sự kiện, tự quay lại đảo Tiki hoặc Hydra Island."
})

-- Teleport vào Frozen Dimension (mới)
LeviathanTab:CreateToggle({
    Name = "❄️ Teleport vào Frozen Dimension",
    CurrentValue = false,
    Callback = function(Value)
        UseFrozenDimension = Value
    end,
    Description = "Dành cho nhiệm vụ đặc biệt có liên quan đến Frozen Dimension."
})
