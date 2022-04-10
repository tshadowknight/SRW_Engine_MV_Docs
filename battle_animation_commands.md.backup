## Notes

The Target input provides a drop down menu with system defined Target ids for ease of use:

* active\_main: The Sprite of the unit performing the current attack.
* active\_target: The Sprite of the target of the current attack. This reference will refer to the support defender when the support defender is active.
* Camera: The Camera of the Battle Scene.

Some commands have a drop down menu that provides default values for ease of use:

* position, startPosition: Have a drop down list with the default positions for the main sprites and the camera.
* rotation, startRotation: Have a drop down list with the default rotations for the main sprites and the camera.

### clear\_attack\_text
Clear the text box.


### create\_bg
Create a new background.

Target: The id of the created background.

Parameters:

* path: The file path of the asset.
* parent: The id of the object that will be the parent of this object.
* position: A position defined by an x, y and z coordinate.
* size: The size of the asset.
* alpha: The alpha of the object.
* billboardMode: Set the billboarding mode for the object: 'none' or 'full'
* rotation: A rotation defined by an x, y and z component. The rotations are described with radian values.
* animationFrames: The number of animation frames in the spritesheet.
* frameSize: The size of the frames in the spritesheet.
* lineCount: The number of lines in the spritesheet.
* columnCount: The number of columns in the spritesheet.
* animationLoop: If 1 the animation will loop.
* animationDelay: The time between animation frames in milliseconds.

### create\_layer
Create a new layer.

Target: The id of the created layer.

Parameters:

* path: The file path of the asset.
* isBackground: If 1 the layer will be a background layer.
* frameSize: The size of the frames in the spritesheet.
* lineCount: The number of lines in the spritesheet.
* columnCount: The number of columns in the spritesheet.
* animationFrames: The number of animation frames in the spritesheet.
* animationLoop: If 1 the animation will loop.
* animationDelay: The time between animation frames in milliseconds.

### create\_sky\_box
Create a new sky box.

Target: The id of the created skybox.

Parameters:

* path: The file path of the asset.
* color: The blend color for the skybox.

### destroy
Play the destruction animation of the target.



### disable\_support\_defender
Switch out the support defender for the defender. This command is automatically called after an attack if applicable.


### dodge\_pattern
Show the target's dodging action. The commands provided as parameters define the evade movement of the target. If the target has a special dodge action, like Double Image, the matching animation will be played instead.

Parameters:

* commands: A list of commands that moves the target during the dodge.

### drain\_en\_bar
Show EN spent.

Parameters:

* percent: How much of the change to the value that should be shown. If the total change is 5000, specifying 50 will show 2500.
* duration: The duration of the command in animation ticks.

### drain\_hp\_bar
Show damage on the HP bar.

Parameters:

* percent: How much of the change to the value that should be shown. If the total change is 5000, specifying 50 will show 2500.
* duration: The duration of the command in animation ticks.

### enable\_support\_defender
Switch out the defender for the support defender. This command is automatically called during the next\_phase command if applicable.


### fade\_in\_bg
Fade in the target background.

Target: The id of the background to fade in.

Parameters:

* startFade: The initial opacity of the object, between 0-1.
* endFade: The final opacity of the object, between 0-1.
* duration: The duration of the command in animation ticks.
* easingFunction: Describes how an object moves from point a to point b. If not specified the object will move linearly.
* easingMode: In, out or inout. Parameterizes the easingFunction.

### fade\_swipe
Swipe the screen to black. This command is automatically called during the next\_phase command.

Parameters:

* time: The duration of the command in milliseconds.

### fade\_white
Fade the screen to white and from white.

Parameters:

* time: The duration of the command in milliseconds.
* speed: The speed of the effect.
* speedOut: The speed of the fadeout: 'fast' or 'slow'.

### flip
Flip the texture of an object.

Target: The id of the object that should be flipped.

Parameters:

