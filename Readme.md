===========================================================================

# LINKS #

AUTO-SCANNER NEXUS PAGE : https://www.nexusmods.com/fallout4/mods/56255

BUFFOUT 4 NEXUS PAGE : https://www.nexusmods.com/fallout4/mods/47359

HOW TO INSTALL BUFFOUT 4 : https://www.nexusmods.com/fallout4/articles/3115

HOW TO READ CRASH LOGS : https://docs.google.com/document/d/17FzeIMJ256xE85XdjoPvv_Zi3C5uHeSTQh6wOZugs4c

FOR WINDOWS 7 SUPPORT, GET LATEST PYTHON VERSION FROM HERE: https://github.com/adang1345/PythonWin7

===========================================================================
# CONTENTS #

Crash Log Auto-Scanner is bundled with several files:

*Scan Readme.md* - The file that you're reading right now.

*Scan Crashlogs.py* - Main script for scanning crash logs generated by Buffout 4. You can place this file into your Documents\My Games\Fallout4\F4SE folder
and run Scan Crashlogs.py by double clicking on it. After scanning completes, close the cmd window, then open any -AUTOSCAN.md file and read what they say.

*Scan Crashlogs.ini* - Configuration file for *Scan Crashlogs.py* where some parameters can be adjusted.

*HOW TO USE AUTO SCANNER.gif* - Looping gif that shows how the script should be used. Don't forget to install Python!

*HOW TO READ CRASH LOGS.pdf* - Document that lists most common Buffout 4 crash log messages and errors, and ways to prevent or fix them.

*CL TOOLS* - Folder with extra scripts for advanced crash log file searching and troubleshooting. (Useful if you like to hoard crash logs).

===========================================================================
# HOW TO READ AUTOSCAN FILES #

After running *Scan Crashlogs.py*, you'll see the following in any *crash-time-and-date-AUTOSCAN.md* output file:
==========
The part above the Main Error shows the name of the scanned crash log and the Auto-Scanner version that was used.

The Main Error segment shows the main error message type and call stack address where the crash likely originates from.
In 95% of cases, the main error will be "EXCEPTION_ACCESS_VIOLATION", meaning the game couldn't access some required data for one reason or another.
The next part is the program or file where the crash originates from and lastly the call stack address that was last accessed before the crash occurred.
NOTE: The call stack address and its values have NOTHING to do with any Plugin or Game IDs. Don't bother trying to match these numbers with your load order.

The part below the Main Error shows the version of Buffout 4 that was used when the crash log was generated and the latest version of Buffout 4 available.

* CHECKING IF BUFFOUT4.TOML PARAMETERS ARE CORRECT * segment checks the Buffout4.toml file inside the game's Fallout 4\Data\F4SE\Plugins folder.
Depending on which mods you have installed, you might need to manually correct the parameters in Buffout4.toml with a text editor as explained by this segment.

* CHECKING IF LOG MATCHES ANY KNOWN CRASH MESSAGES * segment checks the database of all crash errors that are either known about or can be solved.
If any crash messages show CULPRIT FOUND!, this requires that you OPEN the "How To Read Crash Logs" PDF included with the auto-scanner archive
or the online version of that same document and look up all detected crash messages / errors.

* CHECKING FOR MODS THAT CAN CAUSE FREQUENT CRASHES * segment checks the database for mods that are known to cause major problems or frequently crash the game.
You are supposed to temporarily disable any mods detected here and recheck your game to see if the crash went away. If not, continue to the next segments. 

* CHECKING FOR MODS WITH SOLUTIONS & COMMUNITY PATCHES * segment checks the database for mods that can cause various problems or crashes,
but already have available fixes or alternatives as explained by this segment. You should visit this Important Patches & Fixes article:
https://www.nexusmods.com/fallout4/articles/3769 which lists all important community patches and fixes for the base game and various mods.

* CHECKING FOR MODS PATCHED THROUGH OPC INSTALLER * segment checks the database for mods that are patched through my own Optimization Patches Collection mod.
You are supposed to visit this page https://www.nexusmods.com/fallout4/mods/54872, then download and install the main file with your mod manager.

* SCANNING THE LOG FOR SPECIFIC (POSSIBLE) CUPLRITS * segment checks the crash log for any
mentions of Plugins, FormIDs or Game Files that were possibly involved when this crash occurred.
If you weren't able to fix the crash so far, you can search for any Game Files, look up any FormIDs in FO4Edit
or disable any Plugins listed in this segment to further confirm if they caused this crash or not. If all else fails, perform a Binary Search.

