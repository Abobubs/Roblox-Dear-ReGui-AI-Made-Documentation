# ReGui

ReGui Source = https://api.lithium.wtf/misc/regui

Merged reference built from:
- original `regui` source for base/default fields
- previous README structure/examples
- GitBook element order

Notes:
- `Base fields` are taken from the original library source.
- Some elements inherit from another element or helper; that is marked explicitly.
- Examples are practical usage snippets.

## Setup
```lua
local ReGui = loadstring(game:HttpGet("<your regui url here>"))()
ReGui:Init()

local Window = ReGui:Window({
    Title = "ReGui Demo",
    Size = UDim2.fromOffset(520, 420)
})

local Canvas = Window:ScrollingCanvas({Fill = true})
```

## GitBook Elements

## Label

Short text display element.

```lua

type Label = {
    Font= 'Inconsolata',
}

```


```lua
Canvas:Label({
    Text = "Hello world"
})
```

## Error

Styled message block for errors or warnings.

```lua

type Error = {
    RichText=true,
    TextWrapped=true,
}

```


```lua
Canvas:Error({
    Text = "Something went wrong"
})
```

## CodeEditor

Embedded syntax-highlighted code editor widget.

```lua

type CodeEditor = {
    Editable=true,
    Fill=true,
    Text= '',
}

```


```lua
local IDEModule = require(...IDEModule)

local EditorTab = TabSelector:CreateTab({
    Name = "Editor"
})

local CodeEditor = IDEModule.CodeFrame.new({
    Editable = false,
    FontSize = 13,
    Colors = SyntaxColors,
    FontFace = TextFont
})

ReGui:ApplyFlags({
    Object = CodeEditor.Gui,
    WindowClass = Window,
    Class = {
        Fill = true,
        Active = true,
        Parent = EditorTab:GetObject(),
        BackgroundTransparency = 1,
    }
})
```

## Button

Standard clickable action button.

```lua

type Button = {
    Text='Button',
    DoubleClick=false,
    Callback=f,
}

```


```lua
Canvas:Button({
    Text = "Click me",
    Callback = function()
        print("clicked")
    end
})
```

## SmallButton

Compact inline action button.

```lua

type SmallButton = {
    Text='Button',
    PaddingTop=UDim.new(),
    PaddingBottom=UDim.new(),
    PaddingLeft=UDim.new(0,2),
    PaddingRight=UDim.new(0,2),
    ColorTag='Button',
    ElementStyle='Button',
    Callback=f,
}

```


```lua
Row:SmallButton({
    Text = "..."
})
```

## RadioButton

Icon-style button for small actions.

```lua

type RadioButton = {
    Callback=f,
}

```


```lua
Canvas:RadioButton({
    Icon = ReGui.Icons.Arrow,
    Callback = function()
        print("pressed")
    end
})
```

## Image

Displays a static image.

```lua

type Image = {
    Image='',
    Callback=f,
}

```


```lua
Canvas:Image({
    Image = 18395893036
})
```

## VideoPlayer

Embeds and controls a video player.

```lua

type VideoPlayer = {
    Video="",
    Callback=f,
}

```


```lua
local Video = Canvas:VideoPlayer({
    Video = 5608327482,
    Looped = true,
    Ratio = 16 / 9,
    RatioAspectType = Enum.AspectType.FitWithinMaxSize,
    RatioAxis = Enum.DominantAxis.Width,
    Size = UDim2.fromScale(1, 1)
})

Video:Play()
```

## Checkbox

Boolean toggle with label.

```lua

type Checkbox = {
    Label= 'Checkbox',
    IsRadio=false,
    Value=false,
    NoAutoTag=true,
    TickedImageSize=UDim2. fromScale(1,1),
    UntickedImageSize=UDim2.fromScale(0,0),
    Callback=f,
    Disabled=false,
}

```


```lua
Canvas:Checkbox({
    Label = "Enabled",
    Value = true
})
```

## Radiobox

Single-choice radio-style toggle.

```lua

type Radiobox = {
    IsRadio=true,
    CornerRadius=UDim.new(1,0),
}

```


