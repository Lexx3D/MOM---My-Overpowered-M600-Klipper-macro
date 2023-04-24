# MOM---My-Overpowered-M600-macro
# Listen to MOM and everything will be alright!

MOM - My Overpowered M600 macro / written by Jay Lexx
Also tenderly called the Mother Of Macros by u/Woodcat64  

------------------------------------------------------
  NO RESPONSE TAKEN FOR ANY DAMAGE CAUSED BY MOM ;)
------------------------------------------------------
 

 09.11.2021 v0.1.6

 Sourcecode maintenance due to Klipper updates.

 v0.1.5

 - added ability to prevent nozzle cooldown

 Save this file f.e. as /home/pi/klipper_config/m600.cfg to leave printer.cfg nice and clean
 then use [include /home/pi/klipper_config/M600.cfg] in your printer.cfg
 Don't forget to configure default values in [gcode_makro m600cfg]
 

 Usage in CURA Slicer:
 Extensions > Post Processing > Modify G-Code
	Add a script -> Filament Change
			Set Layer to value at which filament should be changed
			I personally set the rest to 0, works like a charm
			( Tbh, i even didn't check if they have any effect ) 

 The M600 command can also be used to just change filament from console or via Button, so, 
 no more need for Unload,Park, Load etc. Macros anymore. The macro should return to the temp
 the printer had when it was started, regardless of printer temperature at 0, 40 or 200
 It will check if temperature is high enough to extrude filament ( you have configured your 
 min_extrude_temp in printer.cfg [extruder] didn't you ?!?), if not it will use the default 
 temperature configured anyway.


 If the printer was not homed - therefore not knowing where it is - it will perform 
 a G28 homing sequence . This will ( better say should ;) ) not happen mid print, don't worry. 
 
 -----------------------------------------------------
  THIS VERSION IS DESIGNED TO WORK ESPECIALLY WITH OCTOPRINT
 -----------------------------------------------------

In Octoprint set Plugins -> Printer Dialogs -> Enable Support = Always
 Thx to u/josolanes for mentioning the fix for this possible issue

 Those macros are in the magic box:

 [M876 S]
 Handle prompt response ( to communicate with octoprint )

 [JOBCENTER]
 Handles navigation inside the whole process ( not to be used as terminal command )

 [M125]
 Park head

 [M701]
 Load filament

 [M702]
 Unload filament

 [LOW_TEMP_CHECK T]
 Heatup process & temperature processor
 uses printer.cfg [extruder] section max_temp & min_extrude_temp

 [M600]
 Marlin compatible guided Filament Change
