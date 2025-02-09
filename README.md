FNAIFY(1) - General Commands Manual

# NAME

**fnaify** - script to get FNA-based games ready to run on OpenBSD

# SYNOPSIS

**fnaify**
\[**-i**&nbsp;|&nbsp;**-y**]
\[**-hv**]
\[**-d**&nbsp;*depdir*]
\[**-m**&nbsp;*monopath*]
\[*gamedir*]

# DESCRIPTION

**fnaify**
sets up games based on the FNA engine to operate with OpenBSD-native
libraries and its
mono(1)
runtime.

As of version 2.0,
**fnaify**
has been extended to attempt configuring XNA games as well.
**fnaify**
can be run in 3 basic modes regarding the addition of missing libraries:
restrictive, interactive, and permissive.

The arguments are as follows:

**-i** | **-y**

> The mode determines how
> **fnaify**
> handles situations where compatibility problems are identified that can
> be addressed with drop-in DLL replacements, or where an option needs to
> be selected.
> With
> **-i**,
> **fnaify**
> runs in interactive mode, meaning the user will be prompted in every
> case.
> With
> **-y**,
> **fnaify**
> runs in permissive mode
> (**-y**
> for
> "yes"
> to all)
> .
> This means that any suggested drop-in DLLs will be installed,
> and if different options are possible (like picking among several .exe
> files for the launch script), the first one will be selected
> automatically.
> If neither
> **-i**
> nor
> **-y**
> is specified,
> **fnaify**
> runs in restrictive mode, that is no drop-in DLLs will be installed.

**-d** *depdir*

> Add
> *depdir*
> to the directories to search for native library dependencies.
> A directory specified this way will be searched
> *before*
> the default locations
> (*/usr/local/lib* etc.).

**-m** *monopath*

> Add
> *monopath*
> to the directories the
> mono(1)
> runtime will search for DLLs.

**-h**

> Prints help text.

**-v**

> Verbose mode.

*gamedir*

> Optional.
> Path to the game directory to process.
> If not specified, the current working directory will be used.

# SUPPORTED GAMES

The Adventures of Shuggy  
Apotheon  
Bleed  
Bleed 2  
Breath of Death VII  
Brushwood Buddies  
Capsized  
Chaos Heart  
Charlie Murder  
Chasm  
CometStriker  
Cryptark  
Cthulhu Saves the World  
Curse of the Crescent Isle DX  
Dad Quest  
Dead Pixels II  
The Dishwasher: Vampire Smile  
Dust: An Elysian Tail  
Escape Goat  
Escape Goat 2  
FEZ  
Fist Puncher  
Flinthook  
Flotilla  
Gateways  
Growing Pains  
HackNet  
Hive  
Hyphen  
Jon Shafer's At the Gates  
LaserCat  
Mercenary Kings  
Ninja Warrior  
One Finger Death Punch  
Overdriven Reloaded  
Owlboy  
Paladin  
Penny Arcade's On the Rain-Slick Precipice of Darkness 3  
Penny Arcade's On the Rain-Slick Precipice of Darkness 4  
Press X to Not Die  
Rex Rocket  
Rogue Legacy  
Salt and Sanctuary  
Shipwreck  
Skulls of the Shogun  
Soulcaster 1 & 2  
SpeedRunners  
Stardew Valley  
Sumico  
Super Amazing Wagon Adventure  
Super Rad Raygun  
Timespinner  
TowerFall: Ascension  
Unexplored  
Unholy Heights (no audio)  
The Useful Dead  
Wizorb  
Wyv and Keep

# FILES

*~/.config/fnaify/fnaify.dllmap.config*

> Configuration file to map DLLs to native libraries, based on OpenBSD
> library naming.

# EXIT STATUS

**fnaify**
returns 1 if an error occurred with the arguments of files provided,
otherwise 0.

# EXAMPLES

Run in permissive mode, suitable to set up most supported games
automatically.

	$ fnaify -y path/to/game/directory

Run in interactive mode.
**fnaify**
will prompt the user if any additional DLLs are recommended, or if a
file needs to be selected for the launch script.

	$ fnaify -i path/to/game/directory

# SEE ALSO

mono(1)

# HISTORY

The
**fnaify**
utility was originally created in December 2017 by
Thomas Frohwein &lt;[thfr@openbsd.org](mailto:thfr@openbsd.org)&gt;

# RELEASE HISTORY

2\.0

> Add support for XNA games.
> Introduce modes
> **-i** | **-y**
> to facilitate adding in needed assemblies/libraries.

1\.3

> Add prompt to download and replace
> *FNA.dll*
> if incompatible version is found.
> Detect steamstubs directory and use Steamworks stubs if present.

1\.2

> FreeBSD portability fixes, account for more special cases (MidBoss,
> Adventures of Shuggy, Atom Zombie Smasher), add directory path to plug
> in additional libraries.

1\.1

> Fix bug selecting .exe by separating input variables.

1\.0

> Initial release.

# AUTHORS

Thomas Frohwein &lt;[thfr@openbsd.org](mailto:thfr@openbsd.org)&gt;

OpenBSD 6.6 - September 21, 2019
