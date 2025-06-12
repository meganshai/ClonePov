local player = game.Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()

-- Create the clone
local clone = char:Clone()
clone.Name = "MaeganClone"
clone.Parent = workspace
clone:SetPrimaryPartCFrame(char.PrimaryPart.CFrame * CFrame.new(0, 0, -5))

-- Freeze clone
if clone:FindFirstChild("Humanoid") then
    clone.Humanoid:ChangeState(Enum.HumanoidStateType.Physics)
end

-- Switch camera to clone
workspace.CurrentCamera.CameraSubject = clone:FindFirstChild("Humanoid") or clone

-- Button to return POV
local gui = Instance.new("ScreenGui", game.CoreGui)
local btn = Instance.new("TextButton", gui)

btn.Size = UDim2.new(0, 120, 0, 40)
btn.Position = UDim2.new(0, 20, 0, 100)
btn.Text = "Back to Me"
btn.BackgroundColor3 = Color3.fromRGB(200, 100, 100)

btn.MouseButton1Click:Connect(function()
    workspace.CurrentCamera.CameraSubject = player.Character:FindFirstChild("Humanoid")
    btn.Text = "Switched ✅"
end)
