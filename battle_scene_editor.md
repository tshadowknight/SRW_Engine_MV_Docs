# Attack Editor
To access the Battle Environment Editor hit F11 on the main title screen and select "Attack Editor" from the top right drop down menu.

## Attack Animations

An Attack Animation defines the graphical effects that will be shown in the Main Battle Scene when an attack is used. The main tasks of an Attack Animation are to spawn in assets and to manipulate them(move them around, rotate them, scale them, etc.) to create the desired graphical representation of an attack. 

Attack Animations are defined as a list of Animation Commands that manipulate elements of the Battle Scene.

Attack animations are assigned to weapons using the weaponAnimId tag. If no animation is assigned to an attack the animation with id 0 will play be default.

### Timing

To time the Animation Commands in an Attack Animation each command is assigned to a certain animation Tick. Each animation Tick is 1/60th of a second.

### Basic scene layout

It is important to keep in mind the default positions of key objects in the scene when making an Attack Animation.
Position are shown as (x, y, z).

Main Sprites(Actor, Enemy) are at height 0 and depth 0 with an x offset of 2 from the center.
* actor: (2,0,0)
* enemy: (-2,0,0)

The default position of the Camera is pulled back to -6.5 on the z axis and is elevated by 1.15 on the y axis (0,1.15,-6.5).

These default positions are available from a drop down list when working with position parameters.

### Assets

Assets for Attack Animations live in the following places depending on their type.

Graphics

* img/SRWBattleBacks: Contains image files for Battle Environment layers
* img/SRWBattleScene: Contains sub-folders containing assets for specific units. The folder for a unit should contain the default sprite information for that unit(more details in the section on unit sprites). An attack can use assets from any of the folders, but keeping assets specific to a unit in the matching folder is recommended for keeping things organized.
* img/skyboxes: Contains image files for skyboxes. For more information on how the skyboxes work check this link: doc.babylonjs.com/divingDeeper/environment/skybox
* effekseer: Effekseer export files should be put in this folder and any needed textures should be in the Texture sub-folder. Alternatively you can create a sub-folder and put the Effekseer definition in there, but the sub-folder will need its own Texture folder.

Sound

Sound effect files live in the default RPG Maker folders: audio/se.

### Unit Sprites

There are 6 special sprites that are always available for use in the Battle Scene:

* actor
* actor twin
* actor supporter
* enemy
* enemy twin
* enemy supporter

These sprites are linked to the real mech/class taking part in the Battle Scene and use the mechBattleSceneSprite metadata tag to determine which folder in img/SRWBattleScene belongs to the sprite. The Battle Scene will automatically pull default sprites poses from the matching folder for certain actions. The required default poses are:

* main: Idle pose
* in: Leaning in while moving
* out: Leaning back while moving
* hurt
* dodge
* block

For units that use regular sprites each of these default poses should have a matching .png file in the correct character folder(main.png, hurt.png, etc.)


### Spine Sprites