```lua
Canvas:Radiobox({
    Label = "Selected",
    Value = true
})
```

## Viewport

3D viewport display element.

```lua

type Viewport = {
    IsRadio=true,
}

```


```lua
Canvas:Viewport({
    Size = UDim2.fromOffset(140, 140)
})
```

## Console

Scrollable output area for log text.

_Not found as a standalone `DefineElement` block in the current source dump._


```lua
Canvas:CodeEditor({
    Text = "print(\"Hello\")",
    Editable = false
})
```

## Region

Basic framed container region.

```lua

type Region = {
    Scroll=false,
    AutomaticSize=Enum.AutomaticSize.Y,
}

```


```lua
local Region = Canvas:Region({
    AutomaticSize = Enum.AutomaticSize.Y
})
Region:Label({ Text = "Inside region" })
```

## List

Vertical container for grouped items.

```lua

type List = {
    Spacing=4,
    HorizontalFlex=Enum. UIFlexAlignment.None,
    VerticalFlex=Enum.UIFlexAlignment.None,
    HorizontalAlignment= Enum.HorizontalAlignment.Left,
    VerticalAlignment=Enum.VerticalAlignment.Top,
    FillDirection=Enum.FillDirection.Horizontal,
}

```


```lua
local List = Canvas:List({
    FillDirection = Enum.FillDirection.Horizontal
})
List:Button({ Text = "A" })
List:Button({ Text = "B" })
```

## CollapsingHeader

Expandable section header with child content.

```lua

type CollapsingHeader = {
    Title= 'Collapsing Header',
    CollapseIcon=aa.Icons.Arrow,
    Collapsed=true,
    Offset=0,
    NoAutoTag=true,
    NoAutoFlags=true,
    IconPadding=UDim.new(0,4),
    Activated=f,
}

```


```lua
local Header = Canvas:CollapsingHeader({
    Title = "Advanced",
    Collapsed = true
})
Header:Label({ Text = "Hidden content" })
```

## TreeNode

Nested expandable tree item.

```lua

type TreeNode = {
    Offset=21,
    IconPadding=UDim.new(0,2),
    TitleBarProperties={Size=UDim2.new(1,0,0,13)},
}

```


```lua
local Node = Canvas:TreeNode({
    Title = "Child 1"
})
Node:Label({ Text = "Nested" })
```

## Separator

Visual divider between sections.

```lua

type Separator = {
    NoAutoTag=true,
    NoAutoTheme=true,
}

```


```lua
Canvas:Separator({
    Text = "Options"
})
```

## Indent

Indented content wrapper.

```lua

type Indent = {
    Offset=15,
    PaddingTop=UDim.new(),
    PaddingBottom=UDim.new(),
    PaddingRight=UDim.new(),
}

```


```lua
local Indent = Canvas:Indent({
    Offset = 15
})
Indent:Label({ Text = "Indented" })
```

## BulletText

Bullet point with text.

```lua

type BulletText = {
}

```


```lua
Canvas:BulletText({
    Rows = {"One", "Two", "Three"}
})
```

## Bullet

Standalone bullet marker.

```lua

type Bullet = {
    Padding=3,
    Icon= aa.Icons.Dot,
    IconSize=UDim2.fromOffset(5,5),
}

```


```lua
local Bullet = Canvas:Bullet()
Bullet:Label({ Text = "Bullet item" })
```

## Row

Horizontal layout container.

```lua

type Row = {
    Spacing=4,
    Expanded=false,
    HorizontalFlex=Enum. UIFlexAlignment.None,
    VerticalFlex=Enum.UIFlexAlignment.None,
}

```


```lua
local Row = Canvas:Row({
    Expanded = true
})
Row:Button({ Text = "Left" })
Row:Button({ Text = "Right" })
```

## SliderInt

Integer slider input.

```lua

type SliderInt = {
    Label='Slider Int',
    ColorTag='Frame',
}

```


```lua
Canvas:SliderInt({
    Label = "Amount",
    Value = 5,
    Minimum = 1,
    Maximum = 32
})
```

