+++
date = '2025-08-24T00:00:00+02:00'
draft = false
title = 'Allowing users to report bugs directly into GitLab or GitHub issues'
+++

> The code in this post (and more) is available on [github](https://github.com/050soft/RobloxBugReport)

Making Roblox games is fun, until you have thousands of players running into bugs - Roblox does not have a built in way for players to give feedback or report bugs.  
A good way to solve this is by allowing players to report bugs and give feedback through a Discord server. Using a Discord server has a small flaw however, it's another platform between developers and fixing the actual bugs.  

## GitHub/GitLab
Of course, not every Roblox developer uses GitHub or GitLab for their games, and that's fine. You don't have to use it.  
The reality is, tracking all of the reported bugs in Discord can become messy... The solution? A GitHub/GitLab repository (it doesn't even have to host the code for the game)  

What if you could automatically make GitHub/GitLab issues directly from feedback in your Roblox game? You could use GitHub projects to track the feedback and also plan who works on it, and when.  

That's where my project comes in - Easily receive bug reports and other feedback from your community! All you need is your own user interface, the rest is handled by the project.

### How it works
Using the client module and 2 text inputs from the user, you can already send your first report!
```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local RobloxBugReport = ReplicatedStorage:WaitForChild("RobloxBugReport")
assert(RobloxBugReport, "RobloxBugReport folder not found under ReplicatedStorage")
local ClientModule = require(RobloxBugReport.Client)
assert(ClientModule, "Client Module not found under RobloxBugReport")

local UI = PathToPlayerGui
local TitleLabel = UI.PathToTitleLabel
local DescriptionLabel = UI.PathToDescriptionLabel
local SendButton = UI.PathToSendButton
SendButton.Activated:Connect(function()
    local title = TitleLabel.Text
    local description = DescriptionLabel.Text
    return ClientModule(title, description)
end)
```
This is a very basic example on how to use the module. 

(wip)