===========================================================================
# THINGS TO DO IF NO CRASH LOGS ARE GIVEN OR IF AUTO-SCAN DOESN'T HELP #

0. Make sure that you've installed all Buffout 4 requirements correctly! And it's best that you install everything manually, WITHOUT using your Mod Manager!
Install all programs manually and files by manually placing them into required folders. This ensures that all required files are ALWAYS loaded by the game.

1. Run Plugin Checker in Wrye Bash and do what it says. Instructions at the end of this article: https://www.nexusmods.com/fallout4/articles/3115

2. Run FO4Edit and load all of your mods, then select all mod plugins (CTRL + A), right click and check for errors.
If any plugins have a bunch of errors (IGNORE Base Game and DLC plugins), disable or clean them by using Quick Auto Clean from FO4Edit
or by opening and resaving that plugin with the Creation Kit. Manually install Creation Kit Fixes as well: https://www.nexusmods.com/fallout4/mods/51165

3. Carefully read both https://www.nexusmods.com/fallout4/articles/3115 for list of mods that frequently cause crashes or other problems and
https://www.nexusmods.com/fallout4/articles/3769 for list of important community patches and fixes for the base game and mods.
Disable, fix, test and install any mods relevant to your situation. If all else fails, perform a binary search.

4. Reset your INI files. This is done by deleting all .ini files inside your Documents\My Games\Fallout4 folder and running the game
once directly through Fallout4Launcher.exe. Once you reach the main menu, exit the game and run BethINI to readjust INI settings.

5. Find the culprit(s) through a BINARY SEARCH. Sometimes, your only viable option is brute force. Instructions below.

===========================================================================
# BINARY SEARCH 101 #

It's an algorithm (method) for tracking down the exact crash culprit as fast as possible when crash logs aren't helpful. Here's a clear example on how to do it.
Of course, this method can (very) rarely backfire since the game could crash due to missing scripts from deactivated content, but it is what it is.
Let's say you have 200 activated plugins in total, and let's give all those plugins arbitrary names. (Plugin1, Plugin2, Plugin3... all the way to Plugin200).

First, backup your latest save before doing this! Saves are located in your Documents\My Games\Fallout4\Saves folder.
Your goal is to disable half, only leave all plugins from Plugin1 to Plugin100 enabled. After that:

-> If the game crashes again, then you know the culprit is somewhere between Plugin1 and Plugin100.  Now you disable half of those, so you only leave plugins from
Plugin1 to Plugin50 enabled and test again. Each time you crash, disable half of the plugin range from which you deduced it must contain the crashing mod.

-> If the game doesn't crash,  then you know the culprit is somewhere between Plugin101 and Plugin200. Now enable half of the ones you disabled, so you leave plugins from
Plugin101 to Plugin150 enabled and test again. Each time you don't crash, enable half of the plugin range from which you deduced it must contain the crashing mod.

Repeat this logic until you're (hopefully) left with one mod that you had to leave disabled for the game not to crash, and that's your culprit.
Basically, for each group of mods you disable, whichever half crashes is the one that contains the Impostor. Use your sussy brain to vote him out. ඞ
After that, enable all other mods and continue from the save before you stared the binary search (in case you kept making exit saves while testing it out). 
Another example, with mods A, B, C, D, E, F, G and H:

ABCDEFGH
Crash

ABCD | EFGH
Crash

AB | CD EFGH
Crash

A | B CDEFGH
No Crash

B must be the sussy boi since the game didn't crash with only Mod A enabled while all other mods are disabled, but it did crash with both Mod A & B enabled.

===========================================================================
# LATEST CHANGES #

- (Future updates will likely take much longer due to lack of feedback / data for some crash errors.)
- (Porting Auto-Scanner to Skyrim will be next. If you're reading this and want to help, let me know.)

5.90
* MAIN SCRIPT *
- Minor adjustments to text in the Auto-Scanner console window to prevent weird behavior.
- Merged commit created by [evildarkarchon] on GitHub that cleans up some things with *FCX Mode*
- Fixed Auto-Scanner reporting *Animation / Physics Crash* and *Player Character Crash* false positives.

* OTHER FILES *
- *Scan Crashlogs.exe* no longer checks for updates to prevent infinite looping problems.
