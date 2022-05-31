# Text Script Manual v0.1

## Demo
For explanations of script structure please check the demo files in the text_scripts/demo folder.

This manual will serve as a reference for available commands and other misc. information.



## Text 

A text box is defined as follows:

```
*Harold
This is a text box!
It can have up to
Three lines! 

```

When interpreted by the script processor the above will show one text box with the portrait for Harold's default expression. It will
also automatically print the character's name at the start of the text box.


Other expressions can be used as follows:

```
	
*Harold
This is a text box!
It can have up to
Three lines! 

*Harold angry
Reading docs is very upsetting!
```

When inserting text it is important that there's one(and only one!) newline between text boxes. When interpreted the above will show two textboxes in succession.


To do non-character text the following can be done:

```
*TEXT
Generic text line 1
Generic text line 2
Generic text line 3
Generic text line 4

```
 
 
 When interpreted the above will show one textbox with the four lines of text. No portrait will be shown and no name will be printed.

### Skipping the auto focus

Sometimes you may not want a unit to be auto focused when a text box for them is shown. In that case add a one after the expression name.

```
*Harold 0 1
This is a text box!
It can have up to
Three lines! 

```

The above shows a text box for Harold's default expression without focusing him on the map even if he is deployed.
 
The next chapter explains how the expressions are defined.

## Defining Script Characters

Script characters are defined in data/ScriptCharacters.json. This file defines each name that can be used for a textbox and what expression are available for that character.

```

"Harold": {
	"nameVar": -1,
	"actorId": 	1,
	"expressions": {
		"0": {"face": "Actor1", "index": 0},
		"angry": {"face": "Actor1", "index": 1}
	}
},

```

* "Harold": the name of the character, to be used at the start of a text box.
* nameVar: if not -1 the name for the character will be taking from the game variable with the specified id
* actorId: if defined and if the matching actor is deployed on the map the cursor will automatically snap to them when a text box for the character is displayed
* expressions: contains multiple entries where the key is the name of the expression. Each entry defines which face image file and which face index in that file is used for that expression. **Note that 0 is the default expression and should always be present**


## Available RPG Maker commands

* fadeIn 

* fadeOut
* wait amount
* showBackground background\_id picture\_name 
* hideBackground background\_id					
* playSE se\_name volume[90] pitch[100] pan[0]
* playBGM bgm\_name volume[90] pitch[100] pan[0]
* fadeOutBGM duration					
* setVar var\_number value
* addVar var\_number value
* subVar var\_number value
* mulVar var\_number value
* divVar var\_number value
* modVar var\_number value
* setSwitch switch\_number state[ON|OFF]
* pluginCmd plugin\_cmd\_name arg0...argN <br>
	Note: All engine commands are available first tier commands in this scripting format, so this command should generally not be used.
* gameOver
* shakeScreen intensity\_x intensity\_y duration wait[wait] 
* showAnimation event\_id animation\_id wait[wait] 
* tintScreen color[r,g,b,a] duration wait[wait] 
* label label\_name
* jumpLabel label\_name
* changePartyMember pilot\_id operation[add|remove]
* warp map\_id target\_x target\_y


## SRW Engine MV specific commands
					
* txtLayout display\_type position<br>	
Set the the text layout for all following text boxes, default is "window bottom".<br>
display\_type: window,dim,transparent<br>
display\_type: top,middle,bottom<br>

	
All Plugin Commands specific to SRW Engine MV are available as first tier commands.<br>
Example: [unlockUnit:] or [moveEventToActor: 5 1]<br>
There is no need to use the pluginCmd command.

See the general manual for info on the functionality of the Plugin Commands.