The battle scene supports the use of animated characters created using Spine(http://esotericsoftware.com/). The mech needs to be configured as follows in the editor:

![](img/spine_setup.png)

* Internal Canvas Width: The width in pixels of the canvas onto which the Spine animation will be rendered
* Internal Canvas Height: The height in pixels of the canvas onto which the Spine animation will be rendered

Note that the engine will not scale the animation to fit the canvas, if an animation is cut off, increase the canvas size.

The assets for the Spine character should be stored in a folder called "spine" in the SRWBattleScene folder for the class(Ex.: img/SRWBattleScene/harold/spine). The assets are the files obtained from exporting the spine project and should have the following names:

* skeleton.atlas
* skeleton.json
* skeleton.png

The Spine project file should contain one skeleton named skeleton and have the following animations defined:

* main: The idle pose for the mech
* in: The moving forward pose for the mech
* out: The moving backwards pose for the mech
* hurt: The taking damage pose for the mech
* block: The animation shown when the mech blocks
* dodge: The animation shown when the mech dodges

It can have any number of additional animations that can be called with the set\_sprite\_frame animation command by name.

#### Looping animations

Whether any of the animations of a mech loop is set in the Spine project file as follows:

* Be in Setup mode
* Create an event called loop
* In the String field of the loop event, list all animations by name that should loop separated by a comma. (Ex.: main,dodge)

### 3D Models

The battle scene supports using 3D Models as unit "sprites".   
To use a 3d model set the Sprite Type to 3D.

The following config setting are available:  

* Scale: A uniform scaling factor applied to model. Tweak this setting until the model fits the default scene layout.
* Rotation(deg): A default rotation applied to the model.

The model for the unit must be stored in a folder called "3d" in the SRWBattleScene folder for the class (Ex.: img/SRWBattleScene/harold/3d).

The model file must be .glb file and be named "model.glb" (Ex.: img/SRWBattleScene/harold/3d/model.glb").

The model should have a default animation for each default pose. When using blender animations correspond to actions in the action editor, the name of the action should match the pose name.

* main: The idle pose for the mech
* in: The moving forward pose for the mech
* out: The moving backwards pose for the mech
* hurt: The taking damage pose for the mech
* block: The animation shown when the mech blocks
* dodge: The animation shown when the mech dodges  

Additional animations may be present in the model file and can be played using the "set\_sprite\_frame" animation command.
If the snap parameter on the command is not set the engine will blend the end state of the current animation into the next animation, if set no blending is done.

#### Attachments

Models may have any number of attachments. These attachments can be used as a reference point to attach other objects to in the battle scene or can be used as part of specific model animations. An attachment must be a top level mesh and have a name starting with "att_".
When loading a model the attachments will be set to invisible by default.

An object can be attached to a model's attachment by setting a parent for the object like "parent\_object\_name:attachment\_name"(Ex.: active\_main:att\_hand) in the parent field for the creation command of the object.

An attachment can be revealed or hidden using the ""show\_attachment" and ""hide\_attachment" animation commands.

#### Animated textures

A model can have a part of its mesh animated using the flipbook mechanism in Blockbench. To enable this animation in engine additional info must be provided and the model must be set up correctly:

* The animated part must have its own texture, which will act as an animation sheet
* The animated part must have parent group with a name that encodes information about the animation: anim\_\<frame size\>\_\<rows\>\_\<columns\>\_delay(milliseconds) Ex.: anim\_64\_5\_1\_400
	- anim_: A prefix indicating this node name has animation information
	- frame size: the size of an individual frame of animation, must be a power of 2. Only square frames are supported.
	- rows: The number of rows in the animation sheet
	- columns: The number of columns in the animation sheet
	- delay: How long each frame of the animation is displayed(in milliseconds)
	


### Effekseer Support

The Battle Scene supports displaying particle systems created using the freely available Effekseer(effekseer.github.io/en/) program.

#### Files
To use an Effekseer particle system export the particle system to the .efk format and put it in the effekseer folder of the project and put the required textures in the effekseer/Texture folder. Note that you will need to ensure that the Effekseer project refers to the texture with the correct path, so while making the particle system keep the textures you use in a Texture folder in the same folder as the project file. Your project folder should look like this:

* effekseer project:
	* effect sub folder
 		* project file.efkc
 	* Texture
  		* texture.png 	

You can copy the content of this folder into the effekseer folder of your RPG Maker project to use the effects.
**Note**: When making a new effect make sure to save it before editing so that it correctly uses relative paths for its textures!

#### Commands
Once the files are in the right place the particle system can be displayed in the Battle Scene with the play_effekseer Animation Command.
It has the following settings:
* path: The location of the .efk file in the effekseer folder
* position:
* scale: 
* speed: 1 is regular playback, supports decimal values
* rotation:
* parent: a target name that can be used to attach the effect to. Use something like active\_main:point\_eye to attach an effect to a part of a model
* isForeground: if true the effect will render as render group 3, so on top of everything in the default scene.
* autoRotate: if true the effect will be flipped on the x-axis when played for the enemy side
* flipZ: if true the z direction will be flipped, may be required to line up the rotation with what is seen in the effekseer editor
* ignoreParentRotation: if true the rotation of the parent(if set) is not applied

Additional effekseer commands are:

* hide_effekseer: hides the target effect(this is permanent)
* remove_effekseer_parent: removes the parent from the target effect
* set_effekseer_color: set the global color/tint for the effect
* stop_effekseer_root: stops the root of the effekseer effect, this will stop child nodes from spawning and let the effect fade out
* send_effekseer_trigger: send a trigger (0-3) to the target effect. This will trigger spawn/stop/destroy triggers set in the efffect.
* set_effekseer_frame: update the target effect to the specified frame.
* set_effekseer_attract_point: set the global attraction point for the effekseer context of the target effect.

#### Tips and tricks

* Fixing the seed: Set the seed to a value other than -1 in the global settings to make the effect consistent every time it is played
* Making a particle that goes on top: In the render settings of a particle uncheck Depth Test to create a particle that will render above everything in the scene
* Rendering order: The order of effects is determined by the order in which they are loaded in the animation. If you want an effect that goes behind another effect but that starts later you can use a trigger: give the root of the effect a spawn trigger. In the animation create the effect that goes behind first and then start it by trigger using the send_effekseer_trigger command. You can have further control over rendering order by using the isForeground setting and using rendering_group settings for scene elements. Elements in higher rendering groups get rendered on top. Standard elements like unit sprites are in group 2 by default, setting isForeground places the effect in group 3. Using the set_rendering_group command you can put default elements in group 4, etc.

### Sequences

An Attack Animation can be different depending on the game state. Whether an attack hits, misses or destroys its target will affect how the attack animation plays out. To account for this an attack animation is split into different sequences:

* Main: This sequence will always play and should have the animation commands for the start of the animation.
* Hit: This sequence only plays when the attack hits.
* Hit Twin: This sequence only plays when the attack hits the sub twin.
* Hit Overwrite: This sequence only plays when the attack hits. If any of the animation Ticks of this sequence match a Tick from the Main sequence the Animation Commands from the Main Sequence for that Tick will not be executed.
* Miss: This sequence only plays when the attack misses.
* Miss Twin: This sequence only plays when the attack misses the sub twin.
* Miss Overwrite: This sequence only plays when the attack misses. If any of the animation Ticks of this sequence match a Tick from the Main sequence the Animation Commands from the Main Sequence for that Tick will not be executed.
* Destroy: This sequence only plays when the attack destroys its target.
* Destroy Twin: This sequence only plays when the attack destroys the sub twin.
* Destroy Overwrite: This sequence only plays when the attack destroys its target. If any of the animation Ticks of this sequence match a Tick from the Main/Hit sequence the Animation Commands from the Main/Hit Sequence for that Tick will not be executed.

Ticks for each Sequence start from 0, so if you define a command for the same Tick in the Main and Hit Sequence for example, those commands will be executed at the same time for normal Sequences. For Overwrite sequences the commands of the Overwrite sequence will be the only ones that are executed for the matching Ticks.

Depending on the game state the Battle Scene will combine the necessary sequences to create the final animation:

* The attack misses: Main + Miss + Miss Overwrite
* The attack hits: Main + Hit + Hit Overwrite
* The attack destroys: Main + Hit + Hit Overwrite + Destroy + Destroy Overwrite

The Twin sequences will only be executed when an ALL attack is used an a sub twin target is available.

#### ALL Attacks

ALL attacks are attacks that hit both units in a target twin. They are special in terms of animation as the animation will show one animation for the attack hitting both targets.

To make this possible the target twin unit will be made available for ALL attack animations through the active\_target\_twin command target. active\_target\_twin can be used to animate the target sub twin in the same way any normal sprite is animated. 
Additionally the sub twins animations must go in the Hit Twin, Miss Twin and Destroy Twin sequences. These sequences will only be executed when an ALL attack is used and a target sub twin is available.

### Flow control commands

There a couple of special Animation Commands that help to manage the flow of an Attack Animation:

* next\_phase: this commands is intended for transitioning between the initial part of the Attack Animation, where the attacker gets things started by firing a projectile for example and the second part of the Animation where the target is hit. This command first swipes the screen to black and in this time some additional commands can be executed to set the scene for the second part of the animation(more details on that in the command list). Then if the target has a support defender this command will automatically show an animation where the target and support defender switch places. In this case the command will also delay the rest of the animation so that the designer doesn't need to worry about the time the defender switching takes up. Finally the command swipes the screen back from black and the animation can resume. This command should always be used at the end of the Main Animation sequence!

* reset_position: this command is used to reset the target of the attack animation back to its starting position relative to the current camera position. It will automatically set the target back to its idle stance and display the damage the target has taken. Importantly it will relocate the camera and the target back to the origin of the scene so that the target can start its counterattack without issues. During this transition the background positions are updated so that the transition is not visible to the player. This command should always be used at the end of the Hit sequence to ensure any counterattacks can happen seamlessly! 

### Targets

Many animation commands will have a target. As a rule of thumb commands that create elements will use the target to set the id of the created element and commands that manipulate elements will use the target as the id of the element that will be manipulated.

There a couple of special ids that refer to fixed elements of the scene:

* active\_main: The Sprite of the unit performing the current attack.
* active\_target: The Sprite of the target of the current attack. This reference will refer to the support defender when the support defender is active.
* Camera: The Camera of the Battle Scene.

## Commands

An Attack Animation is constructed as a list of Animation Commands divided into sequences(see above).

[A full reference list for commands is available here.](battle_animation_commands.md)

## Editor

### Usage

#### General Controls

![](img/battle_scene_main_controls.png)

Existing Attack Animations can be selected from the main drop down. The selected Attack Animation can be previewed in the Preview Pane by clicking the Play button. Animations can be copied or deleted and new Animations can be created. Each Animation can be given a name, though this is mostly for organization purposes, when referring to Attack Animations in the engine the id of the Animation will be used.


#### Preview controls

![](img/battle_scene_preview_controls.png)

* Play Button
* Stop Button
* Enemy Side: If set the attack will play from the enemy side. Note that the Actor and Enemy settings are not flipped
* Attack Hit: If enabled the Hit Sequence can be tested, if disabled the Miss Sequence can be tested
* Attack Destroys: Of enabled the Destroy sequence can be tested
* Attack: The attack for which the animation should play, this setting is here to enable the correct battle dialogue to play during the preview
* Environment: The Battle Environment in which the preview will take place. Note that the environment will not change for flying participants during the preview.
* Actor: The Pilot on the Actor side
* Actor Mech: The mech on the Actor side
* Enemy: The Pilot on the enemy side
* Enemy mech: The mech on the Enemy side

#### Sequence

![](img/battle_scene_sequence_commands.png)

The Sequence Drop Down lets you pick which Sequence to edit(see above for more information on Sequences).
The New Tick button prompts for a new Tick to be entered when clicked and will create the New Tick in the current Sequence. 
#### Tick Commands

![](img/battle_scene_tick_commands.png)

Each Tick has its own entry. Tick Entries can contain multiple Animation Commands, these Animation commands will start on the same Tick. Tick entries are sorted by their Animation Tick in ascending order. The Tick value can be edited at top left input of the Tick Entry. Keep in mind that if the Tick for a Tick Entry is edited to be later than an other existing Tick their positions will change. If a Tick is edited to the same value as an already existing tick a you will be prompted to either discard the already existing Tick or to combine both Tick Entries.

The Delete button allows removing an entire tick and all its Animation Commands. The New button adds one new Animation Command to the Tick Entry. 

Each Animation Command can have the following attributes:  

* Command: The id of the Animation Command
* Target: The target for the command(optional)
* Parameters: Configuration for the command, the number of parameters depends on the command.

**You can hover over the "Command" text or the name of a Parameter to see a tooltip with more information.**<br>
For more information on the Animation Commands and their parameters please refer to the [Animation Command list.](battle_animation_commands.md)

## Basic how to

### Basic animation creation flow
This is only an example workflow:  
  
* 1) Create the animation for the attack for when it hits in the "Main"sequence
* 2) Create the alterations to the animation for when it destroys the target in the "Destroy" and "Destroy Overwrite" sequences as needed
* 3) From the main animation list, send all animaiton commands that only apply when the attack hits to the "Hit" sequence using the "Send to..." control for each animation block.
* 4) Make a "Miss" sequence for the attack.

