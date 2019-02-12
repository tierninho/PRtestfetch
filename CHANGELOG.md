
## Version 3.15.0 - Batou - in development

### New Features

* You can now set the `maxLights` value in the Game Config, which controls the total number of lights the Light2D shader can render in a single pass. The default is 10. Be careful about pushing this too far. More lights = less performance. Close #4081 (thanks @FrancescoNegri)
* `Rectangle.SameDimensions` determines if the two objects (either Rectangles or Rectangle-like) have the same width and height values under strict equality.
* An ArcadePhysics Group can now pass `{ enable: false }`` in its config to disable all the member bodies (thanks @samme)
* `Body.setEnable` is a new chainable method that allows you to toggle the enable state of an Arcade Physics Body (thanks @samme)
* `KeyboardPlugin.resetKeys` is a new method that will reset the state of any Key object created by a Scene's Keyboard Plugin.
* `Pointer.wasCancelled` is a new boolean property that allows you to tell if a Pointer was cleared due to a `touchcancel` event. This flag is reset during the next `touchstart` event for the Pointer.
* `Pointer.touchcancel` is a new internal method specifically for handling touch cancel events. It has the same result as `touchend` without setting any of the up properties, to avoid triggering up event handlers. It will also set the `wasCancelled` property to `true`.

* `WebGLRenderer.deleteTexture` will check to see if the texture it is being asked to delete is the currently bound texture or not. If it is, it'll set the blank texture to be bound after deletion. This should stop `RENDER WARNING: there is no texture bound to the unit 0` errors if you destroy a Game Object, such as Text or TileSprite, from an async or timed process (thanks jamespierce)
* The `RequestAnimationFrame.step` and `stepTimeout` functions have been updated so that the new Frame is requested from raf before the main game step is called. This allows you to now stop the raf callback from within the game update or render loop. Fix #3952 (thanks @tolimeh)
* If you pass zero as the width or height when creating a TileSprite it will now use the dimensions of the texture frame as the size of the TileSprite. Fix #4073 (thanks @jcyuan)
* `TileSprite.setFrame` has had both the `updateSize` and `updateOrigin` arguments removed as they didn't do anything for TileSprites and were misleading.
* `CameraManager.remove` has a new argument `runDestroy` which, if set, will automatically call `Camera.destroy` on the Cameras removed from the Camera Manager. You should nearly always allow this to happen (thanks jamespierce)
