# Flshty-Hub

Bibliothèque Lua créée par Flashtynooo.

--------------------------------------------------------------------------------------------------------------------------------------------------------------
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Flashtynooo/Flshty-Hub/refs/heads/main/lib"))()

local Window = Library:CreateWindow("Flshty Hub")

-- Catégorie 1
local MainTab = Window:AddCategory("Main")

MainTab:AddButton("instant button", function()
    print("Action exécutée !")
end)

MainTab:AddToggle("Toggle off", false, function(state)
    print("TEST")
end)

-- Catégorie 2
local MiscTab = Window:AddCategory("Categories")

MiscTab:AddToggle("Toggle button on", true, function(state)
    print("TEST")
end)
--------------------------------------------------------------------------------------------------------------------------------------------------------------

## Licence

Ce projet est disponible gratuitement pour utilisation.

Le code source peut être consulté, mais toute modification, redistribution,
réutilisation d'une partie du code dans un autre projet est interdite
sans autorisation de l'auteur.

© 2026 Flashtynooo - Tous droits réservés.s
