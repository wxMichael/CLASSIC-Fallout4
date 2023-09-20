===========================================================================
# LINKS #

How To Install Buffout 4 : https://www.nexusmods.com/fallout4/articles/3115

Fallout 4 Important Patches & Fixes : https://www.nexusmods.com/fallout4/articles/3769

Fallout 4 Advanced Troubleshooting: https://www.nexusmods.com/fallout4/articles/4141

Crash Log Auto-Scanner & Setup Integrity Checker: https://www.nexusmods.com/fallout4/mods/56255

XEDIT Plugin Auto Cleaning Tool - https://www.nexusmods.com/fallout4/mods/69413

HOW TO READ CRASH LOGS Online Doc: https://docs.google.com/document/d/17FzeIMJ256xE85XdjoPvv_Zi3C5uHeSTQh6wOZugs4c

===========================================================================
# CONTENTS & FILES #

**CLASSIC Readme.md** - The file that you're reading right now.

**CLASSIC Data** - Folder with all files and data required for *CLASSIC.exe* to run. Needs to be in the same folder with *CLASSIC.exe* OR in *CLASSIC Data* folder.

**CLASSIC.exe** - Main executable for scanning your crash logs and game/mod files. CLASSIC will automatically grab crash log files from your Script Extender folder
and generate AUTOSCAN report files for them. After scanning completes, open any *-AUTOSCAN.md* file with a text editor (Notepad++ or similar) and read it.

**CLASSIC Ignore.txt** - Configuration file for source scripts and the executable where you can add plugin names that you want CLASSIC to ignore.

**CLASSIC Settings.yaml** - Configuration file for source scripts and the executable where various CLASSIC settings can be adjusted.

**HOW TO READ CRASH LOGS.pdf** - Document that lists most common Buffout 4 crash log messages and errors, and ways to prevent or fix them.

===========================================================================
# HOW TO RUN CLASSIC FROM THE MO2 SHORTCUT #

If you are using Mod Organizer 2, you should create a shortcut for *CLASSIC.exe* in MO2.
To do this, run MO2 and select *<Edit...>* from the dropdown menu located next to the *Run* button.

This allows you to remove from or add executables to MO2.
This is required so CLASSIC can correctly locate game and mod files.
> Simply press the Plus Icon > Add From File... and select your *CLASSIC.exe* file from the new window.
> Press OK to save this Executable and make sure it's selected in the MO2 dropdown menu, then press Run.

===========================================================================
# HOW TO READ AUTOSCAN FILES #

AFTER RUNNING THE EXE, YOU'LL SEE THIS IN ANY GENERATED *crash-time-and-date-AUTOSCAN.md* REPORT FILE:

==========
[The part above the Main Error shows the name of the scanned crash log and the CLASSIC version that was used.]

* Main Error * segment shows the main error message type and call stack address where the crash likely originates from.
In 99% of cases, the main error will be "EXCEPTION_ACCESS_VIOLATION", meaning the game couldn't access some required data for one reason or another.
The next part is the program or file where the crash originates from and lastly the call stack address that was last accessed before the crash occurred.
* NOTE: THE CALL STACK ADDRESS AND ITS VALUES HAVE NOTHING TO DO WITH ANY PLUGIN OR GAME IDs. DON'T BOTHER TRYING TO MATCH THESE NUMBERS WITH YOUR LOAD ORDER. *

[The part below the Main Error shows the Buffout 4 version that was installed when this crash log was generated.]
==========
* CHECKING IF BUFFOUT4.TOML PARAMETERS ARE CORRECT * segment checks the Buffout4.toml file inside the game's Fallout 4\Data\F4SE\Plugins folder.
Depending on which mods you have installed, you might need to manually correct the parameters in Buffout4.toml with a text editor as explained by this segment.
==========
* CHECKING IF LOG MATCHES ANY KNOWN CRASH MESSAGES * segment checks the database of all crash errors that are either known about or can be solved.
If any crash messages show SUSPECT FOUND!, this requires that you OPEN the "How To Read Crash Logs" PDF included with the auto-scanner archive
or the online version of that same document and look up all detected crash messages / errors.
==========
* CHECKING FOR MODS THAT CAN CAUSE FREQUENT CRASHES * segment checks the database for mods that are known to cause major problems or frequently crash the game.
You are supposed to temporarily disable any mods detected here and recheck your game to see if the crash went away. If not, continue to the next segments.
==========
* CHECKING FOR MODS THAT CONFLICT WITH OTHER MODS * segment checks the database for mods that are incompatible or known to conflict with your other installed mods.
If any two mods are reported as conflicting, you are supposed to choose which one you want to keep and then disable or uninstall the other mod, to prevent conflicts.
==========
* CHECKING FOR MODS WITH SOLUTIONS & COMMUNITY PATCHES * segment checks the database for mods that can cause various problems or crashes,
but already have available fixes or alternatives as explained by this segment. You should visit this Important Patches & Fixes article:
https://www.nexusmods.com/fallout4/articles/3769 which lists all important community patches and fixes for the base game and various mods.
==========
* CHECKING FOR MODS PATCHED THROUGH OPC INSTALLER * segment checks the database for mods that are patched through my own Optimization Patches Collection mod.
You are supposed to visit this page https://www.nexusmods.com/fallout4/mods/54872, then download and install the main file with your mod manager.
==========
* SCANNING THE LOG FOR SPECIFIC (POSSIBLE) CUPLRITS * segment checks the crash log for any
mentions of Plugins, FormIDs or Game Files that were possibly involved when this crash occurred.
If you weren't able to fix the crash so far, you can search for any Game Files in the FO4 install folder, look up any FormIDs in FO4Edit
or disable any Plugins listed in this segment to further confirm if they caused this crash or not. If all else fails, perform a Binary Search.

