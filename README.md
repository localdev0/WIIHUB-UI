## Get Stuff
```lua
local lib = {}
local CustomColor = Color3.fromRGB(83, 113, 241)

function lib:CreateWindow(title)
	local UI = Instance.new("ScreenGui")
	local Main = Instance.new("Frame")
	local UICorner = Instance.new("UICorner")
	local TopBar = Instance.new("Frame")
	local Icon = Instance.new("ImageLabel")
	local UIAspectRatioConstraint = Instance.new("UIAspectRatioConstraint")
	local Title = Instance.new("TextLabel")
	local ExitButton = Instance.new("ImageButton")
	local UIAspectRatioConstraint_2 = Instance.new("UIAspectRatioConstraint")
	local Subtitle = Instance.new("TextLabel")
	local Line = Instance.new("Frame")
	local Line_2 = Instance.new("Frame")
	local Line_3 = Instance.new("Frame")
	local Line_4 = Instance.new("Frame")
	local Navigation = Instance.new("ScrollingFrame")
	local UIListLayout = Instance.new("UIListLayout")
	local UIPadding = Instance.new("UIPadding")
	local Circle = Instance.new("Frame")
	local UIAspectRatioConstraint_3 = Instance.new("UIAspectRatioConstraint")
	local UICorner_4 = Instance.new("UICorner")
	local PlayerIcon = Instance.new("ImageLabel")
	local UICorner_5 = Instance.new("UICorner")
	local UIAspectRatioConstraint_4 = Instance.new("UIAspectRatioConstraint")
	local UIStroke = Instance.new("UIStroke")
	local PlayerName = Instance.new("TextLabel")
	local Content = Instance.new("Frame")
	
	UI.Name = "UI"
	UI.Parent = game:GetService("Players").LocalPlayer.PlayerGui or game:GetService("CoreGui")
	UI.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	UI.DisplayOrder = 999999999
	UI.ResetOnSpawn = false

	Main.Name = "Main"
	Main.Parent = UI
	Main.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
	Main.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Main.BorderSizePixel = 0
	Main.Position = UDim2.new(0, 364, 0, 128)
	Main.Size = UDim2.new(0, 606, 0, 357)

	UICorner.CornerRadius = UDim.new(0, 15)
	UICorner.Parent = Main

	TopBar.Name = "TopBar"
	TopBar.Parent = Main
	TopBar.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	TopBar.BackgroundTransparency = 1.000
	TopBar.BorderColor3 = Color3.fromRGB(0, 0, 0)
	TopBar.BorderSizePixel = 0
	TopBar.Size = UDim2.new(0, 606, 0, 55)

	Icon.Name = "Icon"
	Icon.Parent = TopBar
	Icon.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Icon.BackgroundTransparency = 1.000
	Icon.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Icon.BorderSizePixel = 0
	Icon.Position = UDim2.new(0.0231023096, 0, 0.165062368, 0)
	Icon.Size = UDim2.new(0, 42, 0, 38)
	Icon.Image = "rbxassetid://4483362458"
	Icon.ImageColor3 = CustomColor

	UIAspectRatioConstraint.Parent = Icon

	Title.Name = "Title"
	Title.Parent = TopBar
	Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Title.BackgroundTransparency = 1.000
	Title.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Title.BorderSizePixel = 0
	Title.Position = UDim2.new(0.115511551, 0, 0, 0)
	Title.Size = UDim2.new(0, 84, 0, 55)
	Title.Font = Enum.Font.GothamSemibold
	Title.Text = title
	Title.TextColor3 = Color3.fromRGB(255, 255, 255)
	Title.TextSize = 24.000
	Title.TextWrapped = true
	Title.TextXAlignment = Enum.TextXAlignment.Left

	ExitButton.Name = "ExitButton"
	ExitButton.Parent = TopBar
	ExitButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	ExitButton.BackgroundTransparency = 1.000
	ExitButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
	ExitButton.BorderSizePixel = 0
	ExitButton.Position = UDim2.new(0.93069309, 0, 0.236363634, 0)
	ExitButton.Size = UDim2.new(0, 30, 0, 38)
	ExitButton.Image = "rbxassetid://10747384394"
	ExitButton.ImageColor3 = Color3.fromRGB(51, 51, 51)
	
	ExitButton.MouseButton1Click:Connect(function()
		Main.Visible = false
	end)
	
	ExitButton.TouchTap:Connect(function()
		Main.Visible = false
	end)

	UIAspectRatioConstraint_2.Parent = ExitButton

	Subtitle.Name = "Subtitle"
	Subtitle.Parent = TopBar
	Subtitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Subtitle.BackgroundTransparency = 1.000
	Subtitle.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Subtitle.BorderSizePixel = 0
	Subtitle.Position = UDim2.new(0.288778871, 0, 0, 0)
	Subtitle.Size = UDim2.new(0, 111, 0, 55)
	Subtitle.Font = Enum.Font.GothamSemibold
	Subtitle.Text = "Projects / "..title.." / Catching"
	Subtitle.TextColor3 = Color3.fromRGB(71, 71, 71)
	Subtitle.TextSize = 17.000
	Subtitle.TextXAlignment = Enum.TextXAlignment.Left

	Line.Name = "Line"
	Line.Parent = Main
	Line.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
	Line.BackgroundTransparency = 0.500
	Line.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Line.BorderSizePixel = 0
	Line.Position = UDim2.new(0, 0, 0.15406163, 0)
	Line.Size = UDim2.new(0, 606, 0, 1)

	Line_2.Name = "Line"
	Line_2.Parent = Main
	Line_2.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
	Line_2.BackgroundTransparency = 0.500
	Line_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Line_2.BorderSizePixel = 0
	Line_2.Position = UDim2.new(0.265676558, 0, 0.15406163, 0)
	Line_2.Size = UDim2.new(0, 1, 0, 248)

	Line_3.Name = "Line"
	Line_3.Parent = Main
	Line_3.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
	Line_3.BackgroundTransparency = 0.500
	Line_3.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Line_3.BorderSizePixel = 0
	Line_3.Position = UDim2.new(0, 0, 0.848739505, 0)
	Line_3.Size = UDim2.new(0, 606, 0, 1)

	Line_4.Name = "Line"
	Line_4.Parent = Main
	Line_4.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
	Line_4.BackgroundTransparency = 0.500
	Line_4.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Line_4.BorderSizePixel = 0
	Line_4.Position = UDim2.new(0.265676558, 0, 0.0254297759, 0)
	Line_4.Size = UDim2.new(0, 1, 0, 35)

	Navigation.Name = "Navigation"
	Navigation.Parent = Main
	Navigation.Active = true
	Navigation.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Navigation.BackgroundTransparency = 1.000
	Navigation.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Navigation.BorderSizePixel = 0
	Navigation.Position = UDim2.new(0, 0, 0.15406163, 0)
	Navigation.Size = UDim2.new(0, 160, 0, 249)
	Navigation.ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0)
	Navigation.CanvasSize = UDim2.new(0, 0, 7, 0)
	Navigation.ScrollBarThickness = 0

	UIListLayout.Parent = Navigation
	UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
	UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIListLayout.Padding = UDim.new(0, 4)

	UIPadding.Parent = Navigation
	UIPadding.PaddingTop = UDim.new(0, 6)
	
	Circle.Name = "Circle"
	Circle.Parent = Main
	Circle.BackgroundColor3 = CustomColor
	Circle.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Circle.BorderSizePixel = 0
	Circle.Position = UDim2.new(0.920792103, 0, 0.868347347, 0)
	Circle.Size = UDim2.new(0, 41, 0, 46)

	UIAspectRatioConstraint_3.Parent = Circle

	UICorner_4.CornerRadius = UDim.new(1, 0)
	UICorner_4.Parent = Circle

	PlayerIcon.Name = "PlayerIcon"
	PlayerIcon.Parent = Circle
	PlayerIcon.BackgroundColor3 = CustomColor
	PlayerIcon.BackgroundTransparency = 1.000
	PlayerIcon.BorderColor3 = Color3.fromRGB(0, 0, 0)
	PlayerIcon.BorderSizePixel = 0
	PlayerIcon.Position = UDim2.new(0.048780486, 0, 0.048780486, 0)
	PlayerIcon.Size = UDim2.new(0, 37, 0, 37)
	PlayerIcon.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"

	UICorner_5.CornerRadius = UDim.new(1, 0)
	UICorner_5.Parent = PlayerIcon

	UIAspectRatioConstraint_4.Parent = PlayerIcon

	UIStroke.Parent = PlayerIcon
	UIStroke.Thickness = 1.300

	PlayerName.Name = "PlayerName"
	PlayerName.Parent = Main
	PlayerName.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	PlayerName.BackgroundTransparency = 1.000
	PlayerName.BorderColor3 = Color3.fromRGB(0, 0, 0)
	PlayerName.BorderSizePixel = 0
	PlayerName.Position = UDim2.new(0.0231023096, 0, 0.851540625, 0)
	PlayerName.Size = UDim2.new(0, 238, 0, 53)
	PlayerName.Font = Enum.Font.GothamSemibold
	PlayerName.Text = "Welcome, "..game:GetService("Players").LocalPlayer.Name
	PlayerName.TextColor3 = Color3.fromRGB(255, 255, 255)
	PlayerName.TextSize = 17.000
	PlayerName.TextXAlignment = Enum.TextXAlignment.Left

	Content.Name = "Content"
	Content.Parent = Main
	Content.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Content.BackgroundTransparency = 1.000
	Content.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Content.BorderSizePixel = 0
	Content.Position = UDim2.new(0.267326742, 0, 0.156862751, 0)
	Content.Size = UDim2.new(0, 444, 0, 247)
	
	local function HXOR_script()
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
	coroutine.wrap(HXOR_script)()
	
	local TweenService = game:GetService("TweenService")
	local UserInputService = game:GetService("UserInputService")

	local dragging
	local dragInput
	local dragStart
	local startPos

	local tweenInfo = TweenInfo.new(0.16, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

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
	
	local selectedTab = nil
	local activeTab = nil

	function lib:CreateTab(tabName)
		local Tab = Instance.new("ImageButton")
		local UICorner_3 = Instance.new("UICorner")
		local UIGradient_2 = Instance.new("UIGradient")
		local Title_3 = Instance.new("TextLabel")
		local Items = Instance.new("ScrollingFrame")
		local UIListLayout_2 = Instance.new("UIListLayout")
		local UIPadding_2 = Instance.new("UIPadding")

		Tab.Name = "Tab"
		Tab.Parent = Navigation
		Tab.BackgroundColor3 = CustomColor
		Tab.BackgroundTransparency = 1.0
		Tab.BorderSizePixel = 0
		Tab.Size = UDim2.new(0, 145, 0, 33)
		Tab.AutoButtonColor = false

		UICorner_3.CornerRadius = UDim.new(0, 6)
		UICorner_3.Parent = Tab

		UIGradient_2.Color = ColorSequence.new({
			ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 255, 255)),
			ColorSequenceKeypoint.new(1.00, Color3.fromRGB(117, 117, 117))
		})
		UIGradient_2.Offset = Vector2.new(-0.1, 0)
		UIGradient_2.Parent = Tab

		Title_3.Name = "Title"
		Title_3.Parent = Tab
		Title_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_3.BackgroundTransparency = 1.0
		Title_3.Size = UDim2.new(0, 132, 0, 33)
		Title_3.Font = Enum.Font.GothamSemibold
		Title_3.Text = tabName
		Title_3.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_3.TextSize = 16
		Title_3.Position = UDim2.new(0.0862068981, 0, 0, 0)
		Title_3.TextTransparency = 0.6
		Title_3.TextXAlignment = Enum.TextXAlignment.Left

		Items.Name = tabName
		Items.Parent = Content
		Items.Active = true
		Items.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Items.BackgroundTransparency = 1.0
		Items.Size = UDim2.new(0, 444, 0, 248)
		Items.ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0)
		Items.CanvasSize = UDim2.new(0, 0, 15, 0)
		Items.ScrollBarThickness = 0
		Items.Visible = false

		UIListLayout_2.Parent = Items
		UIListLayout_2.HorizontalAlignment = Enum.HorizontalAlignment.Center
		UIListLayout_2.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout_2.Padding = UDim.new(0, 8)

		UIPadding_2.Parent = Items
		UIPadding_2.PaddingTop = UDim.new(0, 8)

		Tab.MouseButton1Click:Connect(function()
			if activeTab then
				activeTab.BackgroundTransparency = 1
				activeTab.Title.TextTransparency = 0.6
			end

			Tab.BackgroundTransparency = 0
			Title_3.TextTransparency = 0
			activeTab = Tab
			selectedTab = tabName

			for _, sibling in ipairs(Content:GetChildren()) do
				sibling.Visible = (sibling == Items)
			end

			Subtitle.Text = "Projects / " .. title .. " / " .. tabName
			selectedTab = Tab
		end)

		return Items
	end


	
	function lib:CreateSection(title,TabParent)
		local Section = Instance.new("TextLabel")
		
		Section.Name = "Section"
		Section.Parent = TabParent
		Section.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Section.BackgroundTransparency = 1.000
		Section.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Section.BorderSizePixel = 0
		Section.Position = UDim2.new(0.0292792786, 0, 0, 0)
		Section.Size = UDim2.new(0, 422, 0, 19)
		Section.Font = Enum.Font.GothamSemibold
		Section.Text = title
		Section.TextColor3 = Color3.fromRGB(71, 71, 71)
		Section.TextSize = 16.000
		Section.TextXAlignment = Enum.TextXAlignment.Left
	end
	
	function lib:CreateButton(title, TabParent, callback)
		local Button = Instance.new("ImageButton")
		local UICorner_6 = Instance.new("UICorner")
		local Title_4 = Instance.new("TextLabel")
		local MouseIcon = Instance.new("ImageLabel")
		local UIAspectRatioConstraint_5 = Instance.new("UIAspectRatioConstraint")
		local UIStroke_2 = Instance.new("UIStroke")
		local UIGradient_3 = Instance.new("UIGradient")

		Button.Name = "Button"
		Button.Parent = TabParent
		Button.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
		Button.BackgroundTransparency = 0.200
		Button.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Button.BorderSizePixel = 0
		Button.Position = UDim2.new(0.0292792786, 0, 0.11304792, 0)
		Button.Size = UDim2.new(0, 418, 0, 39)
		Button.AutoButtonColor = false

		UICorner_6.CornerRadius = UDim.new(0, 6)
		UICorner_6.Parent = Button

		Title_4.Name = "Title"
		Title_4.Parent = Button
		Title_4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_4.BackgroundTransparency = 1.000
		Title_4.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Title_4.BorderSizePixel = 0
		Title_4.Position = UDim2.new(0.313479632, 0, -0.0195359457, 0)
		Title_4.Size = UDim2.new(0, 152, 0, 37)
		Title_4.Font = Enum.Font.GothamSemibold
		Title_4.Text = title
		Title_4.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_4.TextSize = 19.000

		MouseIcon.Name = "MouseIcon"
		MouseIcon.Parent = Button
		MouseIcon.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		MouseIcon.BackgroundTransparency = 1.000
		MouseIcon.BorderColor3 = Color3.fromRGB(0, 0, 0)
		MouseIcon.BorderSizePixel = 0
		MouseIcon.Position = UDim2.new(0.916267931, 0, 0.171571389, 0)
		MouseIcon.Size = UDim2.new(0, 26, 0, 30)
		MouseIcon.Image = "rbxassetid://10734898355"
		MouseIcon.ImageColor3 = CustomColor

		UIAspectRatioConstraint_5.Parent = MouseIcon

		UIStroke_2.Parent = Button
		UIStroke_2.Color = Color3.fromRGB(255, 255, 255)
		UIStroke_2.Transparency = 1.000

		UIGradient_3.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, CustomColor), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(0, 0, 0))}
		UIGradient_3.Parent = UIStroke_2

		local function onButtonPressed()
			local originalColor = Button.BackgroundColor3
			Button.BackgroundColor3 = CustomColor
			game:GetService("TweenService"):Create(Button, TweenInfo.new(0.5), {BackgroundColor3 = Color3.fromRGB(10, 10, 10)}):Play()

			if callback then
				callback()
			end
		end

		if game:GetService("UserInputService").TouchEnabled then
			Button.MouseButton1Click:Connect(onButtonPressed)
		else
			Button.MouseButton1Click:Connect(onButtonPressed)
		end
	end
	
	function lib:CreateToggle(title, TabParent, default, callback)
		local Toggle = Instance.new("ImageButton")
		local UICorner_9 = Instance.new("UICorner")
		local UIStroke_5 = Instance.new("UIStroke")
		local UIGradient_5 = Instance.new("UIGradient")
		local Title_6 = Instance.new("TextLabel")
		local Checkbox_2 = Instance.new("Frame")
		local UICorner_10 = Instance.new("UICorner")
		local UIStroke_6 = Instance.new("UIStroke")
		local Checkmark_2 = Instance.new("ImageLabel")
		local UIAspectRatioConstraint_7 = Instance.new("UIAspectRatioConstraint")
		local KeyBox_2 = Instance.new("TextBox")

		local TweenService = game:GetService("TweenService")
		local UserInputService = game:GetService("UserInputService")

		Toggle.Name = "Toggle"
		Toggle.Parent = TabParent
		Toggle.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
		Toggle.BackgroundTransparency = 0.200
		Toggle.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Toggle.BorderSizePixel = 0
		Toggle.Position = UDim2.new(0.0112612611, 0, 0.520833313, 0)
		Toggle.Size = UDim2.new(0, 418, 0, 42)
		Toggle.AutoButtonColor = false

		UICorner_9.CornerRadius = UDim.new(0, 6)
		UICorner_9.Parent = Toggle

		UIStroke_5.Parent = Toggle
		UIStroke_5.Color = Color3.fromRGB(255, 255, 255)
		UIStroke_5.Transparency = 1.000

		UIGradient_5.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, CustomColor), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(0, 0, 0))}
		UIGradient_5.Parent = UIStroke_5

		Title_6.Name = "Title"
		Title_6.Parent = Toggle
		Title_6.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_6.BackgroundTransparency = 1.000
		Title_6.Position = UDim2.new(0.11730738, 0, 0.095238097, 0)
		Title_6.Size = UDim2.new(0, 252, 0, 33)
		Title_6.Font = Enum.Font.GothamSemibold
		Title_6.Text = title
		Title_6.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_6.TextSize = 16.000
		Title_6.TextTransparency = 0.600
		Title_6.TextXAlignment = Enum.TextXAlignment.Left

		Checkbox_2.Name = "Checkbox"
		Checkbox_2.Parent = Toggle
		Checkbox_2.BackgroundColor3 = CustomColor
		Checkbox_2.BackgroundTransparency = 1.000
		Checkbox_2.Position = UDim2.new(0.0191387553, 0, 0.166666672, 0)
		Checkbox_2.Size = UDim2.new(0, 30, 0, 28)

		UICorner_10.CornerRadius = UDim.new(0, 4)
		UICorner_10.Parent = Checkbox_2
		UIStroke_6.Parent = Checkbox_2
		UIStroke_6.Color = Color3.fromRGB(35, 35, 35)

		Checkmark_2.Name = "Checkmark"
		Checkmark_2.Parent = Checkbox_2
		Checkmark_2.BackgroundTransparency = 1.000
		Checkmark_2.Position = UDim2.new(0.100000001, 0, 0.107142858, 0)
		Checkmark_2.Size = UDim2.new(0, 23, 0, 28)
		Checkmark_2.Image = "rbxassetid://10709790644"
		Checkmark_2.ImageTransparency = 1.000
		UIAspectRatioConstraint_7.Parent = Checkmark_2

		KeyBox_2.Name = "KeyBox"
		KeyBox_2.Parent = Toggle
		KeyBox_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		KeyBox_2.BackgroundTransparency = 1.000
		KeyBox_2.Position = UDim2.new(0.787081361, 0, 0.238095239, 0)
		KeyBox_2.Size = UDim2.new(0, 73, 0, 23)
		KeyBox_2.Font = Enum.Font.GothamSemibold
		KeyBox_2.PlaceholderText = "Click To Bind"
		KeyBox_2.Text = ""
		KeyBox_2.TextColor3 = Color3.fromRGB(255, 255, 255)
		KeyBox_2.TextSize = 16.000
		KeyBox_2.TextTransparency = 0.600

		local toggleState = default or false
		local boundKey

		local function onToggle()
			toggleState = not toggleState
			local checkboxTween = TweenService:Create(Checkbox_2, TweenInfo.new(0.7), {BackgroundTransparency = toggleState and 0 or 1})
			local checkmarkTween = TweenService:Create(Checkmark_2, TweenInfo.new(0.7), {ImageTransparency = toggleState and 0 or 1})
			local titleTween = TweenService:Create(Title_6, TweenInfo.new(0.7), {TextTransparency = toggleState and 0 or 0.6})
			local stroke5Tween = TweenService:Create(UIStroke_5, TweenInfo.new(0.7), {Transparency = toggleState and 0 or 1})
			local stroke6Tween = TweenService:Create(UIStroke_6, TweenInfo.new(0.7), {Transparency = toggleState and 1 or 0})

			checkboxTween:Play()
			checkmarkTween:Play()
			titleTween:Play()
			stroke5Tween:Play()
			stroke6Tween:Play()

			if callback then callback(toggleState) end
		end

		Toggle.MouseButton1Click:Connect(onToggle)

		KeyBox_2.FocusLost:Connect(function(enterPressed)
			if enterPressed then
				local inputText = KeyBox_2.Text:upper()
				if #inputText == 1 and inputText:match("%a") then
					boundKey = inputText
					KeyBox_2.Text = "Bind: " .. boundKey
				else
					KeyBox_2.Text = ""
				end
			end
		end)

		UserInputService.InputBegan:Connect(function(input, isProcessed)
			if not isProcessed and input.KeyCode.Name == boundKey then
				onToggle()
			end
		end)
	end
	
	function lib:CreateSlider(title, TabParent, min, max, default, callback)
		local Slider = Instance.new("ImageButton")
		local UICorner_11 = Instance.new("UICorner")
		local UIStroke_7 = Instance.new("UIStroke")
		local UIGradient_6 = Instance.new("UIGradient")
		local Title_7 = Instance.new("TextLabel")
		local Value = Instance.new("TextLabel")
		local SliderBack = Instance.new("Frame")
		local UICorner_12 = Instance.new("UICorner")
		local Draggable = Instance.new("Frame")
		local UICorner_13 = Instance.new("UICorner")
		local Handle = Instance.new("Frame")
		local UICorner_14 = Instance.new("UICorner")
		local UIAspectRatioConstraint_8 = Instance.new("UIAspectRatioConstraint")

		Slider.Name = "Slider"
		Slider.Parent = TabParent
		Slider.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
		Slider.BackgroundTransparency = 0.200
		Slider.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Slider.BorderSizePixel = 0
		Slider.Position = UDim2.new(0.0112612611, 0, 0.520833313, 0)
		Slider.Size = UDim2.new(0, 418, 0, 42)
		Slider.AutoButtonColor = false

		UICorner_11.CornerRadius = UDim.new(0, 6)
		UICorner_11.Parent = Slider

		UIStroke_7.Parent = Slider
		UIStroke_7.Color = Color3.fromRGB(255, 255, 255)
		UIStroke_7.Transparency = 1.000

		UIGradient_6.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, CustomColor), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(0, 0, 0))}
		UIGradient_6.Parent = UIStroke_7

		Title_7.Name = "Title"
		Title_7.Parent = Slider
		Title_7.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_7.BackgroundTransparency = 1.000
		Title_7.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Title_7.BorderSizePixel = 0
		Title_7.Position = UDim2.new(0.11722488, 0, 0.095238097, 0)
		Title_7.Size = UDim2.new(0, 255, 0, 33)
		Title_7.Font = Enum.Font.GothamSemibold
		Title_7.Text = title
		Title_7.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_7.TextSize = 16.000
		Title_7.TextTransparency = 0.600
		Title_7.TextXAlignment = Enum.TextXAlignment.Left

		Value.Name = "Value"
		Value.Parent = Slider
		Value.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Value.BackgroundTransparency = 1.000
		Value.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Value.BorderSizePixel = 0
		Value.Position = UDim2.new(0.0191387553, 0, 0.095238097, 0)
		Value.Size = UDim2.new(0, 41, 0, 33)
		Value.Font = Enum.Font.GothamSemibold
		Value.Text = tostring(default)
		Value.TextColor3 = Color3.fromRGB(255, 255, 255)
		Value.TextSize = 16.000
		Value.TextTransparency = 0.600
		Value.TextWrapped = true
		Value.TextXAlignment = Enum.TextXAlignment.Left

		SliderBack.Name = "SliderBack"
		SliderBack.Parent = Slider
		SliderBack.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
		SliderBack.BorderColor3 = Color3.fromRGB(0, 0, 0)
		SliderBack.BorderSizePixel = 0
		SliderBack.Position = UDim2.new(0.3708134, 0, 0.428571433, 0)
		SliderBack.Size = UDim2.new(0, 247, 0, 5)

		UICorner_12.CornerRadius = UDim.new(1, 0)
		UICorner_12.Parent = SliderBack

		Draggable.Name = "Draggable"
		Draggable.Parent = SliderBack
		Draggable.BackgroundColor3 = CustomColor
		Draggable.BackgroundTransparency = 0.600
		Draggable.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Draggable.BorderSizePixel = 0
		Draggable.Size = UDim2.new(0, 129, 0, 5)

		UICorner_13.CornerRadius = UDim.new(1, 0)
		UICorner_13.Parent = Draggable

		Handle.Name = "Handle"
		Handle.Parent = Draggable
		Handle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Handle.BackgroundTransparency = 0.600
		Handle.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Handle.BorderSizePixel = 0
		Handle.Position = UDim2.new(0.968, 0, -0.800000012, 0)
		Handle.Size = UDim2.new(0, 16, 0, 12)

		UICorner_14.CornerRadius = UDim.new(1, 0)
		UICorner_14.Parent = Handle

		UIAspectRatioConstraint_8.Parent = Handle

		local UIS = game:GetService("UserInputService")
		local TweenService = game:GetService("TweenService")

		local currentValue = default
		local isDragging = false
		local touchID = nil
		
		local function UpdateSliderPosition()
			local percentage = math.clamp((currentValue - min) / (max - min), 0, 1)
			Value.Text = string.format("%.1f", currentValue)

			local targetSize = UDim2.new(percentage, 0, 1, 0)
			local tween = TweenService:Create(Draggable, TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Size = targetSize})
			tween:Play()
			callback(currentValue)
		end

		local function StartDragging(input)
			isDragging = true

			local tweenText = TweenService:Create(Title_7, TweenInfo.new(0.1), {TextTransparency = 0})
			local tweenValue = TweenService:Create(Value, TweenInfo.new(0.1), {TextTransparency = 0})
			local tweenDraggable = TweenService:Create(Draggable, TweenInfo.new(0.1), {BackgroundTransparency = 0})
			local tweenHandle = TweenService:Create(Handle, TweenInfo.new(0.1), {BackgroundTransparency = 0})

			tweenText:Play()
			tweenValue:Play()
			tweenDraggable:Play()
			tweenHandle:Play()

			if input.UserInputType == Enum.UserInputType.Touch then
				touchID = input.UserInputIndex
			end
		end

		local function UpdateDragging(input)
			if not isDragging then return end

			local inputPosition
			if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
				inputPosition = input.Position.X
			end

			if inputPosition then
				local sliderX = SliderBack.AbsolutePosition.X
				local sliderWidth = SliderBack.AbsoluteSize.X
				local newPercentage = math.clamp((inputPosition - sliderX) / sliderWidth, 0, 1)
				currentValue = min + (newPercentage * (max - min))
				currentValue = math.round(currentValue * 10) / 10
				UpdateSliderPosition()
			end
		end

		local function StopDragging(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				isDragging = false
				touchID = nil

				local tweenText = TweenService:Create(Title_7, TweenInfo.new(0.1), {TextTransparency = 0.6})
				local tweenValue = TweenService:Create(Value, TweenInfo.new(0.1), {TextTransparency = 0.6})
				local tweenDraggable = TweenService:Create(Draggable, TweenInfo.new(0.1), {BackgroundTransparency = 0.6})
				local tweenHandle = TweenService:Create(Handle, TweenInfo.new(0.1), {BackgroundTransparency = 0.6})

				tweenText:Play()
				tweenValue:Play()
				tweenDraggable:Play()
				tweenHandle:Play()
			end
		end

		Slider.MouseButton1Down:Connect(StartDragging)
		UIS.InputChanged:Connect(UpdateDragging)
		UIS.InputEnded:Connect(StopDragging)

		currentValue = default
		UpdateSliderPosition()
	end

	function lib:CreateDropdown(title, TabParent, options, default, callback)
		local Dropdown = Instance.new("ImageButton")
		local UICorner_18 = Instance.new("UICorner")
		local UIStroke_10 = Instance.new("UIStroke")
		local UIGradient_9 = Instance.new("UIGradient")
		local DropTop_2 = Instance.new("Frame")
		local SelectedText_2 = Instance.new("TextLabel")
		local Title_10 = Instance.new("TextLabel")
		local DropButton_2 = Instance.new("ImageButton")
		local UIAspectRatioConstraint_10 = Instance.new("UIAspectRatioConstraint")
		local OptionContent_2 = Instance.new("Frame")
		local OptionsHolder_2 = Instance.new("ScrollingFrame")
		local UIListLayout_4 = Instance.new("UIListLayout")
		local UIPadding_4 = Instance.new("UIPadding")

		Dropdown.Name = "Dropdown"
		Dropdown.Parent = TabParent
		Dropdown.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
		Dropdown.BackgroundTransparency = 0.200
		Dropdown.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Dropdown.BorderSizePixel = 0
		Dropdown.Position = UDim2.new(0.0292792786, 0, -0.0958333313, 0)
		Dropdown.Size = UDim2.new(0, 418, 0, 42)
		Dropdown.AutoButtonColor = false

		UICorner_18.CornerRadius = UDim.new(0, 6)
		UICorner_18.Parent = Dropdown

		UIStroke_10.Parent = Dropdown
		UIStroke_10.Color = Color3.fromRGB(255, 255, 255)
		UIStroke_10.Transparency = 1.000

		UIGradient_9.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, CustomColor), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(0, 0, 0))}
		UIGradient_9.Parent = UIStroke_10

		DropTop_2.Name = "DropTop"
		DropTop_2.Parent = Dropdown
		DropTop_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		DropTop_2.BackgroundTransparency = 1.000
		DropTop_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
		DropTop_2.BorderSizePixel = 0
		DropTop_2.Size = UDim2.new(0, 417, 0, 42)

		SelectedText_2.Name = "SelectedText"
		SelectedText_2.Parent = DropTop_2
		SelectedText_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		SelectedText_2.BackgroundTransparency = 1.000
		SelectedText_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
		SelectedText_2.BorderSizePixel = 0
		SelectedText_2.Position = UDim2.new(0.480861247, 0, 0.105286375, 0)
		SelectedText_2.Size = UDim2.new(0, 182, 0, 33)
		SelectedText_2.Font = Enum.Font.GothamSemibold
		SelectedText_2.Text = default
		SelectedText_2.TextColor3 = CustomColor
		SelectedText_2.TextSize = 16.000
		SelectedText_2.TextXAlignment = Enum.TextXAlignment.Right

		Title_10.Name = "Title"
		Title_10.Parent = DropTop_2
		Title_10.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_10.BackgroundTransparency = 1.000
		Title_10.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Title_10.BorderSizePixel = 0
		Title_10.Position = UDim2.new(0.0263157897, 0, 0.105286375, 0)
		Title_10.Size = UDim2.new(0, 290, 0, 33)
		Title_10.Font = Enum.Font.GothamSemibold
		Title_10.Text = title
		Title_10.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_10.TextSize = 16.000
		Title_10.TextTransparency = 0.600
		Title_10.TextXAlignment = Enum.TextXAlignment.Left

		DropButton_2.Name = "DropButton"
		DropButton_2.Parent = DropTop_2
		DropButton_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		DropButton_2.BackgroundTransparency = 1.000
		DropButton_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
		DropButton_2.BorderSizePixel = 0
		DropButton_2.Position = UDim2.new(0.921052635, 0, 0.241184056, 0)
		DropButton_2.Size = UDim2.new(0, 27, 0, 33)
		DropButton_2.AutoButtonColor = false
		DropButton_2.Image = "http://www.roblox.com/asset/?id=11552476728"
		DropButton_2.ImageColor3 = CustomColor

		UIAspectRatioConstraint_10.Parent = DropButton_2

		OptionContent_2.Name = "OptionContent"
		OptionContent_2.Parent = Dropdown
		OptionContent_2.BackgroundColor3 = Color3.fromRGB(12, 14, 17)
		OptionContent_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
		OptionContent_2.BorderSizePixel = 0
		OptionContent_2.Position = UDim2.new(0.0263157897, 0, 0.196569324, 0)
		OptionContent_2.Size = UDim2.new(0, 399, 0, 0)

		OptionsHolder_2.Name = "OptionsHolder"
		OptionsHolder_2.Parent = OptionContent_2
		OptionsHolder_2.Active = true
		OptionsHolder_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		OptionsHolder_2.BackgroundTransparency = 1.000
		OptionsHolder_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
		OptionsHolder_2.BorderSizePixel = 0
		OptionsHolder_2.Position = UDim2.new(-0.00375939859, 0, -0.171536878, 35)
		OptionsHolder_2.Size = UDim2.new(0, 399, 0, 0)
		OptionsHolder_2.ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0)
		OptionsHolder_2.CanvasSize = UDim2.new(0, 0, 1.89999998, 0)
		OptionsHolder_2.ScrollBarThickness = 0

		UIListLayout_4.Parent = OptionsHolder_2
		UIListLayout_4.HorizontalAlignment = Enum.HorizontalAlignment.Center
		UIListLayout_4.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout_4.Padding = UDim.new(0, 6)

		UIPadding_4.Parent = OptionsHolder_2

		Dropdown.MouseButton1Click:Connect(function()
			game:GetService("TweenService"):Create(
				DropButton_2,
				TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
				{Rotation = 180}
			):Play()

			game:GetService("TweenService"):Create(
				Dropdown,
				TweenInfo.new(0.3),
				{Size = UDim2.new(0, 418, 0, 208)}
			):Play()
			game:GetService("TweenService"):Create(
				OptionContent_2,
				TweenInfo.new(0.3),
				{Size = UDim2.new(0, 399, 0, 157)}
			):Play()
			game:GetService("TweenService"):Create(
				OptionsHolder_2,
				TweenInfo.new(0.3),
				{Size = UDim2.new(0, 399, 0, 176)}
			):Play()
		end)

		for _, option in ipairs(options) do
			local OptionButton = Instance.new("ImageButton")
			OptionButton.Name = "OptionButton"
			OptionButton.Parent = OptionsHolder_2
			OptionButton.BackgroundColor3 = Color3.fromRGB(5, 6, 7)
			OptionButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
			OptionButton.BorderSizePixel = 0
			OptionButton.Size = UDim2.new(0, 384, 0, 35)
			OptionButton.AutoButtonColor = false

			local UICorner = Instance.new("UICorner")
			UICorner.CornerRadius = UDim.new(0, 6)
			UICorner.Parent = OptionButton

			local Title = Instance.new("TextLabel")
			Title.Name = "Title"
			Title.Parent = OptionButton
			Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title.BackgroundTransparency = 1.000
			Title.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Title.BorderSizePixel = 0
			Title.Size = UDim2.new(0, 151, 0, 27)
			Title.Font = Enum.Font.GothamSemibold
			Title.Text = option
			Title.Position = UDim2.new(0.314085633, 0, 0.0925928727, 0)
			Title.TextColor3 = CustomColor
			Title.TextSize = 16.000

			OptionButton.MouseButton1Click:Connect(function()
				game:GetService("TweenService"):Create(
					Dropdown,
					TweenInfo.new(0.3),
					{Size = UDim2.new(0, 418, 0, 42)}
				):Play()
				game:GetService("TweenService"):Create(
					OptionContent_2,
					TweenInfo.new(0.3),
					{Size = UDim2.new(0, 399, 0, 0)}
				):Play()
				game:GetService("TweenService"):Create(
					OptionsHolder_2,
					TweenInfo.new(0.3),
					{Size = UDim2.new(0, 399, 0, 0)}
				):Play()

				SelectedText_2.Text = option

				if callback then
					callback(option)
				end

				game:GetService("TweenService"):Create(
					DropButton_2,
					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
					{Rotation = 0}
				):Play()
			end)
		end
	end
	
	return lib
end
```
## Create Window
```lua
lib:CreateWindow("Wiihub")
```
## Create Tab
```lua
local tab1 = lib:CreateTab("Catching")
```
## Create Section
```lua
local sec1 = lib:CreateSection("test",tab1)
```
## Create Button
```lua
lib:CreateButton("Promote",tab1,function(callback)
	print("test")
end)
```
## Create Toggle
```lua
lib:CreateToggle("Magnets",tab1,false,function(state)
	print(state)
end)
```
## Create Slider
```lua
lib:CreateSlider("Magnet Range",tab1,0,25,0,function(value)
	print(value)
end)
```
## Create Dropdown
```lua
lib:CreateDropdown("Magnet Mode", tab1, {"Custom", "League", "Blatant", "Legit"}, "League", function(selectedOption)
	print("You selected: " .. selectedOption)
end)
```
