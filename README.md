# Platform Game Engine
A Platform Game Engine for AMOS

<img src="https://s4.gifyu.com/images/PlatformEngine_Cut2.gif" />

Amos has very convenient commands and underlying engines which provide easy
access to the capabilities of the Amiga hardware without the need to know the
dirty low level details. Unfortunately because the way some of them are designed
it is not possible to achieve the effects we see in games mostly written in
Assembly. Especially the display engine is an example to this. However, the
developers also provided a way to disable the built in display engine and go low
level to some extent, although we don't see many examples of it being used.
The "Copper Off" command.

By calling Copper Off and then writing your own copper list with the provided
"Cop" commands you can have access to tricks to create impressive graphics used
by Assembly coders like sprite multiplexing, screen mirroring, parallaxing,
changing color values, sprite and playfield priorities according to beam
position (aka. beam racing) etc.

But of course it comes with a price...

By installing your custom copper list, you lose the convenience of the commands
below:
All the screen commands (except Screen Open/Close and Screen Copy of course)
All the colour commands like Colour, Palette, Fade, Rainbow etc.
All the Sprite commands...

You have to handle them yourself.

This project aims to provide a template for a side-scrolling platform game
with all the subroutines and procedures required to substitute the lost
commands mentioned above. It is not limited only to a platform game by the way.
Remove platforming stuff and maybe turn it into a side scrolling shooter. It is
all up to you.
It's open source and code is commented in detail. It also comes with some tools
as open Amos code to create the tile and sprite sets to use in the game.

### Features:
  The template is designed as a single buffered DualPlayfield screen in NTSC
  compatible sizes which scrolls at 50 FPS and animate at 25 FPS. These can
  be easily modified according to needs.

- Scroll Engine  
  Highly optimized limitless horizontal scrolling algorithm is implemented.
  Supports tilemaps of any size and can scroll any speed up to 16 pixels in one
  frame. The algorithm used for scrolling is "Scroller_XUnlimited" which is
  broadly explained in: http://aminet.net/package/dev/src/ScrollingTrick.lha

- Custom Sprite Engine  
  A non-blitting* sprite engine that automatically handles attaching and/or
  connecting hardware sprites. Data is loaded as an Amos bank, but it has a
  completely different data structure.

  (*)built-in sprite engine in Amos uses blitter to set image data to sprites,
  this one doesn't and saves some time for your Bobs.

- Color Fade Engine  
  A totally new algorithm which can fade colors in and out in any steps, keeping
  color hues constant during fade and making brighter colors appear/disappear
  simultaneously with darker ones. It can fade all color changes (ie. Rainbows)
  in the copper list as well.
  And it only uses addition/subtraction, so highly optimized.

- Collision and animation routines  
  Some essential loops and variables are set up to provide a basic animation
  and platforming logic.

- Demo graphics  
  A test tileset and background scenery converted to the required data formats
  are included.  
  Tileset and background art by: Amatnieks (aamatniekss.itch.io)  
  Player sprite image art by: Legnops (legnops.itch.io)

- Tools  
   * Sheet2CustomSprite.AMOS  
         Grabs sprite images from iff sprite sheets and creates a bank.  
   * CustomSpriteMerger.AMOS  
         Merges two sprite banks into one.  
   * Sheet2TileSet.AMOS  
         A code to grab tiles from tile sheets into an Amos Icon bank.  

### Requirements:  
   A classic Amiga computer.  
   AmosPro 2.00 or above.

### Licence:
  This is public domain. Use it whatever way you want. However I'd be truly very
  very grateful if you'd mention my name in your credits. Thanks in advance. :)

### Version 0.34 (06.04.2021):
- Initial release version.