===========================================================================
# I DIDN'T GET A CRASH LOG OR THE AUTOSCAN REPORT DIDN'T HELP #

> READ THIS ARTICLE: https://www.nexusmods.com/fallout4/articles/4141

===========================================================================
# GENERATING YOUR OWN FORM ID LIST FROM ALL ACTIVE MODS #

- CLASSIC can automatically look up (most) values of mod FormIDs, you just need to generate your own FormID List.

- To generate the FormID List:
1) Place the *Generate FormID List.pas* from the *CLASSIC Data* folder into your FO4Edit/Edit Scripts folder.
2) Now run FO4Edit.exe and check all plugins you wish to include in the FormID List (I RECOMMEND YOU CHECK / ENABLE ALL PLUGINS).
3) Press OK while holding [Shift] to load your plugins in FO4Edit. Once all plugins are loaded, right click on any plugin and select *Apply Script...*
4) From the dropdown menu, select *Generate FormID List* and press OK. Depending on how many plugins you have, this will take some time (5-25 mins).
5) Once the full FormID List is generated, FO4Edit will ask you to save this list. Save it as a text file, then rename it to: FO4 FID Mods.txt
6) Now place your own generated *FO4 FID Mods.txt* file into the *CLASSIC Data/databases* folder and overwrite existing *FO4 FID Mods* file.
   (Make sure the original *FO4 FID Mods.txt* gets overwritten! If it doesn't, check the name and make sure the extension is set to .txt)
7) Run CLASSIC, enable *Show FID Values* under CLASSIC Settings and that's it! Scan your crash logs, the autoscan will do the rest.

[!] REMINDERS

- Once you overwrite the original *FO4 FID Mods.txt*, crash log file scan will take much longer if you have *Show FID Values* enabled.
To ensure the scan doesn't take as long, only scan a few crash logs (less than 10) at any given time.
[ Delete or move any extra crash log files to another folder so CLASSIC can't find them. ]

- The script will not be able to generate values for ALL FormIDs, around 12% don't have usable names that CLASSIC can display.
You will see [CHECK MANUALLY WITH XEDIT] for these FormIDs. These are usually NavMesh records, but you can check with FO4Edit anyway.

- To stop CLASSIC from checking the FormID List, either delete, rename or move your generated *FO4 FID Mods.txt* file somewhere else.
CLASSIC will simply create a placeholder file again if needed and stop checking FormID values until a new FormID List is provided.

===========================================================================
# BINARY SEARCH 101 #

This is an algorithm (method) for tracking down the exact crash suspect as fast as possible when crash logs aren't helpful. Here's a clear example on how to do it.
Of course, this method can (very) rarely backfire since the game could crash due to missing scripts or files from deactivated content, but it is what it is.
Let's say you have 200 activated plugins in total, and let's give them arbitrary names. (Plugin1, Plugin2, Plugin3... all the way to Plugin200).

First, backup your latest save before doing this! Saves are located in your Documents\My Games\Fallout4\Saves folder.
Your goal is to disable half of your plugins, only leave plugins from Plugin1 to Plugin100 enabled. After that:

-> If the game crashes again, then you know the suspect is somewhere between Plugin1 and Plugin100. Now disable half of those, so you only leave plugins from
Plugin1 to Plugin50 enabled and test again. Each time you crash, *disable* half of the plugin range from which you deduced it must contain the crashing mod.

-> If the game doesn't crash, then you know the suspect is somewhere between Plugin101 and Plugin200. Now enable half of the plugins you disabled, so all plugins from
Plugin101 to Plugin150 are enabled and test again. Each time you don't crash, *enable* half of the plugin range from which you deduced it must contain the crashing mod.

Repeat this logic until you're (hopefully) left with one mod that you had to leave disabled for the game not to crash, and that's your culprit.
Basically, for each group of mods you disable, whichever half crashes is the one that contains the Impostor. Use your sussy brain to vote him out. ඞ
After that, enable all other mods and continue from the save before you stared the binary search (in case you kept making exit saves while testing it out).

For more details, see: https://docs.google.com/document/d/17FzeIMJ256xE85XdjoPvv_Zi3C5uHeSTQh6wOZugs4c