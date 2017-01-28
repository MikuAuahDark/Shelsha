Shelsha Documentation
=====================
In this documentation, `Shelsha` is the namespace, while `ShelshaObject` is the texture bank object

#### `Shelsha.newTextureBank(string|file file_object)`

Creates new texture bank

> **Warning:** This function can be slow if it is called repeatedly, such as from `love.update` or `love.draw`.
If you need to use a specific resource often, create it once and store it somewhere it can be reused! 

Parameters:

* file_object - The file stream. It can be the filename, LOVE2D `File` object, or lua `file` object
previously opened with `io.open`

Returns: `ShelshaObject` object

#### `Mesh ShelshaObject:getImageMesh(number|string index)`

Gets LOVE2D `Mesh` object (which can be drawn) from specific image index

> **Warning:** This function can be slow if it is called repeatedly, such as from `love.update` or `love.draw`.
If you need to use a specific resource often, create it once and store it somewhere it can be reused! 

Parameters:

* index - Texture image index. If it's string, it must be the name of the texture image, without `I` and `.png.imag`

Returns: LOVE2D [`Mesh`](https://love2d.org/wiki/Mesh) object

#### `number,number ShelshaObject:getImageDimensions(number|string index)`

Gets texture image dimensions.

Parameters:

* index - Texture image index.

Returns: width and height of the texture image dimensions.

#### `number,number ShelshaObject:getImageCenter(number|string index)`

Gets texture image center position.

Parameters:

* index - Texture image index.

Returns: center position of the texture image dimensions (x and y, 2 values).

#### `number,number ShelshaObject:getBankDimensions()`

Gets texture bank dimensions.

Returns: width and height of the texture bank dimensions.

#### `Image ShelshaObject:getBankImage()`

Gets texture bank image.

Returns: LOVE2D [`Image`](https://love2d.org/wiki/Image)

#### `table ShelshaObject:getBankImageList()`

Gets list of texture images data (name, x, y, u, v) from current texture bank

Returns: table which contains all texture image information (0-based index)
