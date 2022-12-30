 Visual  UI library

### README
This document is made for a ScriptHub im making so feel free to use it

## creating the Library
```lua
local Library = loadstring(game:HttpGet('https://raw.githubusercontent.com/Duhscriptposter/visual2/main/Source2.lua', true))()
```

## Creating a Window
```lua
local Window = Library:CreateWindow('Title', 'Description', 'Description', 'rbxassetid://10618928818', false, 'ConfigText', 'Default')
```

## Creating a Tab
```lua
local Tab = Window:CreateTab('tab', true, 'rbxassetid://3926305904', Vector2.new(524, 44), Vector2.new(36, 36))
```

## Creating a Section
```lua
local Section = Tab:CreateSection('Section')
```

## Creating a Label
```lua
local Label = Section:CreateLabel('Label')
```

## Creating a Paragraph
```lua
local Paragraph = Section:CreateParagraph('Paragraph', 'Content')
```

## Creating a Button
```lua
local Button = Section:CreateButton('Button', function()
    print('Button Pressed')
end)
```

## Creating a Slider
```lua
local Slider = Section:CreateSlider('Slider', 1, 100, 50, Color3.fromRGB(0, 125, 255), function(Value)
    print(Value)
end)
```

## Creating a TextBox
```lua
local Textbox = Section:CreateTextbox('Textbox', 'Input', function(Value)
    print(Value)
end)
```

## Creating a KeyBind
```lua
local Keybind = Section:CreateKeybind('Keybind', 'F', function()
    print('Key Pressed')
end)
```

## Creating a Toggle
```lua
local Toggle = Section:CreateToggle('Toggle', true, Color3.fromRGB(0, 125, 255), 0.25, function(Value)
    print(Value)
end)
```

## Creating a Dropdown
```lua
local Dropdown = Section:CreateDropdown('Dropdown', {'1', '2', '3', '4', '5'}, '1', 0.25, function(Value)
    print(Value)
end)
```

## Creating a ColourPicker
```lua
local Colorpicker = Section:CreateColorpicker('Colorpicker', Color3.fromRGB(0, 125, 255), 0.25, function(Value)
    print(Value)
end)
```

## Creating a Image
```lua
local Image = Section:CreateImage('Image', 'rbxassetid://10618928818', UDim2.new(0, 200, 0, 200))
```

## Creating Functions
```lua
local DestroyButton = UIFunctions:CreateButton('Destroy UI', function()
    Library:DestroyUI()
end)

local ToggleKeybind = UIFunctions:CreateKeybind('Toggle UI', 'E', function()
    Library:ToggleUI()
end)

local TextboxKeybind = UIFunctions:CreateTextbox('Notification', 'Text', function(Value)
    Library:CreateNotification('Notification', Value, 5)
end)

local TransparencySlider = UIFunctions:CreateSlider('Transparency', 0, 100, 0, Color3.fromRGB(0, 125, 255), function(Value)
    Library:SetTransparency(Value / 100, true)
end)

local TextPromptButton = UIFunctions:CreateButton('Create Text Prompt', function()
    Library:CreatePrompt('Text', 'Prompt Title', 'Prompt Text', 'Alright')
end)

local OneButtonPromptButton = UIFunctions:CreateButton('Create One Button Prompt', function()
    Library:CreatePrompt('OneButton', 'Prompt Title', 'Prompt Text', {
        'Alright',
        function()
            print('Prompt Button Pressed')
        end
    })
end)

local TwoButtonPromptButton = UIFunctions:CreateButton('Create Two Button Prompt', function()
    Library:CreatePrompt('TwoButton', 'Prompt Title', 'Prompt Text', {
        'Button 1',
        function()
            print('Button 1')
        end,
        'Button 2',
        function()
            print('Button 2')
        end
    })
end)

local ConfigSection = LibraryFunctions:CreateSection('Config')

local ConfigNameString = ''
local ConfigName = ConfigSection:CreateTextbox('Config Name', 'Input', function(Value)
    ConfigNameString = Value
end)

local SaveConfigButton = ConfigSection:CreateButton('Save Config', function()
    Library:SaveConfig(ConfigNameString)
end)

local SelectedConfig = ''
local ConfigsDropdown = ConfigSection:CreateDropdown('Configs', Library:GetConfigs(), nil, 0.25, function(Value)
    SelectedConfig = Value
end)

local DeleteConfigButton = ConfigSection:CreateButton('Delete Config', function()
    Library:DeleteConfig(SelectedConfig)
end)

local LoadConfigButton = ConfigSection:CreateButton('Load Config', function()
    Library:LoadConfig(SelectedConfig)
end)

local RefreshConfigsButton = ConfigSection:CreateButton('Refresh', function()
    ConfigsDropdown:UpdateDropdown(Library:GetConfigs())
end)

local ThemesSection = LibraryFunctions:CreateSection('Themes')

local ThemesDropdown = ThemesSection:CreateDropdown('Themes', Library:GetThemes(), nil, 0.25, function(Value)
    Library:ChangeTheme(Value)
end)

local ColorSection = LibraryFunctions:CreateSection('Custom Colors')

for Index, CurrentColor in next, Library:ReturnTheme() do
    ColorSection:CreateColorpicker(Index, CurrentColor, 0.25, function(Color)
        Library:ChangeColor(Index, Color)
    end, {true})
end
```
