local CoreGui = game:GetService("CoreGui")
local HttpService = game:GetService("HttpService")
local Players = game:GetService("Players")
local MarketplaceService = game:GetService("MarketplaceService")
local VirtualInputManager = game:GetService("VirtualInputManager")
local LocalPlayer = Players.LocalPlayer

-- LINK DISCORD ABANG
local DISCORD_LINK = "https://discord.gg/ZuHqAq7h4"

-- Hapus UI lama jika ada
if CoreGui:FindFirstChild("DeltaModernUI") then CoreGui.DeltaModernUI:Destroy() end
if CoreGui:FindFirstChild("StartMenuUI") then CoreGui.StartMenuUI:Destroy() end
if CoreGui:FindFirstChild("LITEDIRT") then CoreGui.LITEDIRT:Destroy() end
if CoreGui:FindFirstChild("Script by litedirt") then CoreGui["Script by litedirt"]:Destroy() end

local function applyCorner(gui, radius)
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, radius or 6)
    corner.Parent = gui
end

-- ==========================================
-- FUNGSI UNTUK MEMUAT MENU UTAMA SCRIPT
-- ==========================================
local function muatMenuUtama()
    local ScreenGui = Instance.new("ScreenGui")
    ScreenGui.Name = "LITEDIRT"
    ScreenGui.Parent = CoreGui

    local fileName = "Lokasi_TP_Delta.json" 
    local daftarLokasi = {}
    local waktuMulai = os.time() -- Mencatat waktu mulai bermain

    local function simpanData()
        pcall(function() if writefile then writefile(fileName, HttpService:JSONEncode(daftarLokasi)) end end)
    end
    local function muatData()
        pcall(function() if isfile and readfile and isfile(fileName) then daftarLokasi = HttpService:JSONDecode(readfile(fileName)) end end)
    end
    muatData()

    local ToggleBtn = Instance.new("TextButton")
    ToggleBtn.Size = UDim2.new(0, 110, 0, 40)
    ToggleBtn.Position = UDim2.new(0, 10, 0, 10)
    ToggleBtn.Text = "BUKA MENU"
    ToggleBtn.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
    ToggleBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    ToggleBtn.Font = Enum.Font.GothamBold
    ToggleBtn.TextSize = 14
    ToggleBtn.Parent = ScreenGui
    applyCorner(ToggleBtn, 8)

    -- Ukuran menu disesuaikan agar muat fitur Webhook
    local menuWidth, menuHeight = 340, 520 
    local MainFrame = Instance.new("Frame")
    MainFrame.Size = UDim2.new(0, menuWidth, 0, menuHeight)
    MainFrame.Position = UDim2.new(0.5, -170, 0.5, -260)
    MainFrame.BackgroundColor3 = Color3.fromRGB(22, 22, 26)
    MainFrame.Visible = false
    MainFrame.Active = true
    MainFrame.Draggable = true
    MainFrame.Parent = ScreenGui
    applyCorner(MainFrame, 10)

    local TabBar = Instance.new("Frame")
    TabBar.Size = UDim2.new(1, -20, 0, 35)
    TabBar.Position = UDim2.new(0, 10, 0, 10)
    TabBar.BackgroundTransparency = 1
    TabBar.Parent = MainFrame

    local TabTPBtn = Instance.new("TextButton")
    TabTPBtn.Size = UDim2.new(0.5, -5, 1, 0)
    TabTPBtn.Text = "🌍 T E L E P O R T"
    TabTPBtn.BackgroundColor3 = Color3.fromRGB(45, 100, 200)
    TabTPBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    TabTPBtn.Font = Enum.Font.GothamBold
    TabTPBtn.Parent = TabBar
    applyCorner(TabTPBtn, 6)

    local TabSetBtn = Instance.new("TextButton")
    TabSetBtn.Size = UDim2.new(0.5, -5, 1, 0)
    TabSetBtn.Position = UDim2.new(0.5, 5, 0, 0)
    TabSetBtn.Text = "⚙️ S E T T I N G"
    TabSetBtn.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    TabSetBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
    TabSetBtn.Font = Enum.Font.GothamBold
    TabSetBtn.Parent = TabBar
    applyCorner(TabSetBtn, 6)

    -- CONTAINER TELEPORT
    local TPContainer = Instance.new("Frame")
    TPContainer.Size = UDim2.new(1, 0, 1, -95)
    TPContainer.Position = UDim2.new(0, 0, 0, 55)
    TPContainer.BackgroundTransparency = 1
    TPContainer.Parent = MainFrame

    local NameInput = Instance.new("TextBox")
    NameInput.Size = UDim2.new(1, -20, 0, 35)
    NameInput.Position = UDim2.new(0, 10, 0, 0)
    NameInput.PlaceholderText = "ADD NAME LOCATION"
    NameInput.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    NameInput.TextColor3 = Color3.fromRGB(255, 255, 255)
    NameInput.ClearTextOnFocus = false
    NameInput.Parent = TPContainer
    applyCorner(NameInput, 6)

    local CoordInput = Instance.new("TextBox")
    CoordInput.Size = UDim2.new(1, -20, 0, 35)
    CoordInput.Position = UDim2.new(0, 10, 0, 45)
    CoordInput.PlaceholderText = "X, Y, Z (Kordinat)"
    CoordInput.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    CoordInput.TextColor3 = Color3.fromRGB(255, 255, 255)
    CoordInput.ClearTextOnFocus = false
    CoordInput.Parent = TPContainer
    applyCorner(CoordInput, 6)

    local GetPosBtn = Instance.new("TextButton")
    GetPosBtn.Size = UDim2.new(0.5, -15, 0, 35)
    GetPosBtn.Position = UDim2.new(0, 10, 0, 90)
    GetPosBtn.Text = "Create"
    GetPosBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 70)
    GetPosBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    GetPosBtn.Font = Enum.Font.GothamBold
    GetPosBtn.Parent = TPContainer
    applyCorner(GetPosBtn, 6)

    local SaveBtn = Instance.new("TextButton")
    SaveBtn.Size = UDim2.new(0.5, -15, 0, 35)
    SaveBtn.Position = UDim2.new(0.5, 5, 0, 90)
    SaveBtn.Text = "Save"
    SaveBtn.BackgroundColor3 = Color3.fromRGB(40, 160, 100)
    SaveBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    SaveBtn.Font = Enum.Font.GothamBold
    SaveBtn.Parent = TPContainer
    applyCorner(SaveBtn, 6)

    local ScrollList = Instance.new("ScrollingFrame")
    ScrollList.Size = UDim2.new(1, -20, 1, -135)
    ScrollList.Position = UDim2.new(0, 10, 0, 135)
    ScrollList.BackgroundColor3 = Color3.fromRGB(28, 28, 33)
    ScrollList.ScrollBarThickness = 5
    ScrollList.Parent = TPContainer
    applyCorner(ScrollList, 6)

    local ListLayout = Instance.new("UIListLayout")
    ListLayout.Parent = ScrollList
    ListLayout.Padding = UDim.new(0, 5)

    -- CONTAINER SETTING (DIPERBARUI DENGAN FITUR WEBHOOK)
    local SetContainer = Instance.new("ScrollingFrame")
    SetContainer.Size = UDim2.new(1, 0, 1, -95)
    SetContainer.Position = UDim2.new(0, 0, 0, 55)
    SetContainer.BackgroundTransparency = 1
    SetContainer.Visible = false
    SetContainer.ScrollBarThickness = 5
    SetContainer.CanvasSize = UDim2.new(0, 0, 0, 420)
    SetContainer.Parent = MainFrame

    local HoldInput = Instance.new("TextBox")
    HoldInput.Size = UDim2.new(1, -20, 0, 35)
    HoldInput.Position = UDim2.new(0, 10, 0, 5)
    HoldInput.PlaceholderText = "Tahan Auto E (Cth: 1.5s)"
    HoldInput.Text = "1.5" 
    HoldInput.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    HoldInput.TextColor3 = Color3.fromRGB(255, 255, 255)
    HoldInput.ClearTextOnFocus = false
    HoldInput.Parent = SetContainer
    applyCorner(HoldInput, 6)

    local DelayInput = Instance.new("TextBox")
    DelayInput.Size = UDim2.new(1, -20, 0, 35)
    DelayInput.Position = UDim2.new(0, 10, 0, 45)
    DelayInput.PlaceholderText = "Jeda Auto E (Cth: 0.5s)"
    DelayInput.Text = "0.5" 
    DelayInput.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    DelayInput.TextColor3 = Color3.fromRGB(255, 255, 255)
    DelayInput.ClearTextOnFocus = false
    DelayInput.Parent = SetContainer
    applyCorner(DelayInput, 6)

    local AutoEBtn = Instance.new("TextButton")
    AutoEBtn.Size = UDim2.new(1, -20, 0, 40)
    AutoEBtn.Position = UDim2.new(0, 10, 0, 85)
    AutoEBtn.Text = "AUTO E"
    AutoEBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
    AutoEBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    AutoEBtn.Font = Enum.Font.GothamBold
    AutoEBtn.Parent = SetContainer
    applyCorner(AutoEBtn, 6)

    local AutoTPDelayInput = Instance.new("TextBox")
    AutoTPDelayInput.Size = UDim2.new(1, -20, 0, 35)
    AutoTPDelayInput.Position = UDim2.new(0, 10, 0, 135)
    AutoTPDelayInput.PlaceholderText = "AUTO TP MAX IS 2s"
    AutoTPDelayInput.Text = "3" 
    AutoTPDelayInput.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    AutoTPDelayInput.TextColor3 = Color3.fromRGB(255, 255, 255)
    AutoTPDelayInput.ClearTextOnFocus = false
    AutoTPDelayInput.Parent = SetContainer
    applyCorner(AutoTPDelayInput, 6)

    local AutoTPBtn = Instance.new("TextButton")
    AutoTPBtn.Size = UDim2.new(1, -20, 0, 40)
    AutoTPBtn.Position = UDim2.new(0, 10, 0, 175)
    AutoTPBtn.Text = "AUTO TP"
    AutoTPBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
    AutoTPBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    AutoTPBtn.Font = Enum.Font.GothamBold
    AutoTPBtn.Parent = SetContainer
    applyCorner(AutoTPBtn, 6)

    -- TOMBOL PRESET RIDE STORM
    local PresetBtn = Instance.new("TextButton")
    PresetBtn.Size = UDim2.new(1, -20, 0, 40)
    PresetBtn.Position = UDim2.new(0, 10, 0, 225)
    PresetBtn.Text = "Load Preset: Auto Farm Ride Storm"
    PresetBtn.BackgroundColor3 = Color3.fromRGB(150, 75, 200)
    PresetBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    PresetBtn.Font = Enum.Font.GothamBold
    PresetBtn.TextSize = 13
    PresetBtn.Parent = SetContainer
    applyCorner(PresetBtn, 6)

    -- === FITUR WEBHOOK ===
    local WebhookInput = Instance.new("TextBox")
    WebhookInput.Size = UDim2.new(1, -20, 0, 35)
    WebhookInput.Position = UDim2.new(0, 10, 0, 275)
    WebhookInput.PlaceholderText = "Paste Discord Webhook URL di sini..."
    WebhookInput.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    WebhookInput.TextColor3 = Color3.fromRGB(255, 255, 255)
    WebhookInput.ClearTextOnFocus = false
    WebhookInput.Parent = SetContainer
    applyCorner(WebhookInput, 6)

    local HideUserBtn = Instance.new("TextButton")
    HideUserBtn.Size = UDim2.new(1, -20, 0, 35)
    HideUserBtn.Position = UDim2.new(0, 10, 0, 320)
    HideUserBtn.Text = "Hide Username: OFF ❌"
    HideUserBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
    HideUserBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    HideUserBtn.Font = Enum.Font.GothamBold
    HideUserBtn.Parent = SetContainer
    applyCorner(HideUserBtn, 6)

    local hideUsernameStatus = false
    HideUserBtn.MouseButton1Down:Connect(function()
        hideUsernameStatus = not hideUsernameStatus
        if hideUsernameStatus then
            HideUserBtn.Text = "Hide Username: ON ✔️"
            HideUserBtn.BackgroundColor3 = Color3.fromRGB(40, 160, 100)
        else
            HideUserBtn.Text = "Hide Username: OFF ❌"
            HideUserBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
        end
    end)

    local TestWebhookBtn = Instance.new("TextButton")
    TestWebhookBtn.Size = UDim2.new(1, -20, 0, 40)
    TestWebhookBtn.Position = UDim2.new(0, 10, 0, 365)
    TestWebhookBtn.Text = "TEST WEBHOOK INFO"
    TestWebhookBtn.BackgroundColor3 = Color3.fromRGB(45, 120, 200)
    TestWebhookBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    TestWebhookBtn.Font = Enum.Font.GothamBold
    TestWebhookBtn.Parent = SetContainer
    applyCorner(TestWebhookBtn, 6)

    TestWebhookBtn.MouseButton1Down:Connect(function()
        local url = WebhookInput.Text
        if url == "" or not string.match(url, "https://discord.com/api/webhooks/") then
            TestWebhookBtn.Text = "URL Webhook Tidak Valid!"
            task.wait(1.5)
            TestWebhookBtn.Text = "TEST WEBHOOK INFO"
            return
        end

        -- Ambil nama game
        local successGame, gameInfo = pcall(function()
            return MarketplaceService:GetProductInfo(game.PlaceId)
        end)
        local namaGame = successGame and gameInfo.Name or "Unknown Game"

        -- Hitung waktu bermain
        local totalDetik = os.time() - waktuMulai
        local jam = math.floor(totalDetik / 3600)
        local menit = math.floor((totalDetik % 3600) / 60)
        local detik = totalDetik % 60
        local waktuBermainStr = string.format("%d Jam %d Menit %d Detik", jam, menit, detik)

        -- Ambil Nama Player / Sembunyikan
        local namaPlayer = hideUsernameStatus and "||Hidden Username||" or LocalPlayer.Name

        local dataBody = {
            ["content"] = "",
            ["embeds"] = {
                {
                    ["title"] = "📊 LITEDIRT SCRIPT - STATUS",
                    ["color"] = 65280,
                    ["fields"] = {
                        {["name"] = "👤 Player", ["value"] = namaPlayer, ["inline"] = true},
                        {["name"] = "🎮 Game Name", ["value"] = namaGame, ["inline"] = false},
                        {["name"] = "⏱️ Play Time", ["value"] = waktuBermainStr, ["inline"] = false}
                    },
                    ["footer"] = {
                        ["text"] = "Litedirt Hub • " .. os.date("%d/%m/%Y %H:%M:%S")
                    }
                }
            }
        }

        local finalJson = HttpService:JSONEncode(dataBody)
        local requestFunc = syn and syn.request or http_request or request or HttpPost
        
        if requestFunc then
            pcall(function()
                requestFunc({
                    Url = url,
                    Method = "POST",
                    Headers = {["Content-Type"] = "application/json"},
                    Body = finalJson
                })
            end)
            TestWebhookBtn.Text = "Webhook Terkirim! ✅"
            TestWebhookBtn.BackgroundColor3 = Color3.fromRGB(40, 160, 100)
            task.wait(1.5)
            TestWebhookBtn.Text = "TEST WEBHOOK INFO"
            TestWebhookBtn.BackgroundColor3 = Color3.fromRGB(45, 120, 200)
        else
            TestWebhookBtn.Text = "Executor Tidak Support Request!"
            task.wait(1.5)
            TestWebhookBtn.Text = "TEST WEBHOOK INFO"
        end
    end)

    local ResizeFrame = Instance.new("Frame")
    ResizeFrame.Size = UDim2.new(1, 0, 0, 35)
    ResizeFrame.Position = UDim2.new(0, 0, 1, -40)
    ResizeFrame.BackgroundTransparency = 1
    ResizeFrame.Parent = MainFrame

    local MinBtn = Instance.new("TextButton")
    MinBtn.Size = UDim2.new(0.5, -15, 1, 0)
    MinBtn.Position = UDim2.new(0, 10, 0, 0)
    MinBtn.Text = "- Perkecil"
    MinBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 45)
    MinBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
    MinBtn.Font = Enum.Font.GothamBold
    MinBtn.Parent = ResizeFrame
    applyCorner(MinBtn, 6)

    local PlusBtn = Instance.new("TextButton")
    PlusBtn.Size = UDim2.new(0.5, -15, 1, 0)
    PlusBtn.Position = UDim2.new(0.5, 5, 0, 0)
    PlusBtn.Text = "+ Perbesar"
    PlusBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 45)
    PlusBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
    PlusBtn.Font = Enum.Font.GothamBold
    PlusBtn.Parent = ResizeFrame
    applyCorner(PlusBtn, 6)

    -- Fungsi Teleport dengan Anti-Void (Di Bawah Kaki)
    local function teleportKe(x, y, z)
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            local hrp = LocalPlayer.Character.HumanoidRootPart
            hrp.Anchored = true
            hrp.CFrame = CFrame.new(x, y, z)
            
            local platform = Instance.new("Part")
            platform.Size = Vector3.new(15, 1, 15)
            platform.Position = Vector3.new(x, y - 3.5, z)
            platform.Anchored = true
            platform.CanCollide = true
            platform.Transparency = 0.5 
            platform.BrickColor = BrickColor.new("Cyan")
            platform.Parent = workspace
            
            task.delay(1, function()
                if hrp then hrp.Anchored = false end
                if platform then platform:Destroy() end
            end)
        end
    end

    local function perbaruiDaftar()
        for _, item in ipairs(ScrollList:GetChildren()) do
            if item:IsA("Frame") then item:Destroy() end
        end
        local tinggiCanvas = 0
        for index, data in ipairs(daftarLokasi) do
            local ItemFrame = Instance.new("Frame")
            ItemFrame.Size = UDim2.new(1, -10, 0, 35)
            ItemFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 45)
            ItemFrame.Parent = ScrollList
            applyCorner(ItemFrame, 6)
            
            local Judul = Instance.new("TextLabel")
            Judul.Size = UDim2.new(1, -100, 1, 0)
            Judul.Position = UDim2.new(0, 10, 0, 0)
            Judul.BackgroundTransparency = 1
            Judul.Text = data.Nama
            Judul.TextColor3 = Color3.fromRGB(255, 255, 255)
            Judul.TextXAlignment = Enum.TextXAlignment.Left
            Judul.Parent = ItemFrame
            
            local TPBtn = Instance.new("TextButton")
            TPBtn.Size = UDim2.new(0, 40, 0, 25)
            TPBtn.Position = UDim2.new(1, -95, 0, 5)
            TPBtn.Text = "TP"
            TPBtn.BackgroundColor3 = Color3.fromRGB(45, 100, 200)
            TPBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
            TPBtn.Parent = ItemFrame
            applyCorner(TPBtn, 4)
            
            local DelBtn = Instance.new("TextButton")
            DelBtn.Size = UDim2.new(0, 45, 0, 25)
            DelBtn.Position = UDim2.new(1, -50, 0, 5)
            DelBtn.Text = "Hapus"
            DelBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
            DelBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
            DelBtn.Parent = ItemFrame
            applyCorner(DelBtn, 4)
            
            TPBtn.MouseButton1Down:Connect(function() teleportKe(data.X, data.Y, data.Z) end)
            DelBtn.MouseButton1Down:Connect(function()
                table.remove(daftarLokasi, index)
                simpanData()
                perbaruiDaftar()
            end)
            tinggiCanvas = tinggiCanvas + 40
        end
        ScrollList.CanvasSize = UDim2.new(0, 0, 0, tinggiCanvas)
    end

    ToggleBtn.MouseButton1Down:Connect(function()
        MainFrame.Visible = not MainFrame.Visible
        ToggleBtn.Text = MainFrame.Visible and "TUTUP MENU" or "BUKA MENU"
    end)
    TabTPBtn.MouseButton1Down:Connect(function()
        TPContainer.Visible = true; SetContainer.Visible = false
        TabTPBtn.BackgroundColor3 = Color3.fromRGB(45, 100, 200); TabTPBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
        TabSetBtn.BackgroundColor3 = Color3.fromRGB(35, 35, 40); TabSetBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
    end)
    TabSetBtn.MouseButton1Down:Connect(function()
        TPContainer.Visible = false; SetContainer.Visible = true
        TabSetBtn.BackgroundColor3 = Color3.fromRGB(45, 100, 200); TabSetBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
        TabTPBtn.BackgroundColor3 = Color3.fromRGB(35, 35, 40); TabTPBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
    end)

    GetPosBtn.MouseButton1Down:Connect(function()
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            local pos = LocalPlayer.Character.HumanoidRootPart.Position
            CoordInput.Text = string.format("%.1f, %.1f, %.1f", pos.X, pos.Y, pos.Z)
        end
    end)
    
    SaveBtn.MouseButton1Down:Connect(function()
        local nama, kordinat = NameInput.Text, CoordInput.Text
        if nama ~= "" and kordinat ~= "" then
            local split = string.split(kordinat, ",")
            if #split >= 3 then
                table.insert(daftarLokasi, {Nama = nama, X = tonumber(split[1]), Y = tonumber(split[2]), Z = tonumber(split[3])})
                simpanData(); perbaruiDaftar()
                NameInput.Text = ""; CoordInput.Text = ""
            end
        end
    end)

    -- LOGIKA TOMBOL PRESET RIDE STORM
    PresetBtn.MouseButton1Down:Connect(function()
        local dataPreset = {
            {Y = 2078, X = -1587, Z = -1820, Nama = "Ride Storm - 1A"},
            {Y = 2111, X = 13968, Z = 7278, Nama = "Ride Storm - 1B"},
            {Y = 2076, X = -1074, Z = -7919, Nama = "Ride Storm - 2A"},
            {Y = 2231, X = -4278, Z = 22925, Nama = "Ride Storm - 2B"}
        }
        
        for _, loc in ipairs(dataPreset) do
            table.insert(daftarLokasi, {Nama = loc.Nama, X = loc.X, Y = loc.Y, Z = loc.Z})
        end
        
        simpanData()
        perbaruiDaftar()
        
        PresetBtn.Text = "Preset Berhasil Ditam
