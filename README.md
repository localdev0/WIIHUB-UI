## Create Window
```lua
local lib = {}

local betterFont = Font.new("rbxassetid://12187372629")
betterFont.Weight = Enum.FontWeight.SemiBold
local cartoonFont = Font.new("rbxassetid://12187607287")
cartoonFont.Weight = Enum.FontWeight.SemiBold

function lib:CreateWindow(title)
	local wii = Instance.new("ScreenGui")
	local Main = Instance.new("Frame")
	local UIAspectRatioConstraint = Instance.new("UIAspectRatioConstraint")
	local UICorner = Instance.new("UICorner")
	local Topbar = Instance.new("Frame")
	local Line = Instance.new("Frame")
	local Navigation = Instance.new("ScrollingFrame")
	local UIListLayout = Instance.new("UIListLayout")
	local UIPadding = Instance.new("UIPadding")
	local Title_3 = Instance.new("TextLabel")
	local Box = Instance.new("Frame")
	local UICorner_4 = Instance.new("UICorner")
	local UIStroke = Instance.new("UIStroke")
	local PlayerName = Instance.new("TextLabel")
	local PlayerIcon = Instance.new("ImageLabel")
	local UICorner_5 = Instance.new("UICorner")
	local UIAspectRatioConstraint_4 = Instance.new("UIAspectRatioConstraint")
	local Content = Instance.new("Frame")
	local Line_2 = Instance.new("Frame")
	
	wii.Name = "wii"
	wii.Parent = game:GetService("CoreGui")
	wii.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	wii.ResetOnSpawn = false

	Main.Name = "Main"
	Main.Parent = wii
	Main.BackgroundColor3 = Color3.fromRGB(17, 18, 22)
	Main.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Main.BorderSizePixel = 0
	Main.Position = UDim2.new(0.247613221, 0, 0.214157507, 0)
	Main.Size = UDim2.new(0, 642, 0, 412)

	UIAspectRatioConstraint.Parent = Main
	UIAspectRatioConstraint.AspectRatio = 1.559

	UICorner.CornerRadius = UDim.new(0, 4)
	UICorner.Parent = Main

	Topbar.Name = "Topbar"
	Topbar.Parent = Main
	Topbar.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Topbar.BackgroundTransparency = 1.000
	Topbar.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Topbar.BorderSizePixel = 0
	Topbar.Size = UDim2.new(0, 642, 0, 55)

	Line.Name = "Line"
	Line.Parent = Main
	Line.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
	Line.BackgroundTransparency = 0.500
	Line.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Line.BorderSizePixel = 0
	Line.Position = UDim2.new(0, 0, 0.131130844, 0)
	Line.Size = UDim2.new(0, 642, 0, 1)

	Navigation.Name = "Navigation"
	Navigation.Parent = Main
	Navigation.Active = true
	Navigation.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Navigation.BackgroundTransparency = 1.000
	Navigation.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Navigation.BorderSizePixel = 0
	Navigation.Position = UDim2.new(0, 0, 0.13113077, 0)
	Navigation.Size = UDim2.new(0, 145, 0, 357)
	Navigation.ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0)
	Navigation.ScrollBarThickness = 0

	UIListLayout.Parent = Navigation
	UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
	UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIListLayout.Padding = UDim.new(0, 6)

	UIPadding.Parent = Navigation
	UIPadding.PaddingTop = UDim.new(0, 10)
	
	Line_2.Name = "Line"
	Line_2.Parent = Main
	Line_2.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
	Line_2.BackgroundTransparency = 0.500
	Line_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Line_2.BorderSizePixel = 0
	Line_2.Position = UDim2.new(0.224299058, 0, 0.13113077, 0)
	Line_2.Size = UDim2.new(0, 1, 0, 355)

	Title_3.Name = "Title"
	Title_3.Parent = Main
	Title_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Title_3.BackgroundTransparency = 1.000
	Title_3.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Title_3.BorderSizePixel = 0
	Title_3.Position = UDim2.new(0.0346283242, 0, 0.0292162951, 0)
	Title_3.Size = UDim2.new(0, 99, 0, 32)
	Title_3.FontFace = cartoonFont
	Title_3.Text = title
	Title_3.TextColor3 = Color3.fromRGB(255, 255, 255)
	Title_3.TextScaled = true
	Title_3.TextSize = 14.000
	Title_3.TextWrapped = true
	Title_3.TextXAlignment = Enum.TextXAlignment.Left

	Box.Name = "Box"
	Box.Parent = Main
	Box.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Box.BackgroundTransparency = 1.000
	Box.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Box.BorderSizePixel = 0
	Box.Position = UDim2.new(0.728971958, 0, 0.0291401874, 0)
	Box.Size = UDim2.new(0, 160, 0, 32)

	UICorner_4.CornerRadius = UDim.new(0, 6)
	UICorner_4.Parent = Box

	UIStroke.Parent = Box
	UIStroke.Color = Color3.fromRGB(71, 71, 71)
	UIStroke.Thickness = 0.700

	PlayerName.Name = "PlayerName"
	PlayerName.Parent = Box
	PlayerName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	PlayerName.BackgroundTransparency = 1.000
	PlayerName.BorderColor3 = Color3.fromRGB(0, 0, 0)
	PlayerName.BorderSizePixel = 0
	PlayerName.Position = UDim2.new(0.203125, 0, 0.03125, 0)
	PlayerName.Size = UDim2.new(0, 113, 0, 31)
	PlayerName.FontFace = betterFont
	PlayerName.Text = "Welcome, " .. game:GetService("Players").LocalPlayer.Name
	PlayerName.TextColor3 = Color3.fromRGB(255, 255, 255)
	PlayerName.TextSize = 18.000
	PlayerName.TextWrapped = true

	PlayerIcon.Name = "PlayerIcon"
	PlayerIcon.Parent = Box
	PlayerIcon.BackgroundColor3 = Color3.fromRGB(121, 121, 121)
	PlayerIcon.BorderColor3 = Color3.fromRGB(0, 0, 0)
	PlayerIcon.BorderSizePixel = 0
	PlayerIcon.Position = UDim2.new(0.0375000015, 0, 0.09375, 0)
	PlayerIcon.Size = UDim2.new(0, 35, 0, 25)
	PlayerIcon.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"

	UICorner_5.CornerRadius = UDim.new(1, 0)
	UICorner_5.Parent = PlayerIcon

	UIAspectRatioConstraint_4.Parent = PlayerIcon
	UIAspectRatioConstraint_4.AspectRatio = 1.060

	Content.Name = "Content"
	Content.Parent = Main
	Content.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Content.BackgroundTransparency = 1.000
	Content.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Content.BorderSizePixel = 0
	Content.Position = UDim2.new(0.225856692, 0, 0.133559152, 0)
	Content.Size = UDim2.new(0, 496, 0, 356)
	
	local TweenService = game:GetService("TweenService")
	local UserInputService = game:GetService("UserInputService")

	local dragging
	local dragInput
	local dragStart
	local startPos

	local tweenInfo = TweenInfo.new(0, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

	local function update(input)
		local delta = input.Position - dragStart
		local targetPos = UDim2.new(
			startPos.X.Scale, 
			startPos.X.Offset + delta.X, 
			startPos.Y.Scale, 
			startPos.Y.Offset + delta.Y
		)

		local tween = TweenService:Create(Main, tweenInfo, {Position = targetPos})
		tween:Play()
	end

	Main.InputBegan:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
			dragging = true
			dragStart = input.Position
			startPos = Main.Position

			input.Changed:Connect(function()
				if input.UserInputState == Enum.UserInputState.End then
					dragging = false
				end
			end)
		end
	end)

	Main.InputChanged:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
			dragInput = input
		end
	end)

	UserInputService.InputChanged:Connect(function(input)
		if input == dragInput and dragging then
			update(input)
		end
	end)

	local function toggleMainVisibility(input)
		if input.UserInputType == Enum.UserInputType.Keyboard and input.KeyCode == Enum.KeyCode.LeftControl then
			Main.Visible = not Main.Visible
		end
	end

	UserInputService.InputBegan:Connect(function(input, gameProcessed)
		if not gameProcessed then
			toggleMainVisibility(input)
		end
	end)
	
	local function UAIT_script()
		local script = Instance.new('LocalScript', PlayerIcon)

		local player = game:GetService("Players").LocalPlayer
		local imageLabel = script.Parent

		local function setProfilePicture()
			local success, url = pcall(function()
				return "https://www.roblox.com/headshot-thumbnail/image?userId=" .. player.UserId .. "&width=420&height=420&format=png"
			end)

			if success then
				imageLabel.Image = url
			else
				warn("Failed to load profile picture.")
			end
		end

		setProfilePicture()
	end
	coroutine.wrap(UAIT_script)()
	
	local selectedTab = nil

	function lib:CreateTab(title, id)
		local tab = {}

		local Tab = Instance.new("ImageButton")
		local UIGradient_2 = Instance.new("UIGradient")
		local UICorner_3 = Instance.new("UICorner")
		local Title_2 = Instance.new("TextLabel")
		local Icon_2 = Instance.new("ImageLabel")
		local UIAspectRatioConstraint_3 = Instance.new("UIAspectRatioConstraint")
		local Items = Instance.new("ScrollingFrame")
		local UIListLayout_2 = Instance.new("UIListLayout")
		local UIPadding_2 = Instance.new("UIPadding")

		Tab.Name = "Tab"
		Tab.Parent = Navigation
		Tab.BackgroundColor3 = Color3.fromRGB(71, 71, 71)
		Tab.BackgroundTransparency = 1.000
		Tab.Size = UDim2.new(0, 121, 0, 39)
		Tab.AutoButtonColor = false

		UIGradient_2.Transparency = NumberSequence.new{NumberSequenceKeypoint.new(0.00, 0.00), NumberSequenceKeypoint.new(1.00, 1.00)}
		UIGradient_2.Parent = Tab

		UICorner_3.CornerRadius = UDim.new(0, 6)
		UICorner_3.Parent = Tab

		Title_2.Name = "Title"
		Title_2.Parent = Tab
		Title_2.BackgroundTransparency = 1.000
		Title_2.Position = UDim2.new(0.330578506, 0, 0.230769232, 0)
		Title_2.Size = UDim2.new(0, 81, 0, 19)
		Title_2.Font = Enum.Font.Gotham
		Title_2.Text = title
		Title_2.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_2.TextScaled = true
		Title_2.TextTransparency = 0.400
		Title_2.TextXAlignment = Enum.TextXAlignment.Left

		Icon_2.Name = "Icon"
		Icon_2.Parent = Tab
		Icon_2.BackgroundTransparency = 1.000
		Icon_2.Position = UDim2.new(0.0495867766, 0, 0.230769232, 0)
		Icon_2.Size = UDim2.new(0, 22, 0, 20)
		Icon_2.Image = "rbxassetid://" .. id
		Icon_2.ImageTransparency = 0.400

		UIAspectRatioConstraint_3.Parent = Icon_2

		Items.Name = "Items"
		Items.Parent = Content
		Items.Active = true
		Items.BackgroundTransparency = 1.000
		Items.Size = UDim2.new(0, 496, 0, 356)
		Items.ScrollBarThickness = 0
		Items.Visible = false

		UIListLayout_2.Parent = Items
		UIListLayout_2.HorizontalAlignment = Enum.HorizontalAlignment.Center
		UIListLayout_2.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout_2.Padding = UDim.new(0, 6)

		UIPadding_2.Parent = Items
		UIPadding_2.PaddingTop = UDim.new(0, 8)

		local TweenService = game:GetService("TweenService")

		local function tweenTransparency(object, transparency, time)
			local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
			local goal = {Transparency = transparency}
			local tween = TweenService:Create(object, tweenInfo, goal)
			tween:Play()
		end

		local function tweenTextTransparency(object, transparency, time)
			local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
			local goal = {TextTransparency = transparency}
			local tween = TweenService:Create(object, tweenInfo, goal)
			tween:Play()
		end

		local function tweenImageTransparency(object, transparency, time)
			local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
			local goal = {ImageTransparency = transparency}
			local tween = TweenService:Create(object, tweenInfo, goal)
			tween:Play()
		end

		local function tweenPadding(object, padding, time)
			local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
			local goal = {PaddingTop = padding}
			local tween = TweenService:Create(object, tweenInfo, goal)
			tween:Play()
		end

		if selectedTab == nil then
			selectedTab = Tab
			tweenTextTransparency(Title_2, 0, 0.2)
			tweenImageTransparency(Icon_2, 0, 0.2)
			tweenTransparency(Tab, 0, 0.2)
			Items.Visible = true
		else
			tweenTextTransparency(Title_2, 0.4, 0.2)
			tweenImageTransparency(Icon_2, 0.4, 0.2)
			tweenTransparency(Tab, 1, 0.2)
			Items.Visible = false
		end

		Tab.MouseButton1Click:Connect(function()
			if selectedTab then
				local selectedTitle = selectedTab:FindFirstChild("Title")
				local selectedIcon = selectedTab:FindFirstChild("Icon")
				local selectedItems = Content:FindFirstChild("Items")
				local selectedPadding = selectedItems and selectedItems:FindFirstChild("UIPadding")

				if selectedTitle then
					tweenTextTransparency(selectedTitle, 0.4, 0.2)
				end
				if selectedIcon then
					tweenImageTransparency(selectedIcon, 0.4, 0.2)
				end
				if selectedPadding then
					tweenPadding(selectedPadding, UDim.new(0, 6), 0.2)
				end
				selectedTab.BackgroundTransparency = 1
				if selectedItems then
					selectedItems.Visible = false
				end
			end
			
			task.wait(0.3)

			selectedTab = Tab
			tweenTextTransparency(Title_2, 0, 0.2)
			tweenImageTransparency(Icon_2, 0, 0.2)
			tweenTransparency(Tab, 0, 0.2)
			Items.Visible = true
		end)
		
		function tab:CreateButton(title, callback)
			local Button = Instance.new("ImageButton")
			local UICorner_6 = Instance.new("UICorner")
			local Title_4 = Instance.new("TextLabel")
			
			Button.Name = "Button"
			Button.Parent = Items
			Button.BackgroundColor3 = Color3.fromRGB(31, 32, 36)
			Button.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Button.BorderSizePixel = 0
			Button.Position = UDim2.new(0.03125, 0, 0, 0)
			Button.Size = UDim2.new(0, 465, 0, 40)
			Button.AutoButtonColor = false

			UICorner_6.CornerRadius = UDim.new(0, 4)
			UICorner_6.Parent = Button

			Title_4.Name = "Title"
			Title_4.Parent = Button
			Title_4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title_4.BackgroundTransparency = 1.000
			Title_4.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Title_4.BorderSizePixel = 0
			Title_4.Position = UDim2.new(0, 0, 0.255769342, 0)
			Title_4.Size = UDim2.new(0, 464, 0, 18)
			Title_4.FontFace = betterFont
			Title_4.Text = title
			Title_4.TextColor3 = Color3.fromRGB(255, 255, 255)
			Title_4.TextScaled = true
			Title_4.TextSize = 14.000
			Title_4.TextTransparency = 0.400
			Title_4.TextWrapped = true
			
			Button.MouseButton1Click:Connect(function()
				if callback then
					callback()
				end
			end)
		end
		
		function tab:CreateDivider()
			local Divider = Instance.new("Frame")
			local Hitbox = Instance.new("Frame")
			
			Divider.Name = "Divider"
			Divider.Parent = Items
			Divider.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Divider.BackgroundTransparency = 1.000
			Divider.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Divider.BorderSizePixel = 0
			Divider.Position = UDim2.new(0.0332661308, 0, 0.660919547, 0)
			Divider.Size = UDim2.new(0, 463, 0, 30)

			Hitbox.Name = "Hitbox"
			Hitbox.Parent = Divider
			Hitbox.BackgroundColor3 = Color3.fromRGB(31, 32, 36)
			Hitbox.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Hitbox.BorderSizePixel = 0
			Hitbox.Position = UDim2.new(0.00215982716, 0, 0.474999994, 0)
			Hitbox.Size = UDim2.new(0, 463, 0, 4)
		end
		
		function tab:CreateTextBox(title, callback)
			local TextBoxButton = Instance.new("ImageButton")
			local UICorner_7 = Instance.new("UICorner")
			local Title_5 = Instance.new("TextLabel")
			local Box_2 = Instance.new("Frame")
			local UIStroke_2 = Instance.new("UIStroke")
			local Textbox = Instance.new("TextBox")
			
			TextBoxButton.Name = "TextBox"
			TextBoxButton.Parent = Items
			TextBoxButton.BackgroundColor3 = Color3.fromRGB(31, 32, 36)
			TextBoxButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
			TextBoxButton.Position = UDim2.new(-0.00302419346, 0, 0.12931034, 0)
			TextBoxButton.Size = UDim2.new(0, 465, 0, 40)
			TextBoxButton.AutoButtonColor = false

			UICorner_7.CornerRadius = UDim.new(0, 4)
			UICorner_7.Parent = TextBoxButton

			Title_5.Name = "Title"
			Title_5.Parent = TextBoxButton
			Title_5.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title_5.BackgroundTransparency = 1.000
			Title_5.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Title_5.BorderSizePixel = 0
			Title_5.Position = UDim2.new(0.0258064512, 0, 0.255769342, 0)
			Title_5.Size = UDim2.new(0, 210, 0, 18)
			Title_5.FontFace = betterFont
			Title_5.Text = title
			Title_5.TextColor3 = Color3.fromRGB(255, 255, 255)
			Title_5.TextScaled = true
			Title_5.TextSize = 14.000
			Title_5.TextTransparency = 0.400
			Title_5.TextWrapped = true
			Title_5.TextXAlignment = Enum.TextXAlignment.Left

			Box_2.Name = "Box"
			Box_2.Parent = TextBoxButton
			Box_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Box_2.BackgroundTransparency = 1.000
			Box_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Box_2.BorderSizePixel = 0
			Box_2.Position = UDim2.new(0.731182814, 0, 0.174999997, 0)
			Box_2.Size = UDim2.new(0, 100, 0, 26)

			UIStroke_2.Parent = Box_2
			UIStroke_2.Color = Color3.fromRGB(71, 71, 71)
			UIStroke_2.Thickness = 1.500

			Textbox.Name = "Textbox"
			Textbox.Parent = Box_2
			Textbox.Active = false
			Textbox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Textbox.BackgroundTransparency = 1.000
			Textbox.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Textbox.BorderSizePixel = 0
			Textbox.Position = UDim2.new(-0.00419372553, 0, 0.140384376, 0)
			Textbox.Selectable = false
			Textbox.Size = UDim2.new(0, 101, 0, 18)
			Textbox.FontFace = betterFont
			Textbox.PlaceholderText = "Enter"
			Textbox.Text = ""
			Textbox.TextColor3 = Color3.fromRGB(255, 255, 255)
			Textbox.TextScaled = true
			Textbox.TextSize = 14.000
			Textbox.TextTransparency = 0.400
			Textbox.TextWrapped = true
			
			Textbox.FocusLost:Connect(function(enterPressed)
				if enterPressed then
					callback(Textbox.Text)
				end
			end)
		end
		
		function tab:CreateSlider(title, min, max, default, callback)
			local Slider = Instance.new("ImageButton")
			local UICorner_8 = Instance.new("UICorner")
			local Title_6 = Instance.new("TextLabel")
			local Box_3 = Instance.new("Frame")
			local UIStroke_3 = Instance.new("UIStroke")
			local Textbox_2 = Instance.new("TextBox")
			local UICorner_9 = Instance.new("UICorner")
			local SliderBack = Instance.new("Frame")
			local UICorner_10 = Instance.new("UICorner")
			local Draggable = Instance.new("Frame")
			local UICorner_11 = Instance.new("UICorner")

			Slider.Name = "Slider"
			Slider.Parent = Items
			Slider.BackgroundColor3 = Color3.fromRGB(31, 32, 36)
			Slider.BorderSizePixel = 0
			Slider.Position = UDim2.new(0.029, 0, 0.247, 0)
			Slider.Size = UDim2.new(0, 465, 0, 40)
			Slider.AutoButtonColor = false

			UICorner_8.CornerRadius = UDim.new(0, 4)
			UICorner_8.Parent = Slider

			Title_6.Name = "Title"
			Title_6.Parent = Slider
			Title_6.BackgroundTransparency = 1.0
			Title_6.Position = UDim2.new(0.026, 0, 0.256, 0)
			Title_6.Size = UDim2.new(0, 210, 0, 18)
			Title_6.FontFace = betterFont
			Title_6.Text = title
			Title_6.TextColor3 = Color3.fromRGB(255, 255, 255)
			Title_6.TextScaled = true
			Title_6.TextTransparency = 0.4
			Title_6.TextXAlignment = Enum.TextXAlignment.Left

			Box_3.Name = "Box"
			Box_3.Parent = Slider
			Box_3.BackgroundTransparency = 1.0
			Box_3.Position = UDim2.new(0.907, 0, 0.175, 0)
			Box_3.Size = UDim2.new(0, 31, 0, 26)
			UIStroke_3.Parent = Box_3
			UIStroke_3.Color = Color3.fromRGB(71, 71, 71)
			UIStroke_3.Thickness = 1.5

			Textbox_2.Name = "Textbox"
			Textbox_2.Parent = Box_3
			Textbox_2.BackgroundTransparency = 1.0
			Textbox_2.Position = UDim2.new(0.188, 0, 0.140, 0)
			Textbox_2.Size = UDim2.new(0, 20, 0, 18)
			Textbox_2.FontFace = betterFont
			Textbox_2.Text = tostring(default)
			Textbox_2.TextColor3 = Color3.fromRGB(255, 255, 255)
			Textbox_2.TextSize = 14.0
			Textbox_2.TextTransparency = 0.4

			UICorner_9.CornerRadius = UDim.new(0, 4)
			UICorner_9.Parent = Box_3

			SliderBack.Name = "SliderBack"
			SliderBack.Parent = Slider
			SliderBack.BackgroundColor3 = Color3.fromRGB(106, 106, 106)
			SliderBack.Position = UDim2.new(0.396, 0, 0.425, 0)
			SliderBack.Size = UDim2.new(0, 230, 0, 6)
			UICorner_10.CornerRadius = UDim.new(1, 0)
			UICorner_10.Parent = SliderBack

			Draggable.Name = "Draggable"
			Draggable.Parent = SliderBack
			Draggable.BackgroundColor3 = Color3.fromRGB(43, 175, 255)
			Draggable.Size = UDim2.new(0, 100, 0, 6)
			
			UICorner_11.CornerRadius = UDim.new(1, 0)
			UICorner_11.Parent = Draggable

			local UIS = game:GetService("UserInputService")
			local TweenService = game:GetService("TweenService")

			local currentValue = default
			local isDragging = false
			local touchID = nil

			local function UpdateSliderPosition()
				local percentage = math.clamp((currentValue - min) / (max - min), 0, 1)
				Textbox_2.Text = string.format("%.1f", currentValue)
				local targetSize = UDim2.new(percentage, 0, 1, 0)
				local tween = TweenService:Create(Draggable, TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Size = targetSize})
				tween:Play()
				callback(currentValue)
			end

			local function StartDragging(input)
				isDragging = true
				if input.UserInputType == Enum.UserInputType.Touch then
					touchID = input.UserInputIndex
				end
			end

			local function UpdateDragging(input)
				if not isDragging then return end
				local inputPosition = input.Position.X
				local sliderX = SliderBack.AbsolutePosition.X
				local sliderWidth = SliderBack.AbsoluteSize.X
				local newPercentage = math.clamp((inputPosition - sliderX) / sliderWidth, 0, 1)
				currentValue = min + (newPercentage * (max - min))
				currentValue = math.round(currentValue * 10) / 10
				UpdateSliderPosition()
			end

			local function StopDragging(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
					isDragging = false
					touchID = nil
				end
			end

			Slider.MouseButton1Down:Connect(StartDragging)
			UIS.InputChanged:Connect(UpdateDragging)
			UIS.InputEnded:Connect(StopDragging)

			Textbox_2.FocusLost:Connect(function()
				local newValue = tonumber(Textbox_2.Text)
				if newValue then
					currentValue = math.clamp(newValue, min, max)
					UpdateSliderPosition()
				end
			end)

			currentValue = default
			UpdateSliderPosition()
		end
		
		function tab:CreateToggle(title, default, callback)
			local Toggle = Instance.new("ImageButton")
			local UICorner_15 = Instance.new("UICorner")
			local Title_8 = Instance.new("TextLabel")
			local Slide_2 = Instance.new("Frame")
			local UICorner_16 = Instance.new("UICorner")
			local Wheel_2 = Instance.new("Frame")
			local UICorner_17 = Instance.new("UICorner")
			local UIAspectRatioConstraint_6 = Instance.new("UIAspectRatioConstraint")
			local UIStroke_5 = Instance.new("UIStroke")
			local UIGradient_4 = Instance.new("UIGradient")

			local TweenService = game:GetService("TweenService")

			Toggle.Name = "Toggle"
			Toggle.Parent = Items
			Toggle.BackgroundColor3 = Color3.fromRGB(31, 32, 36)
			Toggle.Size = UDim2.new(0, 465, 0, 40)
			Toggle.AutoButtonColor = false

			UICorner_15.CornerRadius = UDim.new(0, 4)
			UICorner_15.Parent = Toggle

			Title_8.Name = "Title"
			Title_8.Parent = Toggle
			Title_8.BackgroundTransparency = 1.0
			Title_8.Position = UDim2.new(0.0258, 0, 0.255, 0)
			Title_8.Size = UDim2.new(0, 210, 0, 18)
			Title_8.FontFace = betterFont
			Title_8.Text = title
			Title_8.TextColor3 = Color3.fromRGB(255, 255, 255)
			Title_8.TextScaled = true
			Title_8.TextTransparency = default and 0 or 0.4
			Title_8.TextXAlignment = Enum.TextXAlignment.Left

			Slide_2.Name = "Slide"
			Slide_2.Parent = Toggle
			Slide_2.BackgroundColor3 = default and Color3.fromRGB(43, 175, 255) or Color3.fromRGB(255, 255, 255)
			Slide_2.Position = UDim2.new(0.89, 0, 0.275, 0)
			Slide_2.Size = UDim2.new(0, 30, 0, 18)
			Slide_2.BackgroundTransparency = 0.6

			UICorner_16.CornerRadius = UDim.new(1, 0)
			UICorner_16.Parent = Slide_2

			Wheel_2.Name = "Wheel"
			Wheel_2.Parent = Slide_2
			Wheel_2.BackgroundColor3 = default and Color3.fromRGB(43, 175, 255) or Color3.fromRGB(255, 255, 255)
			Wheel_2.Position = default and UDim2.new(0.57, 0, -0.05, 0) or UDim2.new(-0.36, 0, -0.05, 0)
			Wheel_2.Size = UDim2.new(0, 27, 0, 21)

			UICorner_17.CornerRadius = UDim.new(1, 0)
			UICorner_17.Parent = Wheel_2

			UIAspectRatioConstraint_6.Parent = Wheel_2

			UIStroke_5.Parent = Toggle
			UIStroke_5.Color = Color3.fromRGB(255, 255, 255)
			UIStroke_5.Thickness = 0.8

			UIGradient_4.Color = ColorSequence.new({
				ColorSequenceKeypoint.new(0.00, Color3.fromRGB(17, 18, 22)),
				ColorSequenceKeypoint.new(1.00, Color3.fromRGB(121, 204, 255))
			})
			UIGradient_4.Offset = default and Vector2.new(0, 0) or Vector2.new(0, 1)
			UIGradient_4.Parent = UIStroke_5

			local toggled = default

			local function updateToggleState(state)
				toggled = state
				TweenService:Create(Title_8, TweenInfo.new(0.3), {TextTransparency = state and 0 or 0.4}):Play()
				TweenService:Create(UIStroke_5, TweenInfo.new(0.3), {Transparency = state and 0 or 1}):Play()
				TweenService:Create(Wheel_2, TweenInfo.new(0.3), {BackgroundColor3 = state and Color3.fromRGB(43, 175, 255) or Color3.fromRGB(255, 255, 255)}):Play()
				TweenService:Create(Wheel_2, TweenInfo.new(0.3), {Position = state and UDim2.new(0.57, 0, -0.05, 0) or UDim2.new(-0.36, 0, -0.05, 0)}):Play()
				TweenService:Create(Slide_2, TweenInfo.new(0.3), {BackgroundColor3 = state and Color3.fromRGB(43, 175, 255) or Color3.fromRGB(255, 255, 255)}):Play()

				if callback and type(callback) == "function" then
					callback(state)
				end
			end

			updateToggleState(default)

			Toggle.MouseButton1Click:Connect(function()
				updateToggleState(not toggled)
			end)
		end


		return tab
	end
	
	return lib
end
```
## Create UI
```lua
local wiihub = lib:CreateWindow("WIIHUB")
```
## Create Tab
```lua
local tab1 = lib:CreateTab("Main", 10723407389)
```
## Create Button
```lua
tab1:CreateButton('hello', function()
	print("pressed")
end)
```
## Create Divider
```lua
tab1:CreateDivider()
```
## Create Textbox
```lua
tab1:CreateTextBox("sel", function(input)
	print(input)
end)
```
## Create Slider
```lua
tab1:CreateSlider("vakye", 0, 25, 5, function(value)
	print(value)
end)
```
## Create Toggle
```lua
tab1:CreateToggle("switch", true, function(s)
	print(s)
end)
```