* x: If 1 the object will be flipped along its x-axis.
* y: If 1 the object will be flipped along its y-axis.

### hide\_bgs
Hide the default background elements.


### hide\_effekseer
Hide a running effekseer effect.

Target: The id of the effekseer instance that should be hidden.


### hide\_portrait\_noise
Remove static on character portrait.


### hide\_sprite
Hide a sprite.

Target: The id of the sprite that should be hidden.


### kill\_active\_animations
Immediately stop all running animations.


### kill\_se
Mute all playing sound effects.


### next\_phase
Fade the screen to black and set the scene up for the second phase of the attack. This command automatically brings the support defender if available and sets up the default background to match the target.

Parameters:

* cleanUpCommands: A list of commands to be run to clean up objects before the next phase.
* commands: A list of commands to be run to during the phase transition to set up the next phase.

### play\_effekseer
Play a predefined effekseer effect.

Target: The id for the effekseer instance that will be created.

Parameters:

* path: The file path of the asset.
* position: A position defined by an x, y and z coordinate.
* scale: A scaling factor for the effect.
* speed: The speed of the effect.
* rotation: A rotation defined by an x, y and z component. The rotations are described with radian values.

### play\_se
Play a sound effect.

Parameters:

* seId: The name of the sound effect to play.
* pitch: The pitch to play the sound effect at.
* volume: The volume to play the sound effect at.

### remove\_bg
Remove a background.

Target: The id of the object to remove.


### remove\_layer
Remove a layer.

Target: The id of the object to remove.


### remove\_sky\_box
Remove a sky box.

Target: The id of the object to remove.


### remove\_sprite
Remove a sprite.

Target: The id of the object to remove.


### reset\_position
Reset the position of the target to the default position.

Parameters:

* duration: The duration of the command in animation ticks.

### resize
Change the size of an object between the start size and end size.

Target: The id of the object to resize.

Parameters:

* startSize: The initial size of the target object.
* endSize: The final size of the target object.
* duration: The duration of the command in animation ticks.
* easingFunction
* easingMode: In, out or inout. Parameterizes the easingFunction.

### rotate
Rotate an object from the start rotation to the end rotation.

Target: The id of the object to rotate.

Parameters:

* startRotation: A rotation defined by an x, y and z component. The rotations are described with radian values.
* rotation: A rotation defined by an x, y and z component. The rotations are described with radian values.
* duration: The duration of the command in animation ticks.
* easingFunction: Describes how an object moves from point a to point b. If not specified the object will move linearly.
* easingMode: In, out or inout. Parameterizes the easingFunction.

### rotate\_to
Immediately set to rotation of an object.

Target: The id of the object to rotate.

Parameters:

* rotation: A rotation defined by an x, y and z component. The rotations are described with radian values.

### set\_attack\_text
Show attack text for the current target.

Parameters:

* id: The id of the Quote to show. To assign text for an attack the text should be defined in the Battle Text editor for the Pilot and matching Attack. The id used in the Attack Animation should be the Quote ID defined in the Battle Text editor.

### set\_bg\_scroll\_ratio
Set the speed at which the backgrounds scroll.

Parameters:

* ratio: The factor by which the scroll speed is multiplied.

### set\_damage\_text
Show damage text for the current target. This command is automatically called during the reset\_position command.


### set\_destroyed\_text
Show destroyed text for the current target. This command is automatically called during the destroy command.


### set\_evade\_text
Show evade text for the current target. This command is automatically called during the reset\_position command if applicable.

### set\_sprite\_frame
Set the source frame of a sprite(in, out, dodge, hurt, main).

Target: The id of the sprite.

Parameters:

* name

### set\_sprite\_index
Set the frame of a sprite.

Target: The id of the sprite.

Parameters:

* index: The new sprite index

### shake
Shake an object on the x and y axis with the specified magnitude. This command can also be used to shake the camera.

Target: The id of the object to shake.

Parameters:

* magnitude\_x: The severity of the shaking effect along the x-axis.
* magnitude\_y: The severity of the shaking effect along the y-axis.
* duration: The duration of the command in animation ticks.
* easingFunction: Describes how an object moves from point a to point b. If not specified the object will move linearly.
* easingMode: In, out or inout. Parameterizes the easingFunction.

### show\_bgs
Show the default background elements.


### show\_damage
Show the damage the target has taken for the current attack.


### show\_portrait\_noise
Fade in static on character portrait.


### show\_sprite
Show a sprite.

Target: The id of the sprite.


### show\_support\_defender\_text
Show text for the incoming support defender. This command is automatically called during the next\_phase command if applicable.


### spawn\_sprite
Create a new sprite.

Target: The id of the sprite that will be created.

Parameters:

* path: The file path of the asset.
* position: A position defined by an x, y and z coordinate.
* size: The size of the asset.
* frameSize: The size of the frames in the spritesheet.
* animationFrames: The number of animation frames in the spritesheet.
* animationLoop: If 1 the animation will loop.
* animationDelay: The time between animation frames in milliseconds.

### teleport
Immediately move an object.

Target: The id of the object to move.

Parameters:

* position: A position defined by an x, y and z coordinate.

### toggle\_bg\_scroll
Invert the current background scroll direction.


### translate
Move an object from the start position to the end position.

Target: The id of the object to move.

Parameters:

* startPosition: A position defined by an x, y and z coordinate.
* position: A position defined by an x, y and z coordinate.
* duration: The duration of the command in animation ticks.
* easingFunction: Describes how an object moves from point a to point b. If not specified the object will move linearly.
* easingMode: In, out or inout. Parameterizes the easingFunction.
* hide: Hide the target object after the command has finished.
* catmullRom: Describes two addtional points for a Catmull-Rom spline. To get an idea on how to position the points you can try this visualization www.desmos.com/calculator/552cpvzfxw. The two points provided for this parameter are the points that are not on the curve(red and orange).

### updateBgMode
Update the current default backgrounds to match the target. This command is automatically called during the next\_phase command.

Target: The id of the main sprite to which the backgrounds are matched.

### play\_rmmv\_anim
Play a vanilla RMMV animation in the Battle Scene rendered onto an object in the scene.
The animation can be positioned in the 3d space of the scene.

Target: The id of the animation that will be created.

Parameters:

* animId: The id of the RMMV animation.
* position: A position defined by an x, y and z coordinate.
* scaleX: A scaling factor for the width of the effect.
* scaleY: A scaling factor for the height of the effect.
* loop: If set to 1 the animation will continue looping.
* noFlash: If set to 1 the flashing effects of the animation are not shown.
* noSfx: If set to 1 the built in sound effects of the animation will not play.

### remove\_rmmv\_anim	
Remove a running RMMV animation immediately.

Target: The id of the animation that will be removed.			

### stop\_rmmv\_anim	
Stop a running RMMV animation after the next loop.

Target: The id of the animation that will be stopped.	
	
### play\_rmmv\_screen\_anim
Play a vanilla RMMV animation in the Battle Scene on an overlay over the screen.
The position of the animations will always be the same on the screen, even if the camera is moved.

Target: The id of the animation that will be created.

Parameters:

* animId: The id of the RMMV animation.
* position: A position defined by an **x, y offset to the center of the screen**
* scaleX: A scaling factor for the width of the effect.
* scaleY: A scaling factor for the height of the effect.
* loop: If set to 1 the animation will continue looping.
* noFlash: If set to 1 the flashing effects of the animation are not shown.
* noSfx: If set to 1 the built in sound effects of the animation will not play.

### remove\_rmmv\_screen\_anim	
Remove a running RMMV screen animation immediately.

Target: The id of the animation that will be removed.			

### stop\_rmmv\_screen\_anim	
Stop a running RMMV screen animation after the next loop.

Target: The id of the animation that will be stopped.