## SliderFloat

Float slider input.

```lua

type SliderFloat = {
    Label='Slider Float',
    Format= '%.3f',
    ColorTag='Frame',
}

```


```lua
Canvas:SliderFloat({
    Label = "Ratio",
    Value = 0.5,
    Minimum = 0,
    Maximum = 1,
    Format = "%.3f"
})
```

## SliderEnum

Slider that steps through enum-like values.

```lua

type SliderEnum = {
    Items={},
    Label='Slider Enum',
    Type= 'Snap',
    Minimum=1,
    Maximum=10,
    Value=1,
    Callback=f,
    ColorTag='Frame',
}

```


```lua
Canvas:SliderEnum({
    Label = "Mode",
    Items = {"Fire", "Earth", "Air", "Water"},
    Value = 2
})
```

## SliderColor3

Three-channel slider input for Color3 values.

**Inherits:** `SliderInt3`


```lua

type SliderColor3 = SliderInt3 & {
    Label = 'SliderColor3',
    Callback = f,
    Value = aa.Accent.Light,
    Disabled = false,
    Minimum = {0, 0, 0},
    Maximum = {255, 255, 255, 100},
    BaseInputConfig = {},
    InputConfigs = {
        [1] = {Format = 'R: %.f'},
        [2] = {Format = 'G: %.f'},
        [3] = {Format = 'B: %.f'},
    },
}

-- Value is converted to RGB channels.
-- Layout follows SliderInt3.

```


```lua
Canvas:SliderColor3({
    Label = "Color",
    Value = ReGui.Accent.Light
})
```

## SliderCFrame

XYZ slider group mapped to CFrame values.

**Inherits:** `SliderColor3`


```lua

type SliderCFrame = SliderColor3 & {
    Value = CFrame.new(),
    Minimum = CFrame.new(),
    Maximum = CFrame.new(),
}

-- Uses SliderColor3-style 3-axis layout.
-- Value / Minimum / Maximum are mapped through CFrame position XYZ.

```


```lua
Canvas:SliderCFrame({
    Label = "Position",
    Value = CFrame.new(1, 1, 1),
    Minimum = CFrame.new(0, 0, 0),
    Maximum = CFrame.new(10, 10, 10)
})
```

## SliderProgress

Read-only progress-style slider display.

```lua

type SliderProgress = {
    Label= 'Slider Progress',
    Type='Progress',
    ColorTag='Frame',
}

```


```lua
Canvas:SliderProgress({
    Label = "Progress",
    Value = 8,
    Minimum = 1,
    Maximum = 32
})
```

## DragInt

Integer drag input.

```lua

type DragInt = {
    Format='%.f',
    Label='Drag Int',
    Callback=f,
    Minimum=0,
    Maximum=100,
    ColorTag='Frame',
    Disabled=false,
}

```


```lua
Canvas:DragInt({
    Label = "Drag X",
    Value = 10,
    Minimum = 0,
    Maximum = 100
})
```

## DragFloat

Float drag input.

```lua

type DragFloat = {
    Format='%.3f',
    Label='Drag Float',
    ColorTag= 'Frame',
}

```


```lua
Canvas:DragFloat({
    Label = "Drag Alpha",
    Value = 0.5,
    Minimum = 0,
    Maximum = 1
})
```

## DragColor3

Three-channel drag input for Color3 values.

**Inherits:** `DragInt3`


```lua

type DragColor3 = DragInt3 & {
    Label = 'DragColor3',
    Callback = f,
    Value = aa.Accent.Light,
    Disabled = false,
    Minimum = {0, 0, 0},
    Maximum = {255, 255, 255, 100},
    BaseInputConfig = {},
    InputConfigs = {
        [1] = {Format = 'R: %.f'},
        [2] = {Format = 'G: %.f'},
        [3] = {Format = 'B: %.f'},
    },
}

-- Value is converted to RGB channels.
-- Layout follows DragInt3.

```


```lua
Canvas:DragColor3({
    Label = "Tint",
    Value = ReGui.Accent.Light
})
```

## DragCFrame

XYZ drag group mapped to CFrame values.

**Inherits:** `DragColor3`


```lua

type DragCFrame = DragColor3 & {
    Value = CFrame.new(),
    Minimum = CFrame.new(),
    Maximum = CFrame.new(),
}

-- Uses DragColor3-style 3-axis layout.
-- Value / Minimum / Maximum are mapped through CFrame position XYZ.

```


```lua
Canvas:DragCFrame({
    Label = "Transform",
    Value = CFrame.new(1, 1, 1),
    Minimum = CFrame.new(0, 0, 0),
    Maximum = CFrame.new(10, 10, 10)
})
```

## InputText

Single-line text input.

```lua

type InputText = {
    Value='',
    Placeholder='',
    Label='Input text',
    Callback=f,
    MultiLine=false,
    NoAutoTag=true,
    Disabled=false,
}

```


```lua
Canvas:InputText({
    Label = "Name",
    Value = "Hello"
})
```

## InputTextMultiline

Multi-line text input.

_Not found as a standalone `DefineElement` block in the current source dump._


```lua
Canvas:InputText({
    Label = "Notes",
    MultiLine = true,
    Value = "Line 1\nLine 2"
})
```

## InputInt

Numeric integer input box.

```lua

type InputInt = {
    Value =0,
    Increment=1,
    Placeholder='',
    Label='Input Int',
    Callback=f,
}

```


```lua
Canvas:InputInt({
    Label = "Count",
    Value = 5
})
```

## InputColor3

Three-channel numeric input for Color3 values.

**Inherits:** `InputInt3`


```lua

type InputColor3 = InputInt3 & {
    Label = 'InputColor3',
    Callback = f,
    Value = aa.Accent.Light,
    Disabled = false,
    Minimum = {0, 0, 0},
    Maximum = {255, 255, 255, 100},
    BaseInputConfig = {},
    InputConfigs = {
        [1] = {Format = 'R: %.f'},
        [2] = {Format = 'G: %.f'},
        [3] = {Format = 'B: %.f'},
    },
}

-- Value is converted to RGB channels.
-- Layout follows InputInt3.

```


```lua
Canvas:InputColor3({
    Label = "Color",
    Value = ReGui.Accent.Light
})
```

## InputCFrame

XYZ numeric input group mapped to CFrame values.

**Inherits:** `InputColor3`


```lua

type InputCFrame = InputColor3 & {
    Value = CFrame.new(),
    Minimum = CFrame.new(),
    Maximum = CFrame.new(),
}

-- Uses InputColor3-style 3-axis layout.
-- Value / Minimum / Maximum are mapped through CFrame position XYZ.

```


```lua
Canvas:InputCFrame({
    Label = "Origin",
    Value = CFrame.new(1, 1, 1),
    Minimum = CFrame.new(0, 0, 0),
    Maximum = CFrame.new(10, 10, 10)
})
```

## ProgressBar

Standalone progress bar display.

```lua

type ProgressBar = {
    Label='Progress Bar',
    Type='Progress',
    ReadOnly =true,
    MinValue=0,
    MaxValue=100,
    Format='% i%%',
    Interactable=false,
    ColorTag='Frame',
}

```


```lua
Canvas:ProgressBar({
    Label = "Loading",
    Value = 65
})
```

## Combo

Dropdown-style option selector.

```lua

type Combo = {
    Value='',
    Placeholder='',
    Callback =f,
    Items={},
    Disabled=false,
    WidthFitPreview=false,
    Label='Combo',
}

```


```lua
Canvas:Combo({
    Label = "Preset",
    Items = {"AAAA", "BBBB", "CCCC"},
    Selected = 1
})
```

## Keybind

Keyboard binding picker.

