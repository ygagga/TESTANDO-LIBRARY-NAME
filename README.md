local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/ygagga/My-library-test/refs/heads/main/README.md"))()

-- Inicializar a biblioteca
MyLib:Init()

-- Criar uma janela básica
local TestWindow = MyLib:MakeWindow({
    Name = "MyLib Test Window",
    SaveConfig = false,
    Size = UDim2.new(0, 500, 0, 400),
    Position = UDim2.new(0.5, -250, 0.5, -200)
})

-- Criar um título dentro da janela
local TitleLabel = MyLib.Elements["TextLabel"]({
    Text = "Bem-vindo ao Teste da MyLib",
    TextColor3 = Color3.fromRGB(255, 255, 255),
    TextSize = 24,
    Size = UDim2.new(0, 480, 0, 40),
    Position = UDim2.new(0, 10, 0, 10),
    BackgroundTransparency = 1
})
TitleLabel.Parent = TestWindow

-- Criar um botão de ação dentro da janela
local ActionButton = MyLib.Elements["TextButton"]({
    Text = "Clique aqui!",
    TextSize = 20,
    Size = UDim2.new(0, 200, 0, 50),
    Position = UDim2.new(0.5, -100, 0, 100),
    BackgroundColor3 = Color3.fromRGB(30, 30, 30),
    TextColor3 = Color3.fromRGB(240, 240, 240)
})
ActionButton.Parent = TestWindow

-- Definir função de click para o botão
ActionButton.MouseButton1Click:Connect(function()
    -- Testar a notificação
    MyLib:MakeNotification({
        Name = "Notificação de Teste",
        Content = "Você clicou no botão!",
        Time = 5
    })
end)

-- Criar um slider
local SliderLabel = MyLib.Elements["TextLabel"]({
    Text = "Controle de Volume",
    TextSize = 18,
    TextColor3 = Color3.fromRGB(255, 255, 255),
    Size = UDim2.new(0, 480, 0, 30),
    Position = UDim2.new(0, 10, 0, 200),
    BackgroundTransparency = 1
})
SliderLabel.Parent = TestWindow

local Slider = MyLib.Elements["Slider"]({
    Min = 0,
    Max = 100,
    Size = UDim2.new(0, 480, 0, 40),
    Position = UDim2.new(0, 10, 0, 230)
})
Slider.Parent = TestWindow

-- Exibir uma mensagem quando o valor do slider for alterado
Slider.OnValueChanged:Connect(function(value)
    print("Valor do slider alterado para: " .. value)
end)

-- Criar um campo de texto
local InputFieldLabel = MyLib.Elements["TextLabel"]({
    Text = "Digite seu nome:",
    TextSize = 18,
    TextColor3 = Color3.fromRGB(255, 255, 255),
    Size = UDim2.new(0, 480, 0, 30),
    Position = UDim2.new(0, 10, 0, 280),
    BackgroundTransparency = 1
})
InputFieldLabel.Parent = TestWindow

local InputField = MyLib.Elements["TextBox"]({
    PlaceholderText = "Digite seu nome",
    Size = UDim2.new(0, 480, 0, 40),
    Position = UDim2.new(0, 10, 0, 310),
    TextColor3 = Color3.fromRGB(255, 255, 255),
    BackgroundColor3 = Color3.fromRGB(40, 40, 40),
    TextSize = 18
})
InputField.Parent = TestWindow

InputField.FocusLost:Connect(function(enterPressed)
    if enterPressed then
        print("Nome digitado: " .. InputField.Text)
    end
end)

-- Criar um botão de fechar
local CloseButton = MyLib.Elements["TextButton"]({
    Text = "Fechar",
    TextSize = 20,
    Size = UDim2.new(0, 100, 0, 50),
    Position = UDim2.new(0.5, -50, 1, -60),
    BackgroundColor3 = Color3.fromRGB(180, 50, 50),
    TextColor3 = Color3.fromRGB(255, 255, 255)
})
CloseButton.Parent = TestWindow

CloseButton.MouseButton1Click:Connect(function()
    TestWindow:Destroy()  -- Fecha a janela ao clicar no botão
end)

-- Testar uma animação simples
local function AnimateTest()
    local AnimFrame = MyLib.Elements["Frame"]({
        Size = UDim2.new(0, 50, 0, 50),
        Position = UDim2.new(0.5, -25, 0.5, -25),
        BackgroundColor3 = Color3.fromRGB(0, 255, 0)
    })
    AnimFrame.Parent = MyGui

    local Tween = TweenService:Create(AnimFrame, TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, -1, true), {
        Position = UDim2.new(0.5, -25, 0.5, -100)
    })
    Tween:Play()
end

-- Iniciar animação simples
AnimateTest()
