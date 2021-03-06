sxiv
====

**Simple X Image Viewer**

sxiv is an alternative to feh and qiv. Its only dependencies besides xlib are
imlib2 and giflib. The primary goal for writing sxiv is to create an image
viewer, which only has the most basic features required for fast image viewing
(the ones I want). It has vi key bindings and works nicely with tiling window
managers.  Its code base should be kept small and clean to make it easy for you
to dig into it and customize it for your needs.


Features
--------

* Basic image operations, e.g. zooming, panning, rotating
* Customizable key and mouse button mappings (in *config.h*)
* Thumbnail mode: grid of selectable previews of all images
* Ability to cache thumbnails for fast re-loading
* Basic support for multi-frame images
* Load all frames from GIF files and play GIF animations
* Display image information in status bar


Screenshots
-----------

**Image mode:**

![Image](http://muennich.github.com/sxiv/img/image.png "Image mode")

**Thumbnail mode:**

![Thumb](http://muennich.github.com/sxiv/img/thumb.png "Thumb mode")


Installation
------------

sxiv is built using the commands:

    $ make
    # make install

Please note, that the latter one requires root privileges.
By default, sxiv is installed using the prefix "/usr/local", so the full path
of the executable will be "/usr/local/bin/sxiv".

You can install sxiv into a directory of your choice by changing the second
command to:

    # make PREFIX="/your/dir" install

The build-time specific settings of sxiv can be found in the file *config.h*.
Please check and change them, so that they fit your needs.
If the file *config.h* does not already exist, then you have to create it with
the following command:

    $ make config.h


Usage
-----

sxiv has two modes of operation: image and thumbnail mode. The default is
image mode, in which only the current image is shown. In thumbnail mode a grid
of small previews is displayed, making it easy to choose an image to open.

**Command line options:**

    -b           Do not show info bar on bottom of window
    -c           Remove all orphaned cache files from thumbnail cache and exit
    -d           Scale all images to 100%, but fit large images into window
    -F           Use size-hints to make the window fixed/floating
    -f           Start in fullscreen mode
    -g GEOMETRY  Set window position and size
                 (see section GEOMETRY SPECIFICATIONS of X(7))
    -i           Read file list from stdin
    -n NUM       Start at picture NUM
    -N NAME      Set X window resource name to NAME
    -o           Write list of marked files to stdout when quitting
    -q           Be quiet, disable warnings
    -r           Search given directories recursively for images
    -s           Scale all images to fit into window
    -t           Start in thumbnail mode
    -v           Print version information and exit
    -Z           Same as `-z 100'
    -z ZOOM      Scale all images to current zoom level, use ZOOM at startup

**Key mappings:**

    q            Quit sxiv
    Return       Switch to thumbnail mode / open selected image

    0-9          Prefix the next command with a number (denoted via [count])

    g            Go to first image
    G            Go to the last image, or image number [count]

    f            Toggle fullscreen mode (requires an EWMH/NetWM compliant
                 window manager)
    b            Toggle visibility of info bar on bottom of window
    A            Toggle visibility of alpha-channel, i.e. transparency

    r            Reload image
    R            Reload all thumbnails
    D            Remove image from file list and go to next image

    m            Mark/unmark current image
    N            Go [count] marked images forward
    P            Go [count] marked images backward

*Thumbnail mode:*

    h,j,k,l      Move selection left/down/up/right [count] times
    Ctrl-j,k     Scroll thumbnail grid one window height down/up

*Image mode:*

    n,Space      Go [count] images forward
    p,Backspace  Go [count] images backward
    [,]          Go [count] * 10 images backward/forward

    Ctrl-n,p     Go to the next/previous frame of a multi-frame image
    Ctrl-Space   Play/pause animation of a multi-frame image

    +            Zoom in
    -            Zoom out
    =            Set zoom level to 100%, or [count]%
    w            Fit image into window
    e            Fit image width to window width
    E            Fit image height to window height

    h,j,k,l      Pan image 1/5 of window width/height or [count] pixels
                 left/down/up/right (also with arrow keys)
    H,J,K,L      Pan to left/bottom/top/right image edge
    Ctrl-h,j,k,l Pan image one window width/height left/down/up/right
                 (also with Ctrl-arrow keys)

    <,>          Rotate image (counter-)clockwise by 90 degrees
    ?            Rotate image by 180 degrees
    |,_          Flip image horizontally/vertically

    a            Toggle anti-aliasing
    W            Resize window to fit image

**Mouse button mappings:**

*Image mode:*

    Button1      Go to the next image
    Button2      Drag image with mouse while keeping it pressed
    Button3      Go to the previous image
    Scroll       Pan image up/down
    Shift+Scroll Pan image left/right
    Ctrl+Scroll  Zoom in/out


Download & Changelog
--------------------

You can [browse](https://github.com/muennich/sxiv) the source code repository
on GitHub or get a copy using git with the following command:

    git clone https://github.com/muennich/sxiv.git

**Stable releases**

**[v1.1.1](https://github.com/muennich/sxiv/archive/v1.1.1.tar.gz)**
*(June 2, 2013)*

  * Various bug fixes

**[v1.1](https://github.com/muennich/sxiv/archive/v1.1.tar.gz)**
*(March 30, 2013)*

  * Added status bar on bottom of window with customizable content
  * New keyboard shortcuts `\`/`|`: flip image vertically/horizontally
  * New keyboard shortcut `Ctrl-6`: go to last/alternate image
  * Added own EXIF orientation handling, removed dependency on libexif
  * Fixed various bugs

**[v1.0](https://github.com/muennich/sxiv/archive/v1.0.tar.gz)**
*(October 31, 2011)*

  * Support for multi-frame images & GIF animations
  * POSIX compliant (IEEE Std 1003.1-2001)

**[v0.9](https://github.com/muennich/sxiv/archive/v0.9.tar.gz)**
*(August 17, 2011)*

  * Made key and mouse mappings fully configurable in config.h
  * Complete code refactoring

**[v0.8.2](https://github.com/muennich/sxiv/archive/v0.8.2.tar.gz)**
*(June 29, 2011)*

  * POSIX-compliant Makefile; compiles under NetBSD

**[v0.8.1](https://github.com/muennich/sxiv/archive/v0.8.1.tar.gz)**
*(May 8, 2011)*

  * Fixed fullscreen under window managers, which are not fully EWMH-compliant

**[v0.8](https://github.com/muennich/sxiv/archive/v0.8.tar.gz)**
*(April 18, 2011)*

  * Support for thumbnail caching, only enabled if directory `~/.sxiv/` exists
  * Ability to run external commands (e.g. jpegtran, convert) on current image

**[v0.7](https://github.com/muennich/sxiv/archive/v0.7.tar.gz)**
*(February 26, 2011)*

  * Sort directory entries when using `-r` command line option
  * Hide cursor in image mode
  * Full functional thumbnail mode, use Return key to switch between image and
    thumbnail mode

**[v0.6](https://github.com/muennich/sxiv/archive/v0.6.tar.gz)**
*(February 16, 2011)*

  * Bug fix: Correctly display filenames with umlauts in window title
  * Basic support of thumbnails

**[v0.5](https://github.com/muennich/sxiv/archive/v0.5.tar.gz)**
*(February 6, 2011)*

  * New command line option: `-r`: open all images in given directories
  * New key shortcuts: `w`: resize image to fit into window; `W`: resize window
    to fit to image

**[v0.4](https://github.com/muennich/sxiv/archive/v0.4.tar.gz)**
*(February 1, 2011)*

  * New command line option: `-F`, `-g`: use fixed window dimensions and apply
    a given window geometry
  * New key shortcut: `r`: reload current image

**[v0.3.1](https://github.com/muennich/sxiv/archive/v0.3.1.tar.gz)**
*(January 30, 2011)*

  * Bug fix: Do not set setuid bit on executable when using `make install`
  * Pan image with mouse while pressing middle mouse button

**[v0.3](https://github.com/muennich/sxiv/archive/v0.3.tar.gz)**
*(January 29, 2011)*

  * New command line options: `-d`, `-f`, `-p`, `-s`, `-v`, `-w`, `-Z`, `-z`
  * More mouse mappings: Go to next/previous image with left/right click,
    scroll image with mouse wheel (horizontally if Shift key is pressed),
    zoom image with mouse wheel if Ctrl key is pressed

**[v0.2](https://github.com/muennich/sxiv/archive/v0.2.tar.gz)**
*(January 23, 2011)*

  * Bug fix: Handle window resizes correctly
  * New keyboard shortcuts: `g`/`G`: go to first/last image; `[`/`]`: go 10
    images back/forward
  * Support for mouse wheel zooming (by Dave Reisner)
  * Added fullscreen mode

**[v0.1](https://github.com/muennich/sxiv/archive/v0.1.tar.gz)**
*(January 21, 2011)*

  * Initial release