```lua

type Keybind = {
    Label='Keybind',
    ColorTag='Frame',
    Value=nil,
    DeleteKey=Enum.KeyCode.Backspace,
    IgnoreGameProcessed=true,
    Enabled=true,
    Disabled= false,
    Callback=f,
    OnKeybindSet=f,
    OnBlacklistedKeybindSet=f,
    KeyBlacklist={},
    UiPadding=UDim.new(),
    AutomaticSize=Enum.AutomaticSize.None,
    Size=UDim2.new(0.3,0, 0,19),
}

```


```lua
Canvas:Keybind({
    Label = "Open menu",
    KeyBlacklist = {Enum.UserInputType.MouseButton1}
})
```

## PlotHistogram

Simple histogram/plot display.

```lua

type PlotHistogram = {
    ColorTag='Frame',
    Label= 'Histogram',
}

```


```lua
Canvas:PlotHistogram({
    Label = "Histogram",
    Values = {1, 4, 2, 6, 3}
})
```

## Table

Table/grid layout element.

```lua

type Table = {
    VerticalAlignment=Enum .VerticalAlignment.Top,
    RowBackground=false,
    RowBgTransparency=0.87,
    Border=false,
    Spacing=UDim.new(0,4),
}

```


```lua
local Table = Canvas:Table({
    Border = true,
    RowBackground = true,
    MaxColumns = 3
})

local Row = Table:NextRow()
Row:NextColumn():Label({ Text = "A" })
Row:NextColumn():Label({ Text = "B" })
Row:NextColumn():Label({ Text = "C" })
```

## TabSelector

Tab strip that creates canvases per tab.

```lua

type TabSelector = {
    NoTabsBar=false,
    OnActiveTabChange=f,
    OnTabCreate=f,
    OnTabRemove=f,
}

```


```lua
local Tabs = Window:TabSelector()
local Main = Tabs:CreateTab({ Name = "Main" })
Main:Label({ Text = "Hello from tab" })
```

## Window

Top-level draggable window.

```lua

type Window = {
    Theme='DarkTheme',
    NoSelect=false,
    NoTabs=true,
    NoScroll=false,
    Collapsed=false,
    Visible=true,
    AutoSize =false,
    MinimumSize=Vector2.new(160,90),
    OpenOnDoubleClick=true,
    NoAutoTheme=true,
    NoWindowRegistor=false,
    NoBringToFrontOnFocus=false,
    IsDragging=false,
}

```


```lua
local Window = ReGui:Window({
    Title = "ReGui Demo",
    Size = UDim2.fromOffset(520, 420)
})
```

## TabsWindow

Window variant with built-in tab support.

**Inherits:** `Window`


```lua

type TabsWindow = Window & {NoTabs=false,AutoSelectNewTabs=true}

```


```lua
local TabsWindow = ReGui:TabsWindow({
    Title = "Tabs window!",
    Visible = false,
    Size = UDim2.fromOffset(300, 200)
})

for _, Name in {"Avocado", "Broccoli", "Cucumber"} do
    local Tab = TabsWindow:CreateTab({ Name = Name })
    Tab:Label({ Text = `This is the {Name} tab!` })
end
```

## PopupModal

Modal popup window element.

**Inherits:** `Window`


```lua

type PopupModal = Window & {NoAnimation=false,NoCollapse=true,NoClose=true,NoResize=true,NoSelect=true,NoAutoFlags=true,NoWindowRegistor=true,NoScroll=true}

```


```lua
local Modal = Canvas:PopupModal({
    Title = "Delete?"
})

Modal:Label({
    Text = "This operation cannot be undone.",
    TextWrapped = true
})
Modal:Button({
    Text = "Close",
    Callback = function()
        Modal:ClosePopup()
    end
})
```

## Additional core elements from the original file

## Dropdown

Core dropdown/select helper element.

```lua

type Dropdown = {
    ColorTag='PopupCanvas',
    Disabled=false,
    AutoClose=true,
    OnSelected=f,
}

```


```lua
local Dropdown = Canvas:Dropdown({
    AutoClose = true
})
```

## OverlayScroll

Overlay container with scrolling support.

```lua

type OverlayScroll = {
    ElementClass= 'OverlayScroll',
    Spacing=UDim.new(0,4),
}

```


