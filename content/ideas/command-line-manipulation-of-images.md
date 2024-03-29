<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----




* [How to Convert Images Using Linux](https://www.lifewire.com/convert-linux-command-unix-command-4097060)
* [Edit images with Jupyter and Python](https://opensource.com/article/20/8/edit-images-python)



# Image Minipulation / Photo Editor

## Darktable
[darktable](https://www.darktable.org/)
is an open source photography lighttable and darkroom for photographers.
It manages your digital negatives in a database,
lets you view them through a zoomable lighttable,
and enables you to develop raw images and enhance them.

* [How to use Darktable as a digital darkroom](https://opensource.com/life/16/4/how-use-darktable-digital-darkroom)
* [Open source photo processing with Darktable](https://opensource.com/article/21/12/open-source-photo-processing-darktable)

## Krita
[Krita](https://krita.org/en/)
is best known as a digital painting application.

* [5 surprising reasons I use Krita for photo editing on Linux](https://opensource.com/article/21/12/open-source-photo-editing-krita)

## Gwenview
* [Crop and resize photos on Linux with Gwenview](https://opensource.com/article/22/2/crop-resize-photos-gwenview-kde)
* [Install gwenview on Ubuntu](https://snapcraft.io/install/gwenview/ubuntu)



-----



# Image Conversion

## Display Characteristics
Sometime you need to know the dimensions or pixel resolution
of the monitor you are using.
There happens to be a [website that can help][04]:
[display size][01],
[screen resolution][02],
[dots per square inch][03].
Also, you could use the [xrandr][05] configuration utility.
It can be used to set the size, orientation or reflection of the outputs for a screen,
but also give you your displays chartereistics.
See this example:

```bash
$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0
   1680x1050      59.9
   1280x1024      75.0     60.0
   1152x864       75.0
   1024x768       75.1     60.0
   800x600        75.0     60.3
   640x480        75.0     60.0
   720x400        70.1
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

## Image File Characteristics
For some image formats you can just use the [`file`][06]
or `convert` and `identify` from ImageMagick command:

```bash
$ file Pictures/Wallpaper/ZZ-Top.png
Pictures/Wallpaper/ZZ-Top.png: PNG image data, 2560 x 1600, 8-bit/color RGB, non-interlaced
```

Not all image formats report the size (JPEG most notably doesn't):

```bash
$ file Pictures/Wallpaper/White-Earth-Limb.jpg
Pictures/Wallpaper/White Earth Limb.jpg: JPEG image data, JFIF standard 1.02
```

For those you will have to use something like `convert`:

```bash
$ convert Pictures/Wallpaper/White-Earth-Limb.jpg -print "Size: %wx%h\n" /dev/null
Size: 1500x1487
```
$ convert MyJpeg.jpg -print "Size: %wx%h\n" /dev/null
Size: 380x380

## Converting Image File Format
```bash
# convert image from JPG to PNG format
convert jeffskinnerbox-300x300.jpeg jeffskinnerbox-300x300.png
```

## Image Optimization
* [My favorite Linux commands for optimizing web images](https://opensource.com/article/21/12/optimize-web-images-linux)
* [Drop PNG and JPG for your online images: Use WebP](https://opensource.com/article/20/4/webp-image-compression)

## Resize Image File
```bash
# resize image to a 128 by 128 pexal picture
convert jeffskinnerbox-300x300.png -resize 128x128 jeffskinnerbox-128x128.png
```

## Changing The Size of an Image
* [HOWTO: Command line manipulation of images](http://discourse.criticalengineering.org/t/howto-command-line-manipulation-of-images/47)
* [ImageMagick Command-Line Tools](http://www.imagemagick.org/script/command-line-tools.php)

# How to Remove Image Background
* [turn on gimp toolbox and layer menu](https://www.youtube.com/watch?v=k6qXqUq7lOc)
* [How to Remove Image Background - 2021 GIMP Tutorial](https://www.youtube.com/watch?v=pZuPbRIBwrE&t=34s)

gimp




[01]:http://www.infobyip.com/detectdisplaysize.php
[02]:http://www.infobyip.com/detectscreenresolution.php
[03]:http://www.infobyip.com/detectmonitordpi.php
[04]:http://www.infobyip.com/
[05]:http://pkg-xorg.alioth.debian.org/howto/use-xrandr.html
[06]:http://www.computerhope.com/unix/ufile.htm
[07]:
[08]:
[09]:
[10]:
