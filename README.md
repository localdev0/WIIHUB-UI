## Create WIIHUB UI
```lua
local Library = {};

local plr = game:GetService('Players').LocalPlayer
local mouse = plr:GetMouse()
local Camera = workspace.CurrentCamera;
local CoreGui = game:GetService("CoreGui")
local UIS = game:GetService("UserInputService");
local RS = game:GetService("RunService");
local TS = game:GetService("TweenService");
local spr = RS:IsStudio() and require(workspace.spr) or loadstring(game:HttpGet("https://raw.githubusercontent.com/Fraktality/spr/master/spr.lua"))()


local UI = Instance.new("ScreenGui");
if syn then
	syn.protect_gui(UI)
end
if protectgui then
	protectgui(UI)
end
UI.Parent = RS:IsStudio() and plr.PlayerGui or game:GetService("CoreGui");
UI.ZIndexBehavior = Enum.ZIndexBehavior.Sibling


local components = {}; -- config loading/saving
local Flags = {}
local PrimaryColors = {};
local contents = {};

local LibMeta = {
	PrimaryColor = Color3.fromRGB(113, 94, 241);


	Tabs = {};
	thingsToSet = {};
	thingsToClose = {};
	Sections = {};
};

function LibMeta:Toggle()
	UI.Enabled = not UI.Enabled
end

local toggleBinds = {}
local mainKeybind = "LeftControl"

UIS.InputBegan:Connect(function(key, gp)
	if gp then return end;

	if key.KeyCode == Enum.KeyCode[mainKeybind] then
		LibMeta:Toggle()
	end

	for i,v in ipairs(toggleBinds) do 
		if v.keyBind and Enum.KeyCode[v.keyBind] and Enum.KeyCode[v.keyBind] == key.KeyCode then
			if v.Enabled and v.Disable then 
				v:Disable();
				v.callback(v.Enabled);
			elseif v.Enable then
				v:Enable();
				v.callback(v.Enabled);
			end
		end
	end
end)

local Library = setmetatable({}, { --// Auto change all color things when Library.PrimaryColor is changed
	__newindex = function(table, key, value)
		if key == "PrimaryColor" then
			for item, properties in pairs(PrimaryColors) do
				for _, property in ipairs(properties) do
					item[property] = value;
				end
			end
		end
		LibMeta[key] = value;
	end,
	__index = function(table, key)
		return LibMeta[key];
	end,
})


local function isHoveringOverObj(obj)
	local tx = obj.AbsolutePosition.X
	local ty = obj.AbsolutePosition.Y
	local bx = tx + obj.AbsoluteSize.X
	local by = ty + obj.AbsoluteSize.Y
	if mouse.X >= tx and mouse.Y >= ty and mouse.X <= bx and mouse.Y <= by then
		return true
	end
end

local function CreateDrag(gui)
	local dragging
	local dragInput
	local dragStart
	local startPos

	local function update(input)
		local delta = input.Position - dragStart
		TS:Create(gui, TweenInfo.new(0.16, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)}):Play();
	end

	local lastEnd = 0
	local function closeClosables()
		if os.clock() < lastEnd + 0.5 then
			return
		end
		--lastEnd = os.clock()
		for _, item in ipairs(Library.thingsToClose) do
			task.spawn(function()
				if type(item) == 'table' and rawget(item, "Close") then
					local can = true
					if item.lastOpened and os.clock() < item.lastOpened + 0.5 then
						can = false 
					end
					for _, asd in ipairs(item.MainFrames) do
						if isHoveringOverObj(asd) then
							can = false
						end 
					end
					if can then
						item:Close();
					end
				end
			end)
		end 
	end
	local lastMoved = 0
	local con
	gui.InputBegan:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
			dragging = true
			dragStart = input.Position
			startPos = gui.Position

		end
	end)

	UIS.InputEnded:Connect(function(input)

		if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
			dragging = false
			closeClosables()
		end
	end)


	gui.InputChanged:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
			dragInput = input
			lastMoved = os.clock()
		end
	end)

	UIS.InputChanged:Connect(function(input)
		if input == dragInput and dragging then
			update(input)
		end
	end)
end



--// Main page instances

local BG = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local UIStroke = Instance.new("UIStroke")
local UIGradient = Instance.new("UIGradient")
local UIGradient2 = Instance.new("UIGradient")
local Tabs = Instance.new("ScrollingFrame")
local UIListLayout = Instance.new("UIListLayout")

BG.Name = "Background"
BG.Parent = UI
BG.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
BG.BorderSizePixel = 0
BG.Position = UDim2.new(0.178, 0, 0.312, 0)
BG.Size = UDim2.new(0, 703, 0, 374)

UICorner.CornerRadius = UDim.new(0, 15)
UICorner.Parent = BG

UIStroke.Color = Color3.fromRGB(255, 255, 255);
UIStroke.Thickness = 0.8;
UIStroke.Transparency = 0.45;
UIStroke.Parent = BG

UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(9, 9, 9)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(9, 9, 9))}
UIGradient.Parent = BG

UIGradient2.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(9, 9, 9)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(9, 9, 9))}
UIGradient2.Parent = UIStroke


--// Header
local Header = Instance.new("Frame")
local Container = Instance.new("Frame")
local _1Icon = Instance.new("ImageLabel")
local _2Title = Instance.new("TextLabel")
local UIPadding = Instance.new("UIPadding")
local UIListLayout = Instance.new("UIListLayout")
local UIPadding_2 = Instance.new("UIPadding")
local Middleupperline = Instance.new("Frame")
local _3Padding = Instance.new("Frame")
local Underline = Instance.new("Frame")
local CloseButton = Instance.new("ImageButton")
local _1Path = Instance.new("Frame")
local TextLabelPath = Instance.new("TextLabel")
local UIPadding_3 = Instance.new("UIPadding")

Header.Name = "Header"
Header.Parent = BG
Header.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Header.BackgroundTransparency = 1.000
Header.Size = UDim2.new(0.998577535, 0, -0.112299465, 100)

Container.Name = "Container"
Container.Parent = Header
Container.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Container.BackgroundTransparency = 1.000
Container.Size = UDim2.new(1, 0, 1, 0)

_1Icon.Name = "1Icon"
_1Icon.Parent = Container
_1Icon.BackgroundTransparency = 1.000
_1Icon.BorderSizePixel = 0
_1Icon.ImageColor3 = Color3.fromRGB(113, 94, 241)
_1Icon.Position = UDim2.new(0, 0, 0.103448279, 0)
_1Icon.Size = UDim2.new(0, 31, 0, 31)
_1Icon.Image = "http://www.roblox.com/asset/?id=6031079158"

_2Title.Name = "2Title"
_2Title.Parent = Container
_2Title.AnchorPoint = Vector2.new(0, 0.5)
_2Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
_2Title.BackgroundTransparency = 1.000
_2Title.Position = UDim2.new(0.0725462288, 0, 0.5, 0)
_2Title.Size = UDim2.new(-0.136259779, 200, 1, 0)
_2Title.Font = Enum.Font.Gotham
_2Title.Text = "OnyxHub.exe"
_2Title.TextColor3 = Color3.fromRGB(197, 197, 197)
_2Title.TextSize = 18.000

UIPadding.Parent = _2Title
UIPadding.PaddingLeft = UDim.new(0, 20)

UIListLayout.Parent = Container
UIListLayout.FillDirection = Enum.FillDirection.Horizontal
UIListLayout.VerticalAlignment = Enum.VerticalAlignment.Center

UIPadding_2.Parent = Container
UIPadding_2.PaddingLeft = UDim.new(0, 20)

Middleupperline.Name = "Middleupperline"
Middleupperline.Parent = Container
Middleupperline.AnchorPoint = Vector2.new(0.5, 0.5)
Middleupperline.BackgroundColor3 = Color3.fromRGB(43, 44, 44)
Middleupperline.BackgroundTransparency = 0.550
Middleupperline.BorderSizePixel = 0
Middleupperline.Position = UDim2.new(0.375533313, 0, 0.0802138224, 0)
Middleupperline.Size = UDim2.new(0, 1, 0.5, 0)

_3Padding.Name = "3Padding"
_3Padding.Parent = Container
_3Padding.AnchorPoint = Vector2.new(0.5, 0.5)
_3Padding.BackgroundColor3 = Color3.fromRGB(43, 44, 44)
_3Padding.BackgroundTransparency = 1.000
_3Padding.BorderSizePixel = 0
_3Padding.Position = UDim2.new(0.248644039, 0, 0.5, 0)
_3Padding.Size = UDim2.new(0.0468542725, 1, 0.5, 0)

Underline.Name = "Underline"
Underline.Parent = Header
Underline.AnchorPoint = Vector2.new(0.5, 0.5)
Underline.BackgroundColor3 = Color3.fromRGB(43, 44, 44)
Underline.BackgroundTransparency = 0.550
Underline.BorderSizePixel = 0
Underline.Position = UDim2.new(0.5, 0, 1, 0)
Underline.Size = UDim2.new(1, 0, 0, 1)

CloseButton.Name = "CloseButton"
CloseButton.Parent = Header
CloseButton.Active = false
CloseButton.AnchorPoint = Vector2.new(0, 0.5)
CloseButton.BackgroundTransparency = 1.000
CloseButton.BorderSizePixel = 0
CloseButton.Position = UDim2.new(0.939999998, 0, 0.5, 0)
CloseButton.Selectable = false
CloseButton.Size = UDim2.new(0, 25, 0, 25)
CloseButton.AutoButtonColor = false
CloseButton.Image = "http://www.roblox.com/asset/?id=6031094678"
CloseButton.ImageColor3 = Color3.fromRGB(130, 130, 130)

_1Path.Name = "1Path"
_1Path.Parent = Header
_1Path.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
_1Path.BackgroundTransparency = 1.000
_1Path.Position = UDim2.new(0.294871807, 0, 0.0344827585, 0)
_1Path.Size = UDim2.new(0.646723628, 0, 0.356067389, 36)

TextLabelPath.Parent = _1Path
TextLabelPath.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabelPath.BackgroundTransparency = 1.000
TextLabelPath.Position = UDim2.new(-0.0110132154, 0, 0, 0)
TextLabelPath.Size = UDim2.new(1.01101327, 0, 1, 0)
TextLabelPath.Font = Enum.Font.Gotham
TextLabelPath.RichText = true
TextLabelPath.Text = "Projects  /  Cheeto  / <font color=\"#715EF1\">  Selected Tab</font>"
TextLabelPath.TextColor3 = Color3.fromRGB(116, 116, 116)
TextLabelPath.TextSize = 12.000
TextLabelPath.TextXAlignment = Enum.TextXAlignment.Left

UIPadding_3.Parent = TextLabelPath
UIPadding_3.PaddingLeft = UDim.new(0.0299999993, 0)


--// Footer

local Footer = Instance.new("Frame")
local Container = Instance.new("Frame")
local _3Title = Instance.new("TextLabel")
local UIPadding = Instance.new("UIPadding")
local UICorner = Instance.new("UICorner")
local Avatar = Instance.new("Frame")
local UICorner_2 = Instance.new("UICorner")
local UIStroke_2 = Instance.new("UIStroke")
local InnerBG = Instance.new("Frame")
local UICorner_3 = Instance.new("UICorner")
local Underline = Instance.new("Frame")

Footer.Name = "Footer"
Footer.Parent = BG
Footer.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Footer.BackgroundTransparency = 1.000
Footer.Position = UDim2.new(0, 0, 0.842245996, 0)
Footer.Size = UDim2.new(0.998577535, 0, -0.109625645, 100)

Container.Name = "Container"
Container.Parent = Footer
Container.BackgroundColor3 = Color3.fromRGB(5, 4, 25)
Container.BackgroundTransparency = 1.000
Container.Position = UDim2.new(0, 0, 0.0931247547, 0)
Container.Size = UDim2.new(1, 0, 0.906873763, 0)

_3Title.Name = "2Title"
_3Title.Parent = Container
_3Title.AnchorPoint = Vector2.new(0, 0.5)
_3Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
_3Title.BackgroundTransparency = 1.000
_3Title.Position = UDim2.new(0.0013210373, 0, 0.453275919, 0)
_3Title.Size = UDim2.new(1, 0, 1.09344828, 0)
_3Title.Font = Enum.Font.Gotham
_3Title.Text = "Welcome, OnlyTwentyCharacters"
_3Title.TextColor3 = Color3.fromRGB(197, 197, 197)
_3Title.TextSize = 14.000
_3Title.TextXAlignment = Enum.TextXAlignment.Left

UIPadding.Parent = _3Title
UIPadding.PaddingLeft = UDim.new(0, 20)

UICorner.CornerRadius = UDim.new(0, 15)
UICorner.Parent = Container

Avatar.Name = "Avatar"
Avatar.Parent = Container
Avatar.AnchorPoint = Vector2.new(0, 0.5)
Avatar.BackgroundColor3 = Color3.fromRGB(113, 94, 241)
Avatar.BackgroundTransparency = 1.000
Avatar.Position = UDim2.new(0.921179473, 0, 0.443931043, 0)
Avatar.Size = UDim2.new(0, 38, 0, 38)

UICorner_2.CornerRadius = UDim.new(0, 200)
UICorner_2.Parent = Avatar

UIStroke_2.Color = Color3.fromRGB(113, 94, 241);
UIStroke_2.Thickness = 1;
UIStroke_2.Transparency = 0;
UIStroke_2.Parent = Avatar

InnerBG.Name = "InnerBG"
InnerBG.Parent = Avatar
InnerBG.AnchorPoint = Vector2.new(0.5, 0.5)
InnerBG.BackgroundColor3 = Color3.fromRGB(113, 94, 241)
InnerBG.Position = UDim2.new(0.5, 0, 0.5, 0)
InnerBG.Size = UDim2.new(1, -4, 1, -4)

local avImg = Instance.new("ImageLabel")
avImg.BackgroundTransparency = 1
avImg.Size = UDim2.fromScale(1,1)
local userId = plr.UserId
local thumbType = Enum.ThumbnailType.HeadShot
local thumbSize = Enum.ThumbnailSize.Size420x420
local content, isReady = game:GetService('Players'):GetUserThumbnailAsync(userId, thumbType, thumbSize)
avImg.Image = content
avImg.Parent = InnerBG
UICorner_2:Clone().Parent = avImg

UICorner_3.CornerRadius = UDim.new(0, 200)
UICorner_3.Parent = InnerBG

Underline.Name = "Underline"
Underline.Parent = Footer
Underline.AnchorPoint = Vector2.new(0.5, 0.5)
Underline.BackgroundColor3 = Color3.fromRGB(43, 44, 44)
Underline.BackgroundTransparency = 0.550
Underline.BorderSizePixel = 0
Underline.Position = UDim2.new(0.5, 0, 0, 0)
Underline.Size = UDim2.new(1, 0, 0, 1)


--// Sidebar / Navbar
local Sidebar = Instance.new("ScrollingFrame")
local Underline = Instance.new("Frame")
local Container = Instance.new("Frame")
local UIListLayout = Instance.new("UIListLayout")
local UIPadding = Instance.new("UIPadding")



Sidebar.Name = "Sidebar"
Sidebar.Parent = BG
Sidebar.Active = true
Sidebar.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Sidebar.BackgroundTransparency = 1.000
Sidebar.Position = UDim2.new(0, 0, 0.155080214, 0)
Sidebar.Size = UDim2.new(0.106685631, 118, 0.687165797, 0)
Sidebar.ScrollBarThickness = 0

Underline.Name = "Underline"
Underline.Parent = Sidebar
Underline.AnchorPoint = Vector2.new(1, 0.5)
Underline.BackgroundColor3 = Color3.fromRGB(43, 44, 44)
Underline.BackgroundTransparency = 0.550
Underline.BorderSizePixel = 0
Underline.Position = UDim2.new(0.99000001, 0, 0.5, 0)
Underline.Size = UDim2.new(0, 1, 1, 0)
Underline.ZIndex = 3

Container.Name = "Container"
Container.Parent = Sidebar
Container.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Container.BackgroundTransparency = 1.000
Container.Size = UDim2.new(1, 0, 1, 0)

UIListLayout.Parent = Container
UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayout.Padding = UDim.new(0, 5)

UIPadding.Parent = Container
UIPadding.PaddingTop = UDim.new(0, 15)



local Canvas = Instance.new("Frame")
local UIListLayout_2 = Instance.new("UIListLayout")


Canvas.Name = "Canvas"
Canvas.Parent = BG
Canvas.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Canvas.BackgroundTransparency = 1.000
Canvas.Position = UDim2.new(0.273115218, 0, 0.155080214, 0)
Canvas.Size = UDim2.new(0.726884782, 0, 0.5775401, 100)

UIListLayout_2.Parent = Canvas
UIListLayout_2.HorizontalAlignment = Enum.HorizontalAlignment.Center


CreateDrag(BG)

CloseButton.MouseButton1Click:Connect(function()
	Library:Toggle(false)
end)

local entered = {}
local function closeAllTipsExcept(tab)
	for _, tooltip in ipairs(entered) do
		if tooltip ~= tab and tooltip.isOpen then
			tooltip:Close(true)
		end
	end
end

UIS.InputChanged:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
		if not isHoveringOverObj(BG) then
			closeAllTipsExcept()
		else
			for _, tooltip in ipairs(entered) do
				if tooltip.isOpen and not isHoveringOverObj(tooltip.HoverObj) then
					tooltip:Close(true)
				end
			end
		end
	end
end)


function Library:SetTitle(title)
	_2Title.Text = title
end

function Library:SetFooter(text)
	_3Title.Text = text
end




function Library:NewTab(Title)

	local Funcs = {
		isOpen = false;	
		tweenTime = 0.2;
		LeftTabs = {};
		RightTabs = {};
		cooldown = 0.5;
		lastChanged = 0;
		connections = {};
	};

	--// left tab button
	local ButtonContainer = Instance.new("Frame") -- TODO: Slide in child of ButtonContainer when loaded
	local TabButton = Instance.new("TextButton")
	local UICorner = Instance.new("UICorner")
	local UIGradient = Instance.new("UIGradient")
	local TextLabel = Instance.new("TextLabel")
	local UIPadding = Instance.new("UIPadding")

	ButtonContainer.Name = "ButtonContainer"
	ButtonContainer.Parent = Container
	ButtonContainer.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	ButtonContainer.BackgroundTransparency = 1.000
	ButtonContainer.Size = UDim2.new(1, -25, 0, 25)
	ButtonContainer.ZIndex = -1

	TabButton.Name = "TabButton"
	TabButton.Parent = ButtonContainer
	TabButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	TabButton.Size = UDim2.new(1, -25, 0, 25)
	TabButton.AutoButtonColor = false
	TabButton.Font = Enum.Font.Gotham
	TabButton.BackgroundTransparency = 1
	TabButton.Text = ""
	TabButton.TextColor3 = Color3.fromRGB(255, 255, 255)
	TabButton.TextSize = 14.000
	TabButton.TextXAlignment = Enum.TextXAlignment.Left

	UICorner.CornerRadius = UDim.new(0, 6)
	UICorner.Parent = TabButton

	UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(113, 94, 241)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(75, 64, 149))}
	UIGradient.Parent = TabButton

	TextLabel.Parent = TabButton
	TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	TextLabel.BackgroundTransparency = 1.000
	TextLabel.Size = UDim2.new(1, 0, 1, 0)
	TextLabel.Font = Enum.Font.Gotham
	TextLabel.Text = Title
	TextLabel.TextColor3 = Color3.fromRGB(118, 118, 118)
	TextLabel.TextSize = 14.000
	TextLabel.TextXAlignment = Enum.TextXAlignment.Left

	UIPadding.Parent = TextLabel
	UIPadding.PaddingLeft = UDim.new(0.100000001, 0)


	--// Page / canvas

	local Container = Instance.new("ScrollingFrame")
	local UIListLayout = Instance.new("UIListLayout")
	local UIPadding = Instance.new("UIPadding")

	Container.Name = "Container"
	Container.Parent = Canvas
	Container.Active = true
	Container.Visible = false
	Container.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Container.BackgroundTransparency = 1.000
	Container.Size = UDim2.new(1, 0, 0.813291132, 0)
	Container.ScrollBarThickness = 0
	Container.CanvasPosition = Vector2.new(0, 0)
	Container.AutomaticCanvasSize = Enum.AutomaticSize.Y
	Container.CanvasSize = UDim2.new(1,0,0,0)

	UIListLayout.Parent = Container
	UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
	UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIListLayout.Padding = UDim.new(0, 10)

	UIPadding.Parent = Container
	UIPadding.PaddingTop = UDim.new(0, 15)
	UIPadding.PaddingBottom = UDim.new(0, 15)



	--// Component Functions
	function Funcs:NewToggle(Title, default, Callback, parent)
		local toggleFuncs = {
			Enabled = default;
			toggle_key = nil,
			tweenTime = 0.1;
			keyBind = nil,
			callback = Callback
		};



		local Toggle = Instance.new("ImageButton")
		local UICorner = Instance.new("UICorner")
		local UIStroke1 = Instance.new("UIStroke")
		local UIStroke2 = Instance.new("UIStroke")
		local FeatureTitle = Instance.new("TextLabel")
		local UIPadding = Instance.new("UIPadding")
		local ToggleBtn = Instance.new("ImageButton")
		local UICorner_2 = Instance.new("UICorner")
		local Checkmark = Instance.new("ImageButton")
		local ImageLabel = Instance.new("ImageLabel")
		local UIGradient = Instance.new("UIGradient")

		Toggle.Name = "Toggle"
		Toggle.Parent = parent or Container
		Toggle.AutoButtonColor = false
		Toggle.ImageTransparency = 1
		Toggle.BackgroundColor3 = Color3.fromRGB(75, 75, 75)
		Toggle.BackgroundTransparency = 0.900
		Toggle.Size = UDim2.new(0, 485, 0, 38)

		UICorner.CornerRadius = UDim.new(0, 4)
		UICorner.Parent = Toggle

		UIStroke1.Color = Color3.fromRGB(255, 255, 255);
		UIStroke1.Thickness = 1;
		UIStroke1.Transparency = 1; -- enabled: 0
		UIStroke1.Parent = Toggle

		local UIGradientS = Instance.new("UIGradient")
		UIGradientS.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(5, 4, 25)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(113, 94, 241))}
		UIGradientS.Rotation = 180
		UIGradientS.Parent = UIStroke1
		UIGradientS.Offset = Vector2.new(-1,0)

		FeatureTitle.Name = "FeatureTitle"
		FeatureTitle.Parent = Toggle
		FeatureTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		FeatureTitle.BackgroundTransparency = 1.000
		FeatureTitle.Position = UDim2.new(0.104999967, 0, 0, 0)
		FeatureTitle.Size = UDim2.new(0.0947574526, 100, 1, 0)
		FeatureTitle.Font = Enum.Font.Gotham
		FeatureTitle.Text = Title
		FeatureTitle.TextColor3 = Color3.fromRGB(91, 91, 91)--Color3.fromRGB(162, 162, 162)
		FeatureTitle.TextSize = 14.000
		FeatureTitle.TextXAlignment = Enum.TextXAlignment.Left

		UIPadding.Parent = FeatureTitle

		ToggleBtn.Name = "ToggleBtn"
		ToggleBtn.Parent = Toggle
		ToggleBtn.AnchorPoint = Vector2.new(0, 0.5)
		ToggleBtn.BackgroundColor3 = Color3.fromRGB(113, 94, 241)
		ToggleBtn.Position = UDim2.new(0.0199999996, 0, 0.5, 0)
		ToggleBtn.Size = UDim2.new(0, 20, 0, 20)
		ToggleBtn.AutoButtonColor = false
		ToggleBtn.ImageColor3 = Color3.fromRGB(165, 165, 165)

		UIStroke2.Color = Color3.fromRGB(35, 35, 35);
		UIStroke2.Thickness = 1;
		UIStroke2.Transparency = 0; -- enabled: 1
		UIStroke2.Parent = ToggleBtn

		UICorner_2.CornerRadius = UDim.new(0, 4)
		UICorner_2.Parent = ToggleBtn

		Checkmark.Name = "Checkmark"
		Checkmark.Parent = ToggleBtn
		Checkmark.AnchorPoint = Vector2.new(0.5, 0.5)
		Checkmark.BackgroundColor3 = Color3.fromRGB(113, 94, 241)
		Checkmark.BackgroundTransparency = 1.000
		Checkmark.Position = UDim2.new(0.5, 0, 0.5, 0)
		Checkmark.Size = UDim2.new(0, 18, 0, 18)
		Checkmark.ZIndex = 2
		Checkmark.AutoButtonColor = false
		Checkmark.Image = "http://www.roblox.com/asset/?id=6031094667"
		Checkmark.ImageColor3 = Color3.fromRGB(247, 247, 247)


		ImageLabel.Parent = ToggleBtn
		ImageLabel.AnchorPoint = Vector2.new(0.5, 0.5)
		ImageLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		ImageLabel.BackgroundTransparency = 1.000
		ImageLabel.Position = UDim2.new(0.5, 0, 0.5, 0)
		ImageLabel.Size = UDim2.new(0, 23, 0, 23)
		ImageLabel.Image = "https://www.dreamstime.com/illustration/thinking-emoji.html"
		ImageLabel.ImageColor3 = Color3.fromRGB(113, 94, 241)







		UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(153, 175, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(153, 175, 255))}
		UIGradient.Rotation = 180
		UIGradient.Parent = Toggle



		function toggleFuncs:Enable()
			toggleFuncs.Enabled = true;

			spr.target(Checkmark, 1, 3, {
				ImageTransparency = 0;
			})
			spr.target(ToggleBtn, 1, 3, {
				BackgroundTransparency = 0;
			})
			spr.target(ImageLabel, 1, 3, {
				ImageTransparency = 0;
			})
			spr.target(FeatureTitle, 1, 3, {
				TextColor3 = Color3.fromRGB(162, 162, 162);
			})
			spr.target(UIStroke2, 1, 3, {
				Transparency = 1;
			})

			spr.target(UIStroke1, 1, 3, {
				Transparency = 0;
			})
			spr.target(UIGradientS, .7, 1, {
				Offset = Vector2.new(0,0)
			})

		end

		function toggleFuncs:Disable()
			toggleFuncs.Enabled = false;

			spr.target(Checkmark, 1, 3, {
				ImageTransparency = 1;
			})
			spr.target(ToggleBtn, 1, 3, {
				BackgroundTransparency = 1;
			})
			spr.target(ImageLabel, 1, 3, {
				ImageTransparency = 1;
			})
			spr.target(FeatureTitle, 1, 3, {
				TextColor3 = Color3.fromRGB(91, 91, 91);
			})
			spr.target(UIStroke2, 1, 3, {
				Transparency = 0;
			})
			spr.target(UIStroke1, 1, 3, {
				Transparency = 1;
			})
			spr.target(UIGradientS, .7, .5, {
				Offset = Vector2.new(-1,0)
			})

		end


		if type(Callback) == "function" then
			Callback(default);

			if default == true then
				toggleFuncs:Enable()
			else
				toggleFuncs:Disable()
			end
		end


		table.insert(Funcs.connections, Toggle.MouseButton1Down:Connect(function()
			if toggleFuncs.Enabled then
				toggleFuncs:Disable();
			else
				toggleFuncs:Enable();
			end
			Callback(toggleFuncs.Enabled);
		end))


		function toggleFuncs:AddToolTip(Text)
			--Library:AddToolTip(ScrollingFrame, ToggleBG, toggleFuncs.tweenTime, Text)
		end

		function toggleFuncs:Set(val)
			Callback(val)
			if val then
				toggleFuncs:Enable()
			else
				toggleFuncs:Disable()
			end
			components[Title] = {
				component_name = Title;
				component_default = default;
				component_callback = Callback;
				component_type = "Toggle";
				component_table = toggleFuncs;
			}
		end
		

		toggleFuncs.Toggle = toggleFuncs.Set
		
		
		
		local KeybTxt
		function toggleFuncs:SetKeybind(keyText)
			if KeybTxt then
				KeybTxt:Destroy()
			end
			if keyText == nil then
				keyText = "Click to Bind"
			end

			if keyText ~= "Click to Bind" then
				toggleFuncs.keyBind = keyText
				components[Title] = {
					component_name = Title;
					component_default = default;
					component_callback = Callback;
					component_type = "Toggle";
					component_table = toggleFuncs;
				}
			end

			KeybTxt = Instance.new("TextButton")
			KeybTxt.Name = "Title"
			KeybTxt.Parent = Toggle
			KeybTxt.AnchorPoint	= Vector2.new(1,0.5)
			KeybTxt.Position = UDim2.new(0.965,0,0.5,0)
			KeybTxt.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			KeybTxt.BackgroundTransparency = 1.000
			KeybTxt.AutomaticSize = Enum.AutomaticSize.X
			KeybTxt.Size = UDim2.new(.1, 0, 1, 0)
			KeybTxt.Font = Enum.Font.Gotham
			KeybTxt.TextColor3 = Color3.fromRGB(91, 91, 91)--Color3.fromRGB(162, 162, 162)
			KeybTxt.TextSize = 14.000
			KeybTxt.TextXAlignment = Enum.TextXAlignment.Right

			KeybTxt.Text = keyText ~= "Click to Bind" and "Bind: "..keyText or keyText;

			if keyText ~= "Click to Bind" then
				KeybTxt.TextColor3 = Color3.fromRGB(197, 197, 197)
			end

			local oldCon
			table.insert(Funcs.connections, KeybTxt.MouseButton1Down:Connect(function()
				KeybTxt.Text = "..."
				KeybTxt.TextColor3 = Color3.fromRGB(255, 255, 255);
				if oldCon then
					oldCon:Disconnect()
				end

				oldCon = UIS.InputBegan:Connect(function(key, gp)
					if gp then return end;
					if key.KeyCode and key.KeyCode ~= Enum.KeyCode.Backspace then

						KeybTxt.Text = "Bind: "..tostring(key.KeyCode):gsub("Enum.KeyCode.", "");
						KeybTxt.TextColor3 = Color3.fromRGB(197, 197, 197)

						oldCon:Disconnect()
						task.delay(1, function()
							toggleFuncs.keyBind = tostring(key.KeyCode):gsub("Enum.KeyCode.","")
							components[Title] = {
								component_name = Title;
								component_default = default;
								component_callback = Callback();
								component_type = "Toggle";
								component_table = toggleFuncs;
							}
						end)

					elseif key.KeyCode and key.KeyCode == Enum.KeyCode.Backspace then
						toggleFuncs.keyBind = nil
						toggleFuncs.toggle_key = toggleFuncs.keyBind
						KeybTxt.TextColor3 = Color3.fromRGB(91, 91, 91)
						KeybTxt.Text = "Click to Bind"

						oldCon:Disconnect()

						components[Title] = {
							component_name = Title;
							component_default = default;
							component_callback = Callback;
							component_type = "Toggle";
							component_table = toggleFuncs;
						}

					end
				end)
			end))

			table.insert(toggleBinds, toggleFuncs)

		end
		toggleFuncs:SetKeybind() --//Bindable by default
		
		
		
		table.insert(Library.thingsToSet, {functions = toggleFuncs})
		components[Title] = {
			component_name = Title;
			component_default = default;
			component_callback = Callback;
			component_type = "Toggle";
			component_table = toggleFuncs;
		}
		table.insert(Flags, {
			name = Title, 
			tb = toggleFuncs
		})

		return toggleFuncs

	end

	function Funcs:NewSlider(Title, min, max, default, Callback, parent)
		local toggleFuncs = {	
			tweenTime = 0.2;
			current_value = default;
		};

		local Slider = Instance.new("ImageButton")
		local UICorner = Instance.new("UICorner")
		local UIGradient = Instance.new("UIGradient")
		local SliderBG = Instance.new("Frame")
		local UICorner_2 = Instance.new("UICorner")
		local box = Instance.new("Frame")
		local UICorner_3 = Instance.new("UICorner")
		local ColoredLine = Instance.new("Frame")
		local UICorner_4 = Instance.new("UICorner")
		local FeatureTitle = Instance.new("TextLabel")
		local UIPadding = Instance.new("UIPadding")
		local InputValue = Instance.new("Frame")
		local UICorner_5 = Instance.new("UICorner")
		local TextLabel = Instance.new("TextBox")

		Slider.Name = "Slider"
		Slider.ImageTransparency = 1
		Slider.AutoButtonColor = false
		Slider.Parent = parent or Container
		Slider.BackgroundColor3 = Color3.fromRGB(75, 75, 75)
		Slider.BackgroundTransparency = 0.900
		Slider.Size = UDim2.new(0, 485,0, 38)

		UICorner.CornerRadius = UDim.new(0, 4)
		UICorner.Parent = Slider

		UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(153, 175, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(153, 175, 255))}
		UIGradient.Rotation = 180
		UIGradient.Parent = Slider

		SliderBG.Name = "SliderBG"
		SliderBG.Parent = Slider
		SliderBG.AnchorPoint = Vector2.new(0, 0.5)
		SliderBG.BackgroundColor3 = Color3.fromRGB(91, 91, 91)
		SliderBG.Position = UDim2.new(0.338999987, 0, 0.5, 0)
		SliderBG.Size = UDim2.new(0, 299, 0, 4)

		UICorner_2.CornerRadius = UDim.new(0, 240)
		UICorner_2.Parent = SliderBG

		box.Name = "box"
		box.Parent = SliderBG
		box.AnchorPoint = Vector2.new(0.5, 0.5)
		box.BackgroundColor3 = Color3.fromRGB(214, 220, 235)
		box.Position = UDim2.new(0.819999993, 0, 0.5, 0)
		box.Size = UDim2.new(0, 12, 0, 12)
		box.ZIndex = 2

		UICorner_3.CornerRadius = UDim.new(0, 240)
		UICorner_3.Parent = box

		ColoredLine.Name = "ColoredLine"
		ColoredLine.Parent = SliderBG
		ColoredLine.AnchorPoint = Vector2.new(0, 0.5)
		ColoredLine.BackgroundColor3 = Color3.fromRGB(113, 94, 241)
		ColoredLine.Position = UDim2.new(0, 0, 0.5, 0)
		ColoredLine.Size = UDim2.new(0.819999993, 4, 0, 4)

		UICorner_4.CornerRadius = UDim.new(0, 24)
		UICorner_4.Parent = ColoredLine

		FeatureTitle.Name = "FeatureTitle"
		FeatureTitle.Parent = Slider
		FeatureTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		FeatureTitle.BackgroundTransparency = 1.000
		FeatureTitle.Position = UDim2.new(0.104999967, 0, 0, 0)
		FeatureTitle.Size = UDim2.new(0.0949999988, 0, 1, 0)
		FeatureTitle.Font = Enum.Font.Gotham
		FeatureTitle.Text = Title
		FeatureTitle.TextColor3 = Color3.fromRGB(162, 162, 162)
		FeatureTitle.TextSize = 14.000
		FeatureTitle.TextXAlignment = Enum.TextXAlignment.Left

		UIPadding.Parent = FeatureTitle
		UIPadding.PaddingRight = UDim.new(0, 10)

		InputValue.Name = "InputValue"
		InputValue.Parent = Slider
		InputValue.Active = true
		InputValue.AnchorPoint = Vector2.new(0, 0.5)
		InputValue.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		InputValue.BackgroundTransparency = 1.000
		InputValue.Position = UDim2.new(0.0199999996, 0, 0.5, 0)
		InputValue.Selectable = true
		InputValue.Size = UDim2.new(0, 25, 0, 25)

		UICorner_5.CornerRadius = UDim.new(0, 4)
		UICorner_5.Parent = InputValue

		TextLabel.Parent = InputValue
		TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TextLabel.BackgroundTransparency = 1.000
		TextLabel.Size = UDim2.new(1, 0, 1, 0)
		TextLabel.Font = Enum.Font.Gotham
		TextLabel.Text = default or "0"
		TextLabel.TextColor3 = Color3.fromRGB(162, 162, 162)
		TextLabel.TextSize = 14.000
		TextLabel.TextWrapped = true

		local Value = 0

		local Connection;
		table.insert(Funcs.connections, UIS.InputEnded:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 then
				if(Connection) then
					TS:Create(TextLabel, TweenInfo.new(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {TextColor3 = Color3.fromRGB(81, 84, 90)}):Play();
					TS:Create(FeatureTitle, TweenInfo.new(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {TextColor3 = Color3.fromRGB(81, 84, 90)}):Play();
					TS:Create(box, TweenInfo.new(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {BackgroundColor3 = Color3.fromRGB(99, 105, 113)}):Play();
					TS:Create(ColoredLine, TweenInfo.new(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {BackgroundTransparency = 0.65}):Play();
					--TS:Create(Accent, ti(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {BackgroundTransparency = 0.65}):Play();
					Connection:Disconnect();
					Connection = nil;
				end;
			end;
		end));

		table.insert(Funcs.connections, Slider.MouseButton1Down:Connect(function()
			if(Connection) then
				Connection:Disconnect();
			end;
			TS:Create(TextLabel, TweenInfo.new(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {TextColor3 = Color3.fromRGB(255, 255, 255)}):Play();
			TS:Create(FeatureTitle, TweenInfo.new(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {TextColor3 = Color3.fromRGB(255, 255, 255)}):Play();
			TS:Create(box, TweenInfo.new(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {BackgroundColor3 = Color3.fromRGB(255, 255, 255)}):Play();
			TS:Create(ColoredLine, TweenInfo.new(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {BackgroundTransparency = 0}):Play();
			--TS:Create(Accent, ti(toggleFuncs.tweenTime, Enum.EasingStyle.Sine, Enum.EasingDirection.In), {BackgroundTransparency = 0}):Play();

			Connection = RS.Heartbeat:Connect(function()
				local mouse = UIS:GetMouseLocation();
				local percent = math.clamp((mouse.X - SliderBG.AbsolutePosition.X) / (SliderBG.AbsoluteSize.X), 0, 1);
				local Value = min + (max - min) * percent;

				local NewValue = percent * 99.9
				ColoredLine:TweenSize(UDim2.new(NewValue/100, 4, 1, 0),Enum.EasingDirection.Out,Enum.EasingStyle.Quad,0.1,true,nil)
				box:TweenPosition(UDim2.new(NewValue/100, 0, 0.5, 0),Enum.EasingDirection.Out,Enum.EasingStyle.Quad,0.1,true,nil)




				TextLabel.Text = (Value)
				toggleFuncs.current_value = Value
				pcall(Callback, Value) 
			end);
		end));

		function toggleFuncs:Set(val)
			local percval = val
			if math.abs(min) ~= min then
				percval = val + math.abs(min)
			elseif min ~= 0 then
				percval = val - math.abs(min)
			end
			local percent = (percval/(max-min));
			local Value = val;

			local NewValue = percent * 99.9
			ColoredLine:TweenSize(UDim2.new(NewValue/100, 4, 1, 0),Enum.EasingDirection.Out,Enum.EasingStyle.Quad,0.1,true,nil)
			box:TweenPosition(UDim2.new(NewValue/100, 0, 0.5, 0),Enum.EasingDirection.Out,Enum.EasingStyle.Quad,0.1,true,nil)

			TextLabel.Text = (Value)
			toggleFuncs.current_value = Value
			pcall(Callback, Value) 
		end

		TextLabel.FocusLost:Connect(function()
			local toNum 
			pcall(function()
				toNum = tonumber(TextLabel.Text)
			end)
			if toNum then
				toNum = math.clamp(toNum, min, max)
				toggleFuncs:Set(toNum)
			end
		end)

		function toggleFuncs:AddToolTip(Text)
			--Library:AddToolTip(ScrollingFrame, ToggleBG, toggleFuncs.tweenTime, Text)
		end

		toggleFuncs:Set(default or 0)

		table.insert(Library.thingsToSet, {functions = toggleFuncs})

		components[Title] = {
			component_name = Title;
			component_minimum = min;
			component_maximium = max;
			component_default = default;
			component_callback = Callback;
			component_table = toggleFuncs;
			component_type = "Slider";
		}

		table.insert(Flags, {
			name = Title, 
			tb = toggleFuncs
		})

		return toggleFuncs;

	end

	function Funcs:NewDropdown(Title, list, default, callback, parent)
		local properties = {
			tweenTime = 0.2;
			cooldown = 0.5;
			lastTimed = 0;
			lastOpened = 0;
			selected = default;
			connections = {};
			components = {};
			open = false;
		}
		components[Title] = {
			component_name = Title;
			component_list = list;
			component_default = default;
			component_concat = "";
			component_callback = callback;
			component_type = "Dropdown";
			component_table = properties;
		}
		list = list or {"N/A"};
		callback = callback or function() end;

		local Dropdown = Instance.new("ImageLabel")
		local UICorner_28 = Instance.new("UICorner")
		local DropTop = Instance.new("ImageButton")
		local UICorner_29 = Instance.new("UICorner")
		local ToggleBG_6 = Instance.new("ImageLabel")
		local Title_10 = Instance.new("TextLabel")
		local UIPadding_12 = Instance.new("UIPadding")
		local CornerHider = Instance.new("Frame")
		local UIListLayout_8 = Instance.new("UIListLayout")
		local Frame_3 = Instance.new("Frame")
		local Frame_4 = Instance.new("Frame")
		local ScrollingFrame_2 = Instance.new("ScrollingFrame")
		local UIListLayout_9 = Instance.new("UIListLayout")

		Dropdown.Name = "Dropdown"
		Dropdown.Parent = parent or Container
		Dropdown.BackgroundColor3 = Color3.fromRGB(37, 34, 42)
		Dropdown.Position = UDim2.new(0.0173160173, 0, 0.30127424, 0)
		Dropdown.Size = UDim2.new(1, -24, 0, 0)
		Dropdown.BackgroundTransparency = 1
		--Dropdown.AutoButtonColor = false
		Dropdown.AutomaticSize = Enum.AutomaticSize.Y
		Dropdown.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"
		Dropdown.ImageTransparency = 1.000

		UICorner_28.CornerRadius = UDim.new(0, 4)
		UICorner_28.Parent = Dropdown

		DropTop.Name = "DropTop"
		DropTop.Parent = Dropdown
		DropTop.BackgroundColor3 = Color3.fromRGB(13, 13, 15)
		DropTop.BackgroundTransparency = 0
		DropTop.Size = UDim2.new(1, 0, 0, 38)
		DropTop.AutoButtonColor = false
		DropTop.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"
		DropTop.ImageTransparency = 1.000

		UICorner_29.CornerRadius = UDim.new(0, 4)
		UICorner_29.Parent = DropTop

		ToggleBG_6.Name = "ToggleBG"
		ToggleBG_6.Parent = DropTop
		ToggleBG_6.AnchorPoint = Vector2.new(1, 0.5)
		ToggleBG_6.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		ToggleBG_6.BackgroundTransparency = 1.000
		ToggleBG_6.Size = UDim2.new(0, 38, 0, 38)
		--ToggleBG_6.AutoButtonColor = false
		ToggleBG_6.AnchorPoint = Vector2.new(0,0.5)
		ToggleBG_6.Position = UDim2.new(0.9,0,0.5,0)
		ToggleBG_6.Image = "rbxassetid://6034818372"
		ToggleBG_6.ImageColor3 = Color3.fromRGB(113, 94, 241)

		Title_10.Size = UDim2.new(0, 669, 0, 55)
		Title_10.Position = UDim2.new(0,0,0.5,0)
		Title_10.AnchorPoint = Vector2.new(0,0.5)
		Title_10.Name = "FeatureTitle"
		Title_10.Parent = DropTop
		Title_10.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_10.BackgroundTransparency = 1.000
		Title_10.Font = Enum.Font.Gotham
		Title_10.Text = Title
		Title_10.TextColor3 = Color3.fromRGB(91, 91, 91)--Color3.fromRGB(162, 162, 162)
		Title_10.TextSize = 14.000
		Title_10.TextXAlignment = Enum.TextXAlignment.Left

		UIPadding_12.Parent = Title_10
		UIPadding_12.PaddingLeft = UDim.new(0, 12)

		CornerHider.Name = "CornerHider"
		CornerHider.Parent = DropTop
		CornerHider.AnchorPoint = Vector2.new(0, 1)
		CornerHider.BackgroundColor3 = Color3.fromRGB(48, 45, 53)
		CornerHider.BackgroundTransparency = 1.000
		CornerHider.BorderSizePixel = 0
		CornerHider.Position = UDim2.new(0, 0, 1, 0)
		CornerHider.Size = UDim2.new(1, 0, 0, 8)

		UIListLayout_8.Parent = Dropdown
		UIListLayout_8.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout_8.Padding = UDim.new(0, 0)-- -4)

		Frame_3.Parent = Dropdown
		Frame_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Frame_3.BackgroundTransparency = 1.000
		Frame_3.LayoutOrder = 1
		Frame_3.ZIndex = 0
		Frame_3.BorderSizePixel = 0
		Frame_3.Position = UDim2.new(0, 0, 0.24647671, 0)
		--Frame_3.Size = UDim2.new(1, 0, 0.0144986296, 152)
		Frame_3.Size = UDim2.new(1, 0, 0, 0)

		Frame_4.Parent = Frame_3
		Frame_4.AnchorPoint = Vector2.new(0.5, 0)
		Frame_4.BackgroundColor3 = Color3.fromRGB(31, 31, 36)
		Frame_4.BackgroundTransparency = 0.35
		Frame_4.LayoutOrder = 1
		Frame_4.BorderSizePixel = 0
		Frame_4.Position = UDim2.new(0.5, 0, 0, 0)
		Frame_4.Size = UDim2.new(1, -12, 1, 0)

		local UICorner_35 = Instance.new("UICorner")
		UICorner_35.CornerRadius = UDim.new(0, 6)
		UICorner_35.Parent = Frame_4

		ScrollingFrame_2.Parent = Frame_4
		ScrollingFrame_2.Active = true
		ScrollingFrame_2.BackgroundColor3 = Color3.fromRGB(30, 27, 38)
		ScrollingFrame_2.BackgroundTransparency = 1.000
		ScrollingFrame_2.BorderSizePixel = 0
		ScrollingFrame_2.LayoutOrder = 1
		ScrollingFrame_2.Size = UDim2.new(1, 0, 1, 0)
		ScrollingFrame_2.CanvasSize = UDim2.new(0, 0, 0, 0)
		ScrollingFrame_2.AutomaticCanvasSize = Enum.AutomaticSize.Y
		ScrollingFrame_2.ScrollBarThickness = 0

		UIListLayout_9.Parent = ScrollingFrame_2
		UIListLayout_9.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout_9.Padding = UDim.new(0, 8)

		local UIPadding_13 = Instance.new("UIPadding")
		UIPadding_13.Parent = ScrollingFrame_2
		UIPadding_13.PaddingBottom = UDim.new(0, 8)
		UIPadding_13.PaddingLeft = UDim.new(0, 8)
		UIPadding_13.PaddingRight = UDim.new(0, 8)
		UIPadding_13.PaddingTop = UDim.new(0, 12)

		local ValueText = Instance.new("TextLabel")
		local UIPadding = Instance.new("UIPadding")

		ValueText.Name = "Value"
		ValueText.Parent = DropTop
		ValueText.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		ValueText.BackgroundTransparency = 1.000
		ValueText.Size = UDim2.new(0.9, 0, 0, 55)
		ValueText.Font = Enum.Font.Gotham
		ValueText.Text = default or "Click to Select"
		ValueText.TextColor3 = Color3.fromRGB(113, 94, 241)
		ValueText.TextSize = 12.000
		ValueText.AnchorPoint = Vector2.new(0,0.5)
		ValueText.Position = UDim2.new(0,0,0.5,0)
		ValueText.TextXAlignment = Enum.TextXAlignment.Right

		UIPadding.Parent = ValueText
		UIPadding.PaddingLeft = UDim.new(0, 12)

		function properties:Close()
			properties.open = false

			spr.target(Frame_3, .75, 2.5, {
				Size = UDim2.new(1, 0, 0, 0)
			})
			spr.target(ToggleBG_6, .7, 2.5, {
				Rotation = 0
			})
		end

		function properties:Open()
			if properties.lastTimed + properties.cooldown > os.time() then 
				return 
			end

			properties.lastTimed = os.time();
			if properties.open then
				properties:Close()
				return
			else
				properties.open = true
				properties.lastOpened = os.clock()
			end

			local newList = list
			if type(list) == "function" then
				newList = list();
			end
			local buttons = {};

			for x,y in next, properties.components do
				y:Destroy()
			end
			properties.components = {}

			if type(newList) == "table" then
				for _, text in next, (newList) do

					local DropdownOption = Instance.new("TextButton")
					local Title_11 = Instance.new("TextLabel")
					local UICorner_30 = Instance.new("UICorner")

					DropdownOption.Name = "DropdownOption"
					DropdownOption.Parent = ScrollingFrame_2
					DropdownOption.BackgroundColor3 = Color3.fromRGB(13, 13, 13)
					DropdownOption.BorderSizePixel = 0
					DropdownOption.Size = UDim2.new(1, 0, 0, 34)
					DropdownOption.AutoButtonColor = false
					DropdownOption.Font = Enum.Font.SourceSans
					DropdownOption.Text = ""
					DropdownOption.TextColor3 = Color3.fromRGB(0, 0, 0)
					DropdownOption.TextSize = 14.000

					UICorner_30.CornerRadius = UDim.new(0, 4)
					UICorner_30.Parent = DropdownOption

					Title_11.Name = "Title"
					Title_11.Parent = DropdownOption
					Title_11.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					Title_11.BackgroundTransparency = 1.000
					Title_11.Size = UDim2.new(1, 0, 1, 0)
					Title_11.Font = Enum.Font.Gotham
					Title_11.Text = text
					Title_11.TextColor3 = Color3.fromRGB(113, 94, 241)
					Title_11.TextSize = 12.000


					table.insert(buttons, DropdownOption)
					table.insert(properties.components, DropdownOption)

					table.insert(properties.connections, DropdownOption.MouseButton1Down:Connect(function()
						ValueText.Text = text;
						properties.selected = text
						pcall(callback, text);
						properties:Close();
					end))
				end

			end
			spr.target(ToggleBG_6, .7, 2.5, {
				Rotation = 180
			})
			if #newList <= 3 then
				local pTop = 12
				local pBottom = 8
				local pDiff = 8
				local size = pTop + pBottom + (#newList*(pDiff+34)) - 6

				spr.target(Frame_3, .8, 3, {
					Size = UDim2.new(1, 0, 0, size)
				})
			else
				spr.target(Frame_3, .8, 3, {
					Size = UDim2.new(1, 0, 0.0144986296, 152)
				})
			end
		end

		function properties:Set(val)
			ValueText.Text = val;
			properties.selected = val
			pcall(callback, val);
			properties:Close();
		end

		table.insert(Library.thingsToSet, {functions = properties})
		--table.insert(Library.thingsToClose, properties)

		table.insert(properties.connections, DropTop.MouseButton1Down:Connect(properties.Open))

		table.insert(Flags, {
			name = Title, 
			tb = properties
		})

		return properties
	end
	
	function Funcs:NewButton(Title, callback, parent)
		local Button = Instance.new("ImageButton")
		local UICorner_26 = Instance.new("UICorner")
		local ToggleBG_5 = Instance.new("ImageLabel")
		local UICorner_27 = Instance.new("UICorner")
		local Title_9 = Instance.new("TextLabel")
		local UIListLayout_7 = Instance.new("UIListLayout")
		local ImageLabel = Instance.new("ImageLabel")
		local UIPadding_11 = Instance.new("UIPadding")

		Button.Name = "Button"
		Button.Parent = parent or Container
		--Button.BackgroundColor3 = Color3.fromRGB(48, 45, 53)
		Button.Position = UDim2.new(0.0173160173, 0, 0.0299999993, 0)
		Button.Size = UDim2.new(1, -24, 0, 36)
		Button.AutoButtonColor = false
		Button.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"
		Button.ImageTransparency = 1.000
		Button.BackgroundColor3 = Color3.fromRGB(13, 13, 15)

		UICorner_26.CornerRadius = UDim.new(0, 4)
		UICorner_26.Parent = Button

		ToggleBG_5.Name = "ToggleBG"
		ToggleBG_5.Parent = Button
		ToggleBG_5.AnchorPoint = Vector2.new(0.5, 0.5)
		ToggleBG_5.BackgroundColor3 = Color3.fromRGB(113, 94, 241)
		ToggleBG_5.BackgroundTransparency = 1.000
		ToggleBG_5.Position = UDim2.new(0.5, 0, 0.5, 0)
		ToggleBG_5.Size = UDim2.new(1, 0, 1, 0)
		ToggleBG_5.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"
		ToggleBG_5.ImageTransparency = 1.000

		local strk = Instance.new("UIStroke")
		strk.Parent = Button
		strk.Color = Color3.fromRGB(142, 125, 255)
		strk.Thickness = 0--1

		UICorner_27.CornerRadius = UDim.new(0, 4)
		UICorner_27.Parent = ToggleBG_5

		Title_9.Name = "Title"
		Title_9.Parent = ToggleBG_5
		Title_9.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_9.BackgroundTransparency = 1.000
		Title_9.LayoutOrder = 1
		Title_9.Position = UDim2.new(0.380620152, 0, 0, 0)
		Title_9.Size = UDim2.new(0, 10, 1, 0)
		Title_9.ZIndex = 2
		Title_9.AutomaticSize = Enum.AutomaticSize.X
		Title_9.Font = Enum.Font.Gotham
		Title_9.Text = Title
		Title_9.TextColor3 = Color3.fromRGB(98, 7, 255)
		Title_9.TextSize = 14.000
		Title_9.TextXAlignment = Enum.TextXAlignment.Left

		UIListLayout_7.Parent = ToggleBG_5
		UIListLayout_7.FillDirection = Enum.FillDirection.Horizontal
		UIListLayout_7.HorizontalAlignment = Enum.HorizontalAlignment.Center
		UIListLayout_7.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout_7.VerticalAlignment = Enum.VerticalAlignment.Center
		UIListLayout_7.Padding = UDim.new(0, 12)

		ImageLabel.Parent = ToggleBG_5
		ImageLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		ImageLabel.BackgroundTransparency = 1.000
		ImageLabel.Size = UDim2.new(0, 20, 0, 20)
		ImageLabel.Image = "rbxassetid://11432848110"
		ImageLabel.ImageColor3 = Color3.fromRGB(113, 94, 241)

		UIPadding_11.Parent = ToggleBG_5

		Button.MouseButton1Down:Connect(function()
			spr.target(ToggleBG_5, 0.7, 2.5, {
				BackgroundTransparency = 0.5
			})
		end)
		Button.MouseButton1Up:Connect(function()
			spr.target(ToggleBG_5, 0.7, 2.5, {
				BackgroundTransparency = 1
			})
		end)

		Button.MouseButton1Click:Connect(function()


			callback()
		end)
	end
	
	function Funcs:Open()
		Funcs.isOpen = true;
		Container.Visible = true;
		TextLabel.TextColor3 = Color3.fromRGB(255,255,255);
		TabButton.BackgroundTransparency = 0;
		TextLabelPath.Text = "Projects  /  Cheeto  / <font color=\"#715EF1\">  "..Title.."</font>"
		--PrimaryColors[TabButton] = {"TextColor3"};

		Container.CanvasSize = UDim2.new(0, 0,0,Container.AbsoluteCanvasSize.Y)



		for _, tab in ipairs(Library.Tabs) do
			if tab.TabButton ~= TabButton then
				tab.Funcs:Close();
			end
		end

	end

	function Funcs:Close()
		Funcs.isOpen = false;
		Container.Visible = false;

		TextLabel.TextColor3 = Color3.fromRGB(118, 118, 118);
		TabButton.BackgroundTransparency = 1;
		--PrimaryColors[TabButton] = nil;

	end

	
	function Funcs:NewSection(Title)
		local returnFuncs = {}
		
		
		local sectionFrame = Instance.new("Frame")
		sectionFrame.BackgroundTransparency = 1
		sectionFrame.AutomaticSize = Enum.AutomaticSize.Y
		sectionFrame.Size = UDim2.new(1,0,0,10)
		sectionFrame.Parent = Container
		
		

		local UIListLayout = Instance.new("UIListLayout")
		local UIPadding = Instance.new("UIPadding")
		UIListLayout.Parent = sectionFrame
		UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout.Padding = UDim.new(0, 10)

		UIPadding.Parent = sectionFrame
		UIPadding.PaddingTop = UDim.new(0, 10)
		
		local sectionTitle = Instance.new("TextLabel")
		sectionTitle.Name = "sectionTitle"
		sectionTitle.Parent = sectionFrame
		sectionTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		sectionTitle.BackgroundTransparency = 1.000
		sectionTitle.Position = UDim2.new(0.104999967, 0, 0, 0)
		sectionTitle.Size = UDim2.new(1, 0, 0, 20)
		sectionTitle.Font = Enum.Font.Gotham
		sectionTitle.Text = Title
		sectionTitle.TextColor3 = Color3.fromRGB(91, 91, 91)--Color3.fromRGB(162, 162, 162)
		sectionTitle.TextSize = 14.000
		sectionTitle.TextXAlignment = Enum.TextXAlignment.Left
		
		local UIPadding = Instance.new("UIPadding")
		UIPadding.Parent = sectionTitle
		UIPadding.PaddingLeft = UDim.new(0, 15)
		UIPadding.PaddingBottom = UDim.new(0, -15)
		
		function returnFuncs:NewToggle(Title, default, Callback)
			return Funcs:NewToggle(Title, default, Callback, sectionFrame)
		end

		function returnFuncs:NewSlider(Title, min, max, default, Callback)
			return Funcs:NewSlider(Title, min, max, default, Callback, sectionFrame)
		end
		
		function returnFuncs:NewDropdown(Title, list, default, callback, parent)
			return Funcs:NewDropdown(Title, list, default, callback, sectionFrame)
		end
		
		function returnFuncs:NewButton(Title, callback, parent)
			return Funcs:NewButton(Title, callback, sectionFrame)
		end
		
		return returnFuncs
		
	end
	

	table.insert(Funcs.connections, TabButton.MouseButton1Down:Connect(function()
		if not Funcs.isOpen and Funcs.lastChanged + Funcs.cooldown <= os.time() then
			Funcs.lastChanged = os.time();
			Funcs:Open();
		end
	end))

	table.insert(Library.Tabs, {
		Title = Title,
		TabButton = TabButton;
		ContentBG = Container,
		Funcs = Funcs;
	})

	return Funcs
end

function Library:Init(tab)
	if tab and type(tab) == 'table' and rawget(tab, "Funcs") then
		tab.Funcs:Open();
	end
end

Library:SetTitle("Vortex")
Library:SetFooter("Welcome, "..(plr.DisplayName or plr.Name))

-- Start

local plr = game.Players.LocalPlayer
local rs = game:GetService("RunService")
```
## Create Title & Footing
```lua
Library:SetTitle("Cheeto")
Library:SetFooter("Welcome, "..(plr.DisplayName or plr.Name))
```
## Create Tab
```lua
local tab1 = Library:NewTab("Catching")
```
## Create Section
```lua
local sec1 = tab1:NewSection("Catching")
```
## Create Toggle
```lua
sec1:NewToggle("Magnets", false, function(v)

end)
```
## Create Slider
```lua
sec1:NewSlider("Magnet Range", 0, 15, 120, function(v)

end)
```
## Create Dropdown
```lua
sec1:NewDropdown("Magnet Type", {"Brute", "Regular", "Blantant", "League", "Twen"}, "Skibibi", function(v)

end)
```
