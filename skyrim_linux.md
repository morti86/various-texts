This is the new guide on how to run modded Skyrim under Linux.

## Mod Manager
For the easiest installation use [Fluorine Mod Manager](https://github.com/SulfurNitride/Fluorine-Manager). It is based on MO2 with some features streamlining installation under Linux. It will create the prefix by itself, so you do not need to use protontricks manually.

For the rest of the text the *SKYRIM_PREFIX* is a replacement for the path to the prefix used by Skyrim.

Options:
`PROTON_DXVK_LOWLATENCY=1 PROTON_ENABLE_WAYLAND=1 command%`

## Proton version
Use Proton (GE) 10 because Proton 11 prevents the game from loading. This must be the issue of some DLL mod not working under it. If I find the solution, I'll post it.

## Community Shaders
I consider ENB to be a legacy solution now. CS has grown so much that I see no point fighting with it. CS just works. CS looks great and has plenty of modern features. It has one click upscaling/framegen support too.

### Reshade
Choose the version for DirectX 11

### HDR
Add the following options if you want it: `PROTON_ENABLE_HDR=1 DXVK_HDR=1 ENABLE_HDR_WSI=1 %`

## SSEEdit and Sniff
Those are troublesome. They reqire setting Wine compatibility to Windows XP and this cannot be done to the main game prefix. There is a workaround. I'll use Bottles.

1. Create a new Bottle, let's call it SSEEdit
2. In the settings set the program to *Soda 9.0.1* and the version of Winwods to _Windows XP_
3. Look for the file called `~/.local/share/bottles/bottles/SSEEdit/bottle.yml` and copy it inside the Skyrim prefix directory
4. `rm -rf ~/.local/share/bottles/bottles/SSEEdit`
5. `ln -s SKYRIM_PREFIX ~/.local/share/bottles/bottles/SSEEdit`
6. Start SSEEdit from Bottles now and see if it works. It may throw and error saying that it cannot find the ini file. Note the path where it was trying to find it. The problem might be with the username used by Bottles and Steam prefix.

Steam uses *steamuser* while Bottles uses your username. In this case do the following:
- `ln -s SKYRIM_PREFIX/drive_c/users/steamuser/Documents/My\ Games SKYRIM_PREFIX/drive_c/users/(username)/My\ Games` unless you already have *My Games* directory in your home dir. Then create a link inside it to the *Skyrim Special Edition* directory in the prefix.

And try if it works now. If it does but shows only the base game it is all right. Now you need to close it, in the mod manager in the data tab use *browse VFS* button to mount the VFS. Then when you run SSEEdit again, you should see all mods.

## Creation Kit
I do not know whether it works right. I can see some issues with the call view window: trying to drag and drop items is troublesome. There might be other problems too.
Install the [Creation Kit Platform Extended](https://www.nexusmods.com/skyrimspecialedition/mods/71371) into the game main directory. Not through the mod manager.

If it still loads the vanilla CK, then try setting DLL overrides:
<img width="707" height="476" alt="image" src="https://github.com/user-attachments/assets/b65cfac8-3720-4784-abf2-4036560ce9a4" />

## Pandora Engine
Works fine although there can be a glitch if you install new plugin and need to rerun it. If it throws error than rerun it with only the base ticked, close it and then run it with all stuff selected.

### TK Dodge
This one can be troublesome because it is three plugins for compatibility. Use:
- TK Dodge SE
- TK Dodge RE - Script free
- TK Dodge NG
- TK First person fix for Pandora

- For the first one, just like in the instruction for RE, hide all the files that are outside *meshes* folder.

## PG Patcher
If requires setting a launch option as below:
<img width="713" height="476" alt="image" src="https://github.com/user-attachments/assets/0764604c-96fc-4bc1-b425-9d7439931bbe" />

## Those work fine
- BodySlide
- OutfitStudio
- TexGen
- DynDOLOD
