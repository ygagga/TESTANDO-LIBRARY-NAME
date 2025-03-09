local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/ygagga/My-library-test/refs/heads/main/README.md"))()

local Window = Library.new("Meu Script") -- Cria a janela principal

local MainTab = Window:Tab("Principal") -- Adiciona uma aba chamada "Principal"

MainTab:Button("Clique aqui", function()
    print("Botão pressionado!") -- Deve imprimir no console quando clicado
end)

MainTab:Toggle("Ativar Modo", function(state)
    print("Toggle ativado:", state) -- Deve imprimir true/false ao alternar
end)
