Shelsha
=======
Shelsha is a [L�VE](https://love2d.org/) library which allows of loading Playground texture bank images (TEXB).

Dependencies
============

* L�VE 0.9.1. L�VE 0.10.0 or later version is recommended (and faster)

* [compress.deflatelua](https://github.com/davidm/lua-compress-deflatelua) (and it's crc32 library)
if using L�VE 0.9.1. It's already bundled in this repo. Safe to delete if using L�VE 0.10.0 (or later version)

Performance
===========

* In L�VE 0.9.1, it takes about ~4 seconds to load 1024x1024 TEXB image. This is
because it uses pure Lua deflate library (and it's slow) and it has to set every pixel on loop,
since L�VE 0.9.1 does lack of `love.image.newImageData(width, height, rgba_image_data)` function.

* In L�VE 0.10.0, it takes about ~80ms to load 1024x1024 TEXB image. This is because
in L�VE 0.10.0, there's [`love.math.decompress`](https://love2d.org/wiki/love.math.decompress)
and that's of course faster than pure Lua deflate implementation.
