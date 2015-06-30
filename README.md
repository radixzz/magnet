Magnet
======

![Screenshots of Magnet functionality in portrait and landscape](https://www.imageupload.co.uk/images/2015/06/26/magnet_screenshot.png)

Position Helper for Corona SDK Graphics 2.0

A module to position display objects on different screen resolutions. This helper will only work with the newest version of Corona (aka 2.0). Anchors and screen orientations are internally managed to provide consistency.

Recent changes:
  - _Storyboard_ replaced with _Composer_ API
  - Refreshed _build.settings_ with portrait orientation as a default
  - Removed all _print()_ logs

Positioning
===========

To position you just call the function and pass the displayObject
```lua
magnet:topLeft( displayObject )
```

Margins
=======

If you need to have a margin of 10px from the left this is how you do it:
```lua
magnet:topLeft( displayObject, 10 )
```
or same as before but with 20 px from the top:

```lua
magnet:topLeft( displayObject, 10, 20)
```

If you want to reposition after a screen rotation all you need to do is call the following function on the orientation event:
```lua
magnet:updateCurrentOrientation()
```

Basic Alignments
=======
```lua
magnet:top(obj, marginY)
magnet:right(obj, marginX)
magnet:bottom(obj, marginY)
magnet:left(obj, marginX)
magnet:center(obj, marginX, marginY)
```
Composed Alignments
=====
```lua
magnet:topLeft(obj, marginX, marginY)
magnet:topRight(obj, marginX, marginY)
magnet:bottomLeft(obj, marginX, marginY)
magnet:bottomRight(obj, marginX, marginY)
magnet:topCenter(obj, marginX, marginY)
magnet:centerRight(obj, marginX, marginY)
magnet:bottomCenter(obj, marginX, marginY)
magnet:centerLeft(obj, marginX, marginY)
```

Generic Call
=====
Or a generic call with the align as a parameter:
```lua
magnet:alignTo(sAlign, obj, ...)
```
where sAlign is the method name in a string like: 
```lua
magnet("bottomRight", myObject, xMargin, yMargin)
```

Other utilities
======
```lua
magnet:getPercentX( percent )
magnet:getPercentY( percent )
```

Gotchas
======
When positioning display objects inside snapshots you'll need to provide an additional parameter "parent" as the current snapshot that contains it. Otherwise it won't work!
```lua
local snapshot = display.newSnapshot(width, height)
local circle = display.newCircle(snapshot.group, 0, 0, 10)
magnet:center(circle, 0, 0, snapshot) --add the parent
```


