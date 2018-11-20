fnaify 1.1-fbsd
===============

created 2017-12-27
by Thomas Frohwein (thfr)

FreeBSD version 2018
by Mariusz Zaborski (oshogbo@)

Note:
-----
Please notice that this is an unofficial fork of the fnity implemented by Thomas Frohwein.

The orginal source code: https://thfr.info/cgi-bin/cvsweb/projects/fnaify/

The goal of this fork is to port the OpenBSD version of this script to FreeBSD.

For more details: https://oshogbo.vexillium.org/blog/58/

Intro:
------
Script to get FNA-based games ready to run on {Free,Open}BSD

FNA is a reimplementation of the Microsoft XNA Game Studio 4.0 Refresh libraries.
Thanks to the great work by Ethan Lee (flibitijibibo) games using FNA are
highly portable and can even run on {Free,Open}BSD.
Please refer to https://fna-xna.github.io/ for more information about FNA

Requirements:
-------------

- SDL_GetPlatform to recognize OS. {Free,Open}BSD's SDL2 upgrade to 2.0.7
  achieves this by returning "Linux" until FNA patches to recognize
  *BSD platforms have been rolled out.
  You can check with [sdl2plat](https://github.com/thfrwn/sdl2plat)
  which platform is returned by SDL_GetPlatform.
- mono: package available for -current, but not for 6.2 or 6.3. However, a
  version of mono with a few bugs can likely be built from the ports tree, by
  removing the line starting with `BROKEN`
- game-specific libraries, like theoraplay, mojoshader, ... fnaify
  should abort and tell you which libraries need to be installed if
  some of them can't be found.

Usage:
------

`fnaify [-v] [-h]`

`-h`:	display usage information
`-v`:	enable verbose output

Status:
-------

The following games have been reported to work with this script:

* The Adventures of Shuggy (needs different FNA.dll than the bundled one)
* Apotheon (needs a different FNA.dll than the bundled one)
* Atom Zombie Smasher (needs [AZSNotSFML](https://github.com/flibitijibibo/AZSNotSFML))
* A Virus Named TOM
* Bleed
* Bleed 2
* Brushwood Buddies (needs a different FNA.dll than the bundled one)
* Capsized
* Curse of the Crescent Isle DX (needs different FNA.dll than the bundled one)
* Dust: An Elysian Tail
* Escape Goat
* Escape Goat 2
* FEZ
* Gateways
* HackNet (only runs with -disableweb which is automaticall set by fnaify)
* Hidden In Plain Sight
* Hyphen
* Overdriven Reloaded
* Owlboy
* Paladin
* Press X to Not Die
* Rogue Legacy
* Shipwreck
* Skulls of the Shogun
* Soulcaster 1
* Soulcaster 2
* Stardew Valley (recommend data size limit of 2G)
* TowerFall: Ascension
* Wizorb (needs a different FNA.dll than the bundled one)
* Wyv and Keep (needs a different FNA.dll than the bundled one)

Caveats
-------

* It is recommended to obtain copies of the FNA games that are DRM-free and can
  run without the Steam client.
* Some FNA games use non-free libraries like FMOD/FMODStudio that are not
  available on {Open, Free}BSD.

Release History
---------------

1.1-fbsd:	rewritten to Bourne shell
1.1:		fix bug selecting .exe by separating input variables
1.0:		initial release
