getgenv().DeltaMode=true
local f=function(u)return syn and syn.request and syn.request({Url=u,Method="GET"}).Body or http and http.get(u)or game:HttpGet(u,true)end
loadstring(f("https://raw.githubusercontent.com/Binintrozza/yutv2e/main/Yutohub"))()

local Players=game:GetService("Players")
local Tween=game:GetService("TweenService")
local Plr=Players.LocalPlayer
local Gui=Plr:WaitForChild("PlayerGui")

local UI=Instance.new("ScreenGui")
UI.Name="XeroHub"
UI.ResetOnSpawn=false
UI.ZIndexBehavior=Enum.ZIndexBehavior.Sibling
UI.Parent=Gui

local Janela=Instance.new("Frame")
Janela.Size=UDim2.new(0,440,0,540)
Janela.Position=UDim2.new(0.24,0,0.14,0)
Janela.BackgroundColor3=Color3.new(0.05,0.05,0.09)
Janela.BorderSizePixel=0
Janela.Active=true
Janela.Draggable=true
Janela.ClipsDescendants=true
Janela.Parent=UI

local Topo=Instance.new("Frame")
Topo.Size=UDim2.new(1,0,0,44)
Topo.BackgroundColor3=Color3.new(0.22,0.18,0.06)
Topo.BorderSizePixel=0
Topo.Parent=Janela

local BtnMin=Instance.new("TextButton")
BtnMin.Size=UDim2.new(0,34,0,34)
BtnMin.Position=UDim2.new(1,-38,0,5)
BtnMin.BackgroundColor3=Color3.new(0.16,0.26,0.52)
BtnMin.BorderSizePixel=0
BtnMin.Text="-"
BtnMin.Font=Enum.Font.GothamBold
BtnMin.TextColor3=Color3.new(1,1,1)
BtnMin.TextSize=20
BtnMin.AutoButtonColor=false
BtnMin.Parent=Topo

local Menu=Instance.new("ScrollingFrame")
Menu.Size=UDim2.new(0,155,1,-48)
Menu.Position=UDim2.new(0,5,0,46)
Menu.BackgroundColor3=Color3.new(0.07,0.07,0.12)
Menu.BorderSizePixel=0
Menu.CanvasSize=UDim2.new(0,0,0,460,0)
Menu.ScrollBarThickness=3
Menu.ScrollBarImageColor3=Color3.new(0.3,0.3,0.4)
Menu.Parent=Janela

local Conteudo=Instance.new("ScrollingFrame")
Conteudo.Size=UDim2.new(1,-165,1,-48)
Conteudo.Position=UDim2.new(0,160,0,46)
Conteudo.BackgroundColor3=Color3.new(0.06,0.06,0.1)
Conteudo.BorderSizePixel=0
Conteudo.CanvasSize=UDim2.new(0,0,0,620,0)
Conteudo.ScrollBarThickness=3
Conteudo.ScrollBarImageColor3=Color3.new(0.3,0.3,0.4)
Conteudo.Parent=Janela

local BtnAbrir=Instance.new("TextButton")
BtnAbrir.Size=UDim2.new(0,50,0,50)
BtnAbrir.Position=UDim2.new(0,18,0.5,-25)
BtnAbrir.BackgroundColor3=Color3.new(0.16,0.26,0.52)
BtnAbrir.BorderSizePixel=0
BtnAbrir.Text="+"
BtnAbrir.Font=Enum.Font.GothamBold
BtnAbrir.TextColor3=Color3.new(1,1,1)
BtnAbrir.TextSize=24
BtnAbrir.AutoButtonColor=false
BtnAbrir.Visible=false
BtnAbrir.ZIndex=10
BtnAbrir.Parent=UI

local Estado=false
local Tam=Janela.Size

BtnMin.MouseButton1Click:Connect(function()
    Estado=not Estado
    if Estado then
        Tween:Create(Janela,TweenInfo.new(0.2,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),{Size=UDim2.new(0,440,0,44)}):Play()
        Menu.Visible=false
        Conteudo.Visible=false
        BtnAbrir.Visible=true
    else
        Tween:Create(Janela,TweenInfo.new(0.2,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),{Size=Tam}):Play()
        Menu.Visible=true
        Conteudo.Visible=true
        BtnAbrir.Visible=false
    end
end)

BtnAbrir.MouseButton1Click:Connect(function()
    Estado=false
    Tween:Create(Janela,TweenInfo.new(0.2,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),{Size=Tam}):Play()
    Menu.Visible=true
    Conteudo.Visible=true
    BtnAbrir.Visible=false
end)

for i=1,10 do
    local B=Instance.new("TextButton")
    B.Size=UDim2.new(0.94,0,0,42)
    B.Position=UDim2.new(0.03,0,0,(i-1)*46,0)
    B.BackgroundColor3=Color3.new(0.09,0.09,0.15)
    B.BorderSizePixel=0
    B.Text=""
    B.Font=Enum.Font.GothamSemibold
    B.TextColor3=Color3.new(0.92,0.92,0.96)
    B.TextSize=15
    B.AutoButtonColor=false
    B.Parent=Menu
end

local function Toggle(Y:number)
    local Ligado=false
    local B=Instance.new("TextButton")
    B.Size=UDim2.new(0.88,0,0,38)
    B.Position=UDim2.new(0.06,0,0,Y,0)
    B.BackgroundColor3=Color3.new(0.18,0.18,0.22)
    B.BorderSizePixel=0
    B.Text=""
    B.AutoButtonColor=false
    B.MouseButton1Click:Connect(function()
        Ligado=not Ligado
        Tween:Create(B,TweenInfo.new(0.15,Enum.EasingStyle.Sine),{BackgroundColor3=Ligado and Color3.new(0.75,0.58,0.28)or Color3.new(0.18,0.18,0.22)}):Play()
    end)
    B.Parent=Conteudo
end

Toggle(20)Toggle(68)Toggle(116)Toggle(164)Toggle(212)Toggle(260)Toggle(308)Toggle(356)Toggle(404)Toggle(452)
