Shelsha
=======
Shelsha is a [LÖVE](https://love2d.org/) library which allows of loading Playground texture bank images (TEXB).

The name itself comes from one of my friend. I already have [permission](https://twitter.com/MikuAuahDark/status/825181343000645632) to use her name of course.

Dependencies
============

* LÖVE 0.9.1. LÖVE 0.10.0 or later version is recommended (and faster)

* [compress.deflatelua](https://github.com/davidm/lua-compress-deflatelua) (and it's crc32 library)
if using LÖVE 0.9.1. Not needed (and safe to delete) when using LÖVE 0.10.0 (or later version)

* [LuaBit](http://luaforge.net/projects/bit/), when pure Lua 5.1 is used (not LuaJIT).

Performance
===========

* In LÖVE 0.9.1, it takes about ~3.1 seconds to load 1024x1024 TEXB image (**with FFI**). This is
because it uses pure Lua deflate library (and it's slow), since LÖVE 0.9.1 does lack of
`love.image.newImageData(width, height, rgba_image_data)` function.

* In LÖVE 0.10.0, it takes about ~80ms to load 1024x1024 TEXB image (**with FFI**). This is because
in LÖVE 0.10.0, there's [`love.math.decompress`](https://love2d.org/wiki/love.math.decompress)
and that's of course faster than pure Lua deflate implementation. It also uses
`love.image.newImageData(width, height, rgba_image_data)` function to create image which is faster.

* __Without FFI__, it's way more slower. Using LÖVE 0.9.1 takes ~26.7 seconds, and using LÖVE 0.10.0 takes ~7.6 seconds.

Example
=======
Below is the example code of using Shelsha

```lua
local Shelsha = require("Shelsha")
local tx_startup_w1136
local bank
local imagetgt

function love.load()
	local b
	local file = love.filesystem.newFile("tx_startup_w1136.texb", "r")
	local tx_startup_w1136 = Shelsha.newTextureBank(file)
	
	imagetgt = tx_startup_w1136:getImageMesh("assets/image/ui/login/log_etc_02_iphne5_01")
	bank = tx_startup_w1136:getBankImage()
end

function love.draw()
	love.graphics.draw(imagetgt)
end
```