```lua
local Overlay = Canvas:OverlayScroll({
    Spacing = UDim.new(0, 4)
})
```

## Overlay

Overlay container above normal content.

```lua

type Overlay = {
    ElementClass='Overlay',
}

```


```lua
local Overlay = Canvas:Overlay()
```

## Selectable

Selectable text or item block.

```lua

type Selectable = {
    Text='Selectable',
    Callback=f,
    Selected=false,
    Disabled=false,
    Size=UDim2.fromScale(1,0),
    AutomaticSize=Enum.AutomaticSize.Y,
    TextXAlignment=Enum.TextXAlignment.Left,
    AnimationTags={Selected='Buttons', Unselected='TransparentButtons'},
}

```


```lua
Menu:Selectable({
    Text = "Open",
    Callback = function() end
})
```

## ImageButton

Clickable image button element.

```lua

type ImageButton = {
    ElementStyle='Button',
    Callback=f,
}

```


```lua
Canvas:ImageButton({
    Image = ReGui.Icons.Close,
    Callback = function() end
})
```

## MenuBar

Top menu bar container.

```lua

type MenuBar = {
}

```


```lua
local MenuBar = Window:MenuBar()
```

## MenuButton

Menu bar button or menu opener.

```lua

type MenuButton = {
    Text='MenuButton',
    PaddingLeft=UDim.new(0,8),
    PaddingRight=UDim.new(0,8),
    Size=UDim2.fromOffset(0,19),
    AutomaticSize=Enum.AutomaticSize.XY,
}

```


```lua
local Menu = MenuBar:MenuItem({
    Text = "File"
})
```

## TabBar

Core tab bar helper.

```lua

type TabBar = {
    AutoSelectNewTabs= true,
    OnActiveTabChange=f,
    OnTabCreate=f,
    OnTabRemove=f,
}

```


```lua
local TabBar = Window:TabBar()
TabBar:CreateTab({ Name = "Main" })
```

## Canvas

Basic window content canvas.

```lua

type Canvas = {
}

```


```lua
local Canvas = Window:Canvas()
Canvas:Label({ Text = "Hello" })
```

## ScrollingCanvas

Canvas with scrolling enabled.

```lua

type ScrollingCanvas = {
    Scroll=true,
}

```


```lua
local Canvas = Window:ScrollingCanvas({
    Fill = true
})
```

## Group

Grouped content container.

```lua

type Group = {
    Scroll=false,
    AutomaticSize=Enum.AutomaticSize.Y,
}

```


```lua
local Group = Canvas:Group()
Group:Label({ Text = "Grouped item" })
```

## PopupCanvas

Popup-attached canvas container.

```lua

type PopupCanvas = {
    AutoClose=false,
    Scroll=false,
    Visible=true,
    Spacing=UDim.new(0,1),
    AutomaticSize= Enum.AutomaticSize.XY,
    MaxSizeY=150,
    MinSizeX=100,
    MaxSizeX=math.huge,
    OnClosed=f,
}

```


```lua
local Popup = Canvas:PopupCanvas({
    RelativeTo = SomeButton,
    AutoClose = true
})
Popup:Label({ Text = "Popup content" })
```

## ArrowButton

Directional arrow button.

```lua

type ArrowButton = {
    Direction='Left',
    ColorTag='Button',
    Icon= aa.Icons.Arrow,
    Size=UDim2.fromOffset(21,21),
    IconSize=UDim2.fromScale(1,1),
    IconPadding=UDim.new(0,4),
    Rotations={Left=180,Right=0},
}

```


```lua
Canvas:ArrowButton({
    Direction = "Left"
})
```

## MultiElement

Composite helper that builds multiple sub-elements.

```lua

type MultiElement = {
    Callback=f,
    Label='',
    Disabled=false,
    BaseInputConfig={},
    InputConfigs={},
    Value={},
    Minimum={},
    Maximum={},
    MultiCallback=f,
}

```


```lua
Canvas:MultiElement({
    Label = "XYZ",
    InputConfigs = { {}, {}, {} },
    Value = {0, 0, 0}
})
```
