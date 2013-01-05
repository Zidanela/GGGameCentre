GGGameCentre
============

GGGameCentre makes working with Game Center nice and easy.
	
Basic Usage
-------------------------

##### Require The Code
```lua
local GGGameCentre = require( "GGGameCentre" )
```

##### Create your new game center manager
```lua
local gameCentre = GGGameCentre:new()
```

##### Show the achievements dialog
```lua
gameCentre:showAchievements()
```

##### Show the leaderboards dialog
```lua
gameCentre:showLeaderboards()
```

##### Show a specific leaderboard
```lua
gameCentre:showLeaderboards( "com.game.leaderboard" )
```

##### Show a specific leaderboard for today
```lua
gameCentre:showLeaderboards( "com.game.leaderboard", GGGameCentre.TimeScope.Today )
```

##### Show the friend request dialog
```lua
gameCentre:requestFriends()
```

##### Show the friend request dialog for a specific friend and include a message
```lua
gameCentre:requestFriends( "Will you be my friend?", 12345678 )
```

##### Show the friend request dialog for two friends and include a message
```lua
gameCentre:requestFriends( "Will you be my friend?", { "G:12345678", "G:64826483" } )
```

##### Show the friend request dialog for a specific friend via email addresses and include a message
```lua
gameCentre:requestFriends( "Will you be my friend?", nil, "me@me.com" )
```

##### Show the friend request dialog for two friends via email addresses and include a message
```lua
gameCentre:requestFriends( "Will you be my friend?", nil, { "me@me.com", "bob@me.com" } )
```

##### Check if the player is logged in
```lua
local loggedIn = gameCentre:isLoggedIn()
```

##### Set a new highscore.
```lua
gameCentre:setHighScore( "com.game.leaderboard", 25 )
```

##### Unlock an achievement.
```lua
gameCentre:unlockAchievement( "com.game.achievement1" )
```

##### Partly unlock an achievement.
```lua
gameCentre:unlockAchievement( "com.game.achievement2", 50 )
```

##### Reset all achievements.
```lua
gameCentre:resetAchievements()
```

##### Load the local player.
```lua
local listener = function( event )
	if event.phase == "loadLocalPlayer" then
		print( event.player.playerID )
	end
end

local gameCentre = GGGameCentre:new( listener )

gameCentre:loadLocalPlayer()
```

##### Get the local player after it has already been loaded.
local player = gameCentre:getLocalPlayer()
```

##### Load the friends of the local player.
```lua
local listener = function( event )
	if event.phase == "loadFriends" then
		print( event.freinds[ 1 ].playerID )
	end
end

local gameCentre = GGGameCentre:new( listener )

gameCentre:loadFriends()
```

##### Get the friends of the local player after it has already been loaded.
local friends = gameCentre:getFriends()
```

##### Destroy this GGGameCentre object
```lua
gameCentre:destroy()
```