### Choosing a camera postion and angle
The recommended approach to setting a camera postion and angle is to use the camera controls in the preview window.
Play an animation and pause it, from there you can use mouse and keyboard controls in the preview window to move the camera:  

* Drag: Change the camera view angle.
* Arrow Keys: Move the camera on the z plane
* Page up/down: Move the camera up or down

Once a good position and angle has been set you can copy them to translate, teleport, rotate and rotate\_to commands by clicking the "Copy from Helper" button.

### Using the helper widget
The helper widget in the top left corner of the attack editor allows you to inspect the current position and rotation of named object in the scene. To use it pause an attack animation and type in the name(target) of an object the animation has created or Camera, active\_main or active\_target to get those default objects. You can then inspect and modify their position and rotation in the helper. You can also copy the values of the current active object in the helper to position and rotations in animation commands using the "Copy from Helper" buttons.

### Creating motion
To create animations where units move around the scene a lot it is most practical to keep the movement of the actual units to a minimum and to instead move the background to imply movement. This can be done with the bg\_scroll\_ratio command.
So instead of moving a unit accross a great distance, keep the unit in place and set a high scroll speed for the background.

### Using the transition commands
#### next\_phase
The next\_phase animation command must be used when transitioning between the windup and impact of an animations. Simple example: Unit first rocket -> next\_phase -> target is hit by rocket.
The next\_phase commands takes care of switching in support defenders automatically.

#### reset\_position
The reset\_position command must be used at the end of animation if the target moved from its default position. It will return the target and camera to their default positions so the next animation(counter attack) can start from a neutral state. By default it will also show the damage number and damage text for the target but these can be switched off.

### Making a working destroy sequence
To have a working destroy sequence a "destroy" command must be used to play the destruction animation of the unit at the end of attack animation. If you have a dynamic kill where the target unit isn't seen after the animation this is not needed.

### Small things to not forget or that add to the animations

* Use the drain\_en\_bar command to show the used EN
* Use the drain\_hp\_bar command to animate the HP being drained
* Create a dark fade using a create\_bg command(default asset available in general/fade\_black) and a fade it in with a fade\_in\_bg to about 0.6 command to darken the scene 
* Reset the camera position and background scrolls to default in the cleanUpCommands of a next\_phase command so the support defender swap in happens cleanly.
* Remove any fades in the cleanUpCommands of a next\_phase command and reapply them before impact for a more dynamic animation.
* Use animating fades to fake lighting(ex. a glow coming of an energy blast) for a more dynamic animation.
