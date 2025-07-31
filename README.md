# Discord RPC Lua

A Lua C module that implements the [Discord Rich Presence](https://github.com/discord/discord-rpc) library, inspired by [lua-discordRPC](https://github.com/pfirsich/lua-discordRPC).

---

## Usage

Start by requiring the module in Lua with:

```lua
local discordRPC = require("discord_rpc")
```

### Example code
```lua
print(discordRPC._VERSION)
```
Output:
```
DiscordRPC Lua v1.0
```

## Methods

## `discordRPC.initialize(applicationId, autoRegister, optionalSteamId)`

 - `applicationId` (string): Your Discord application ID
 - `autoRegister` (boolean): Whether to automatically register the app
 - `optionalSteamId` (string or nil): Steam ID, optional


## `discordRPC.updatePresence(presence)`

 - `presence` must be a table with the following keys (all optional):
    - `state` (string, max length: 127)
    - `details` (string, max length: 127)
    - `startTimestamp` (number)
    - `endTimestamp` (number)
    - `largeImageKey` (string, max length: 31)
    - `largeImageText` (string, max length: 127)
    - `smallImageKey` (string, max length: 31)
    - `smallImageText` (string, max length: 127)
    - `partyId` (string, max length: 127)
    - `partySize` (number)
    - `partyMax` (number)
    - `matchSecret` (string, max length: 127)
    - `joinSecret` (string, max length: 127)
    - `spectateSecret` (string, max length: 127)
    - `instance` (number)

## `discordRPC.shutdown()`

## `discordRPC.runCallbacks()`

## `discordRPC.clearPresence()`

## `discordRPC.respond(userId, reply)`
 - `userId` (string)
 - `reply` (string, must be either "no", "yes" or "ignore")

## Callbacks
## `discordRPC.onReady(callback)`
```lua
discordRPC.onReady(function(userId, username, discriminator, avatar)
    -- userId: string
    -- username: string
    -- discriminator: string
    -- avatar: string
end)
```

## `discordRPC.onDisconnected(callback)`
```lua
discordRPC.onDisconnected(function(errorCode, message)
    -- errorCode: number
    -- message: string
end)
```

## `discordRPC.onErrored(callback)`
```lua
discordRPC.onErrored(function(errorCode, message)
    -- errorCode: number
    -- message: string
end)
```

## `discordRPC.onJoinGame(callback)`
```lua
discordRPC.onJoinGame(function(joinSecret)
    -- joinSecret: string
end)
```

## `discordRPC.onSpectateGame(callback)`
```lua
discordRPC.onSpectateGame(function(spectateSecret)
    -- spectateSecret: string
end)
```

## `discordRPC.onJoinRequest(callback)`
```lua
discordRPC.onJoinRequest(function(userId, username, discriminator, avatar)
    -- userId: string
    -- username: string
    -- discriminator: string
    -- avatar: string
end)
```