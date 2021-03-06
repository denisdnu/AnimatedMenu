# Menus #
Menus are where it all starts in the plugin  
### Summary ###
#### Standard features ####
- [Enable](#user-content-enable)
- [Menu-Name](#user-content-menu-name)
- [Menu-Type](#user-content-menu-type)
- [Rows](#user-content-rows)
- [Permission](#user-content-permission)
- [Permission-Message](#user-content-permission-message)
- [Title-Update-Delay](#user-content-title-update-delay)
- [Menu-Opener](#user-content-menu-opener)
- [Menu-Opener-Name](#user-content-menu-opener-name)
- [Menu-Opener-Lore](#user-content-menu-opener-lore)
- [Menu-Opener-Slot](#user-content-menu-opener-slot)
- [Open-On-Join](#user-content-open-on-join)
- [Open-Sound](#user-content-open-sound)
- [Command](#user-content-command)
- [Hide-From-Command](#user-content-hide-from-command)
- [Click-Delay](#user-content-click-delay)
- [Delay-Message](#user-content-delay-message)
- [Items](#user-content-items)

#### Plus features ####
- [Open-Animation](#user-content-open-animation)
- [Empty-Item](#user-content-empty-item)
- [Open-Commands](#user-content-open-commands)
- [Close-Commands](#user-content-close-commands)
- [Sql-Await](#user-content-sql-await)
- [Wait-Message](#user-content-wait-message)
- [Admin](#user-content-admin)
- [Require-Other](#user-content-require-other)
- [Save-Navigation](#user-content-save-navigation)
- [Auto-Close](#user-content-auto-close)
- [Global](#user-content-global)

### Standard features ###
- #### Enable ####
  Default value: yes  
  \------------------------------  
  If disabled, this menu will not be loaded. An easy way to temporarily disable a menu.  

- #### Menu-Name ####
  Animatable, Supports placeholders  
  \------------------------------  
  This menu's title  

- #### Menu-Type ####
  The type of this menu, one of the following:  
  'Chest', 'Hopper', 'Dispenser', 'Dropper', 'Crafting'  
  If the type is 'Chest', or it is not specified, see [Rows](#user-content-rows)  

- #### Rows ####
  If [Menu-Type](#user-content-menu-type) is set to 'Chest' or not set, this is used  
  A number of 1 through 6 that specifies the amount of rows in the menu  

- #### Permission ####
  Supports placeholders  
  \------------------------------  
  The permission required to open this menu  

- #### Permission-Message ####
  Supports placeholders  
  \------------------------------  
  The message to send when the player does not have the Permission  

- #### Title-Update-Delay ####
  Default value: 20  
  \------------------------------  
  The interval in ticks between each title update  

- #### Menu-Opener ####
  The item to use to open the menu, format is &lt;type&gt;:&lt;amount&gt;:&lt;data&gt;  

- #### Menu-Opener-Name ####
  The display name [Menu-Opener](#user-content-menu-opener) must have to open the menu  

- #### Menu-Opener-Lore ####
  The lore [Menu-Opener](#user-content-menu-opener) must have to open the menu  

- #### Menu-Opener-Slot ####
  The slot to put [Menu-Opener](#user-content-menu-opener) in when a player joins  

- #### Open-On-Join ####
  Whether the menu should open when a player joins  

- #### Open-Sound ####
  The sound to play when the menu is opened, in format &lt;sound&gt;[:&lt;volume&gt;[:&lt;pitch&gt;]]  
  NOTE: This uses /playsound command names. For a list of sounds, see [this page](http://www.minecraftforum.net/forums/mapping-and-modding/mapping-and-modding-tutorials/1571574-all-minecraft-playsound-file-names-1-9)  

- #### Command ####
  The command to type to open the menu  
  Use ; to specify multiple commands, e.g. 'command1; command2'  
  This can also be a section, where you can specify more stuff:  

```YAML
Command:
  Name: 'somecommand'
  Usage: '/somecommand'
  Description: Opens a menu
  Lenient-Args: true
  Fallback: 'help'
```
  If Lenient-Args is set to false and a player was to enter too many arguments in the command, it would fail  
  The 'Fallback' option specifies a command to run when the player has entered too many arguments (or the console uses it). "/somecommand a b c" would make the player run "/help a b c"  

- #### Hide-From-Command ####
  Prevent this menu from being openable through /animatedmenu open  

- #### Click-Delay ####
  The delay (in ticks) that a player must wait before clicking an item again  

- #### Delay-Message ####
  Supports special placeholders  
  \------------------------------  
  The message to send when [Click-Delay](#user-content-click-delay) is not over yet  
  You can use these special placeholders to customize the message:  
    - **\\{hoursleft\\}** to retrieve the amount of hours left
    - **\\{minutesleft\\}** to retrieve the amount of minutes left in the hour
    - **\\{secondsleft\\}** to retrieve the amount of seconds left in the minute
    - **\\{ticksleft\\}** to retrieve the amount of ticks left in the second

  You can use formulas (e.g. \(20\\{secondsleft\\} + \\{ticksleft\\})) to get a total of something  

- #### Items ####
  Section of Key-Section pairs  
  \------------------------------  
  The items to put in this menu  
  See the [Items](items.md) page for info on how to set this up  

### Plus features ###
- #### Open-Animation ####
  Animatable  
  \------------------------------  
  The animation to play when the menu opens, in format &lt;type&gt;[:&lt;speed&gt;].  
  &lt;type&gt; can be a custom animation specified in config.yml, or one of:  
    - down, up, right, left
    - up-left, up-right, down-left, down-right
    - out, in
    - snake-down, snake-up, snake-right, snake-left


- #### Empty-Item ####
  The item to put in empty slots, see [Items](items.md) for the format.  
  If you set 'Single' to 'true', the item will only be loaded once when opening the menu instead of repeating it for each item.  
  Setting it would look something like this:  

```YAML
Empty-Item:
  Name: '&0'
  Material: stained-glass-pane:1:gray
  Single: true
```

- #### Open-Commands ####
  The commands to perform when the menu opens, see [Commands](click_handlers.md#commands)  

- #### Close-Commands ####
  The commands to perform when the menu closes, see [Commands](click_handlers.md#commands)  

- #### Sql-Await ####
  A comma-separated list of Sql Queries to request before opening the menu  
  This happens asynchronously, which means that your server won't be paused by this  
  You can use [Wait-Message](#user-content-wait-message) to specify a message to send when waiting  

- #### Wait-Message ####
  Supports placeholders  
  \------------------------------  
  The message to send when waiting for Sql-Await to complete  

- #### Admin ####
  Set to 'true' to make this an administrative menu. When this is the case:  
    - The menu is hidden from /animatedmenu open
    - The menu can only be opened through a custom command by using /&lt;command&gt; &lt;player&gt;

  You can then use %menuadmin_&lt;placeholder&gt;% to use &lt;placeholder&gt; as the target player  
  %menuadmin_player_name% would retrieve the target player's name  
  When switching between admin menus, the target player will retain until the menu is closed  

- #### Require-Other ####
  Default value: true  
  \------------------------------  
  When [Admin](#user-content-admin) is enabled, this specifies whether another player needs to be specified  
  If this is set to 'false', the effects of [Admin](#user-content-admin) no longer apply and the menuadmin placeholder uses the player itself  

- #### Save-Navigation ####
  When set to 'true', any navigation to other menus will be saved  
  This will make a player open the last opened menu when opening this menu  
  If you have some sort of paged shop, this can be quite useful  

- #### Auto-Close ####
  Specify a time after which to automatically close the menu.  
  You can use placeholders in text (item name, lore etc.) to get the time left:  
    - \\{autoclose_hoursleft\\}
    - \\{autoclose_minutesleft\\}
    - \\{autoclose_secondsleft\\}
    - \\{autoclose_ticksleft\\}

  You can either specify the amount of ticks, or a time:  
    - 1200 = 20 * 60 ticks = 1 minute
    - 3h6m5s = 3 hours, 6 minutes and 5 seconds


- #### Global ####
  When set to 'true' and AnimatedMenuPlus and AnimationLib are in the BungeeCord plugins folder, this menu will be spread across the entire BungeeCord network  
  Note that in order to send the menu's data a player needs to have been online at least once since the menu was loaded, so I recommend putting global menus in a lobby server  

