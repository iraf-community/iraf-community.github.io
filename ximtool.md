# Welcome to XImtool V2.0BETA

XImtool is an image display server developed by the IRAF Project at the
National Optical Astronomy Observatories. To view images you need client
software (such as IRAF) to load images into the display, or it can load
images directly when run as a standalone task.

More [detailed help](#toc) is available on the following topics:

Basic Usage:

-   [Getting Started](#getting-started) \-- The basics.
-   [GUI Overview](#gui-overview) \-- What it looks like.
-   [Mouse Operations](#mouse-operations) \-- Doing stuff.
-   [Keystroke Accelerators](#keystroke-accelerators) \-- Keystroke summary.
-   [Markers](#markers) \-- Panner/WCS markers, general markers.
-   [Control Panel](#control) \-- Operating the Control panel.
-   [Load Panel](#load) \-- Load panel operation and options.
-   [Save Panel](#save) \-- Save panel operation and options.
-   [Print Panel](#print) \-- Print panel operation and options.
-   [Info Panel](#info) \-- Information panel.

Advanced Features:

-   [Command-line Options](#comline) \-- Startup flags.
-   [Client Connections](#client-connections) \-- Use as a display server.
-   [Frame Buffers](#frame-buffers) \-- Explanation of Frame buffers.
-   [Printer Configurations](#pprinter) \-- Configuring output devices.
-   [TclShell](#tclshell) \-- Expert-mode interactive shell.

Please contact *iraf\@noao.edu* with comments, bugs, or suggestions.
More detailed documentation is also available in the man page for this
task.


## Getting Started

As a display server, XImtool is started as a separate process from
client software such as IRAF. Once it is running it will accept
[client connections](#client-connections) simultaneously on fifo
pipes, unix domain sockets, or inet sockets. A display client like the
IRAF DISPLAY task makes a connection and sends the image across using
an IIS protocol (other/different protocols may be supported in the
future). Once the image is loaded in the display buffer it may be
[enhanced](#cenhance), [saved to a disk file](#save) in a number of
different formats, or [printed](#print) as Encapsulated Postscript to
a printer or disk file.

When run in standalone mode, images may be loaded on the [command
line](#comline) or by using the [Load Panel](#load). This allows you to
browse images and perform the same manipulations as if they had been
displayed by a client.


## GUI Overview

The GUI consists of a large image display window and a number of smaller
panels that control various specific functions such as image
[Load](#load), [Save](#save) and [Print](#print) as well as a general
purpose [Control Panel](#control). The main window menubar has several
menu buttons to the left: the *Files* menu is used to load/save/print an
image as well as quit the task. The *View* menu lets you select the
image orientation, zoom, colormap or frame. The *Options* menu allows
you to call up control panels, toggle markers or blinking etc. Some of
this functionality is duplicated elsewhere in the GUI. The right side of
the menubar contains command buttons to flip the image as well as
buttons for frame selection and the help button.

For more detailed information on the operation of the control panels
please see the on-line help (i.e. use the \'?\' button or Alt-h
keystroke in the main image window).


## Mouse Operations

Clicking and dragging MB1 (mouse button 1) in the main image window
creates a rectangular region [marker](#markers), used to select a region
of the image. If you do this accidentally and don\'t want the marker,
put the pointer in the marker and type DELETE or BACKSPACE to delete the
marker. With the pointer in the marker, MB3 will call up a [marker
menu](#markmenu) listing some things you can do with the marker, like
zoom the outlined region. MB1 can be used to drag or resize the marker.
[See below](#markers) for more information on markers.

Clicking on MB2 in the main image window pans (one click) or zooms (two
clicks) the image. Further clicks cycle through the builtin zoom
factors. Moving the pointer to a new location and clicking moves the
feature under the pointer to the center of the display window. Holding
down the Shift key while clicking MB2 will cause a full-screen crosshair
cursor to appear until the button is released, this can be useful for
fine positioning of the cursor.

MB3 is used to adjust the contrast and brightness of the displayed
image. The position of the pointer within the display window determines
the contrast and brightness values. Click once to set the values
corresponding to the pointer location, or click and drag to continuously
adjust the display.


## Keystroke Accelerators

The following keystrokes are currently defined in the GUI:

### Misc Functions

 * **Ctrl-b**: Previous (back) frame
 * **Ctrl-c**: Center frame
 * **Ctrl-f**: Forward frame
 * **Ctrl-i**: Invert colormap
 * **Ctrl-m**: Toggle magnifier
 * **Ctrl-n**: Normalize
 * **Ctrl-p**: Toggle panner
 * **Ctrl-r**: Register
 * **Ctrl-s**: Match LUT scaling
 * **Ctrl-t**: Tile frames toggle
 * **Ctrl-u**: Unzoom (zoom=1)
 * **Ctrl-x**: Flip X
 * **Ctrl-y**: Flip Y
        
 * **Ctrl-=**: Print using current setup
 * **Ctrl-<**: Decrease blink rate (blink faster)
 * **Ctrl->**: Increase blink rate (blink slower)
 * **Ctrl-+**: Zoom in
 * **Ctrl--**: Zoom out
        
 * **Alt-1** thru **Alt-4**: Set frame to be displayed
 * **Ctrl-1** thru **Ctrl9**: Set integer zoom factor
        
 * **Ctrl-Alt-q**: Quit
 * **Ctrl-Alt-f**: Fitframe
        
### Panel Toggles

 * **Alt-b**: Blink frames
 * **Alt-c**: Control panel
 * **Alt-h**: Help popup
 * **Alt-i**: Info box popup
 * **Alt-l**: Load file popup
 * **Alt-p**: Print popup
 * **Alt-s**: Save popup
 * **Alt-t**: TclShell popup
        
### Cursor Positioning

 * **Ctrl-h** / **Ctrl-Left**:  Move cursor one pixel left
 * **Ctrl-j** / **Ctrl-Down**:  Move cursor one pixel down
 * **Ctrl-k** / **Ctrl-Up**:    Move cursor one pixel up
 * **Ctrl-l** / **Ctrl-Right**: Move cursor one pixel right
        
 * **Shift-Ctrl-h**:    Move cursor ten pixels left
 * **Shift-Ctrl-Left**: Move cursor ten pixels left
 * **Shift-Ctrl-j**:    Move cursor ten pixels down
 * **Shift-Ctrl-Down**: Move cursor ten pixels down
 * **Shift-Ctrl-k**:    Move cursor ten pixels up
 * **Shift-Ctrl-Up**:   Move cursor ten pixels up
 * **Shift-Ctrl-l**:    Move cursor ten pixels right
 * **Shift-Ctrl-Right**: Move cursor ten pixels right

### Auto-Registration

 * **Ctrl-a**: Toggle auto-registration
 * **Ctrl-o**: Set frame offset

### Frame Positioning

 * **Ctrl-Left**:  Shift one full frame left
 * **Ctrl-Down**:  Shift one full frame down
 * **Ctrl-Up**:    Shift one full frame up
 * **Ctrl-Right**: Shift one full frame right

 * **Ctrl-Alt-Left**:  Shift one half frame left
 * **Ctrl-Alt-Down**:  Shift one half frame down
 * **Ctrl-Alt-Up**:    Shift one half frame up
 * **Ctrl-Alt-Right**: Shift one half frame right
        
                            Peak Up Centroiding                  
 * **Ctrl-[       Decrease centroiding box size
 * **Ctrl-]       Increase centroiding box size
 * **Ctrl-0 (zero)    Centroid/find local maximum
 * **Alt-Ctrl-0 (zero)   Find local minimum
        
                            Mouse Button Events                   
 * **Shift-Btn1Down   Turn on magnifier
 * **Shift-Btn1Up     Turn off magnifier
 * **Shift-Btn2Down   Turn on crosshair cursor
 * **Shift-Btn2Up     Turn off crosshair cursor
        
 * **Btn1Down         Create a Marker
 * **Btn1Motion       Resize marker being created
 * **Btn2Down         Zoom/center on cursor position
 * **Btn3Down/Motion     Brightness/contrast scale the image
        
 * **Ctrl-Btn1Down    Create Ruler Marker
 * **Ctrl-Btn1Motion     Resize Ruler Marker being created
 * **Ctrl-Btn1Up  Destroy Ruler Marker
        
 * **Alt-Motion       Freeze cursor readout



## Client Connections

Ximtool allows clients to connect in any of the following ways:

 * **fifo pipes**: The traditional approach. The default, global
    `/dev/imt1[io]` pipes may be used, or a private set of fifos.

 * **tcp/ip socket**: Clients connect via a tcp/ip socket. There is a
    default port, or a custom port may be specified. This permits
    connecting to the server over a remote network connection anywhere
    on the Internet.

 * **unix domain socket**: Like a tcp/ip socket, but limited to a
    single host system. Usually faster than a tcp/ip socket, and
    comparable to a fifo. By default each user gets their own unix
    domain socket, so this option allows multiple users to run
    ximtools on the same host without having to customize things.

By default ximtool listens simultaneously for client connctions on all
three types of ports. Clients communicate with XImtool using the IIS
protocol, other protocols may be supported in the future.


## Frame Buffers

XImtool starts up using default frame buffer size of 512x512 pixels, two
(of 16 possible) frames will be created. When loading disk images (i.e.
run in standalone mode) the frame buffer configuration file will be
searched for a defined frame buffer that is the same size or larger than
the current image, if no suitable buffer can be found a custom frame
buffer the same size as the image will be created in an unused portion
of the configuration table. When used as a display server the frame
buffer configuration number is passed in by the client and loaded
explicitly even if it means clipping the image. If a new frame buffer is
a different size than previously defined frames, all available frames
will be initialized and cleared prior to the display. The default frame
buffer configuration file is `/usr/local/lib/imtoolrc`, this can be
overridden by defining a `IMTOOLRC` environment variable naming the
file to be used, by creating a `.imtoolrc` file in your home
directory, or a new file may be specified using the `-imtoolrc`
command line flag or `imtoolrc` application resource.

The format of the frame buffer configuration file is

       configno nframes width height [extra fields]

e.g.

        1  2  512  512
        2  2  800  800
        3  1 1024 1024          # comment

At most 128 frame buffer sizes may be defined, each configuration may
define up to 16 frames, configuration numbers need not be sequential.

### Support for 16 Display Frames

As part of the extensive GUI changes with the V1.3 release, support for
the full 16 frames allowed by the IIS protocol is now available. IRAF
V2.11.4 or later client tasks (and CDL library) are required to take
advantage of this frames. All changes are backwards compatible, older
versions of IRAF will continue to work but cannot access more than the
original four frames. The new DISPLAY task will automatically sense
whether the display server being used supports 16 frames or the original
4 and adjust the `frame` parameter maximum accordingly. The changes
are fully backwards compatible for other servers.

More frames are possible if needed but will require further changes to
the client IRAF code to be effective. Allowing creation of more than 16
frames by the Load panel can be done independently but would also
require numerous code change to XImtool. Please contact site support if
there is a need for this, or for workaround suggestions depending on
your application.

[Command-line Options]{##comline}
---------------------------------

The following command-line options are currently recognized:

      -basePixel <num>         Base colormap pixel number
      -cmap1 <file>            User cmap 1 
      -cmap2 <file>            User cmap 2 
      -cmapDir1 <dir>          User cmapDir 1 
      -cmapDir1 <dir>          User cmapDir 2 
      -cmapInitialize <bool>   Initialize colormap at startup
      -cmapName <name>         Private colormap name 
      -config <num>            Initial config number
      -defgui                  Print default GUI to stdout
      -displayPanner <bool>    Display panner box
      -displayCoords <bool>    Display wcs coords box
      -fifo <pipe>             Fifo pipe to use
      -fifo_only               Use fifo pipes only 
      -gui <file>              GUI file to use 
      -help                    Print command-line summary 
      -imtoolrc <file>         Frame buffer configuration file 
      -inet_only               Use inet sockets only 
      -invert                  Invert colormap on startup?
      -ismdev                  ISM socket template
      -maxColors <num>         Number of colors 
      -memModel <type>         Memory model (fast,small,beNiceToServer)
      -nframes <num>           Number of frames at startup
      -port <num>              Inet port to use
      -printConfig <file>      Printer configuration file 
      -port_only               Use inet sockets only 
      -tile                    Tile frames on startup?
      -unix <name>             Unix socket to use
      -unix_only               Use unix sockets only 
      <file>                   File to load on startup

------------------------------------------------------------------------

[Markers]{##markers}
--------------------

### [Panner Marker]{##panner}

The panner window always displays the full frame buffer. Try setting the
frame buffer configuration to a nonsquare frame buffer (e.g. imtcryo)
and then displaying a square image (e.g. `dev$pix`) and the panner will
show you exactly where the image has been loaded into the frame.

The panner window uses two markers, one for the window border and one to
mark the displayed region of the frame. Most of the usual marker
keystrokes mentioned [below](#genmark) apply to these markers as well,
e.g. you can use MB1 to reposition on the panner window within the main
image display window, or to drag the region marker within the panner
(pan the image). Resizing the region marker zooms the image; this is a
non-aspect constrained zoom. The panner window itself can be resized by
dragging a corner with MB1. Typing delete or backspace anywhere in the
panner window deletes the panner.

A special case is MB2. Hitting MB2 anywhere in the panner window pans
the image to that point. This is analogous to typing MB2 in the main
display window to pan the image.

The panner marker can be disabled by defining the `displayPanner` GUI
resource, its size and location can be controlled using the `pannerArea`
and `pannerGeom` GUI resources respectively.

### [Magnifier Marker]{##magnifier}

The magnifier marker can be used to zoom in on a small area around the
cursor. It will be updated as the cursor moves but only for small
motions (either mouse movement or with the cursor movement keystrokes)
to minimize the impact on the system. The zoom factor is expressed as
some fraction of the size of the magnifier marker itself. The default
zoom is 4, i.e. the area in the marker represents and area in the image
that's one-fourth the size of the marker. Other zoom factors may be
selected using the popup menu created by hitting MB1 in the marker.

By default the magnifier marker is not visible, to toggle it select the
*Magnifier* option from the *Options* menubar button. Alternatively, for
just a quick look holding down the Shift Key and MB2 Button will display
the marker until the button is released.

The magnifier marker can be disabled by defining the *displayMagnifier*
GUI resource, its size and location can be controlled using the
*magnifierArea*and *magnifierGeom* GUI resources respectively.

### [Coords Box Marker]{##coords}

Ximtool provides a limited notion of world coordinates, allowing frame
buffer pixel coordinates and pixel values to be converted to some
arbitrary client defined coordinate system. The coords box feature is
used to display these world coordinates as the pointer is moved about in
the image window.

The quantities displayed in the coords box are X, Y, and Z: the X,Y
world coordinates of the pointer, and Z, the world equivalent of the
pixel value under the pointer. All coordinate systems are linear. The
precision of a displayed quantity is limited by the range of values of
the associated raw frame buffer value. For example, if the display
window is 512x512 only 512 coordinate values are possible in either axis
(the positional precision can be increased however by zooming the
image). More seriously, at most about 200 pixel values can be displayed
since this is the limit on the range of pixel values loaded into the
frame buffer. If a display pixel is saturated a \"+\" will be displayed
after the intensity value.

The coords box is a marker (text marker) and it can be moved and resized
with the pointer like any other marker.

### [Ruler Markers]{##rulers}

Holding down the Ctrl key and the Left-Mouse-Button while moving the
mouse will drag out a \"ruler marker\" measuring the distance from the
initial point to the current mouse position. Releasing the Ctrl key
before lifting the mouse button will leave the marker on the display,
otherwise it will be erased automatically once the mouse button is
released. Any number of ruler markers can be created in the frame.

Distances are measured by default in image logical pixels however the
Right-Mouse-Button can be used inside the marker to popup a menu of
options:

**Sticky**
:   By default rulers are destroyed whenever the display changes due to
    a pan, zoom, flip, or frame change. This option will make the ruler
    \"sticky\" so it will not be erased, subsequent use of the menu to
    shows this option to be \"UnSticky\" to remove this feature.

**Units**
:   Sub-menu to select the units of the display. If the ISM is enabled
    and a WCS is present in the image and selected as one of the readout
    options, distances may also be read out in units of arcseconds,
    arcminutes, or degrees instead of the default logical pixels. All
    markers created after the unit change will readout in the new units
    as their default.

**Color**
:   Select the color of the marker.

**Draw into Frame**
:   (*Not Yet Implemented*) Draw the marker as overlay graphics in the
    frame. Doing so will retain the marker when printing a hardcopy of
    the display.

**Destroy**
:   Destroy the marker.

The marker can also be destroyed by hitting the Delete or Backspace key
while the cursor is in the marker. There is presently no way to move the
marker to a new position in the frame.

### [General Markers]{##genmark}

Although ximtool doesn\'t do much with markers currently, they are a
general feature of the Gterm widget and are used more extensively in
other programs (e.g. the prototype IRAF science GUI applications).
Ximtool uses markers for the marker zoom feature discussed above, and
also for the [panner](#panner) and the [coords box](#coords). All
markers share some of the same characteristics, so it is worthwhile
learning basic marker manipulation keystrokes.

-   MB1 anywhere inside a marker may be used to drag the marker.
-   MB1 near a marker corner or edge, depending on the type of marker,
    resizes the marker.
-   Shift-MB1 on the corner of most markers will rotate the marker.
-   Markers stack, if you have several markers and you put one on top of
    the other. The active marker is highlighted to tell you which of the
    stacked markers is active. If the markers overlap, this will be
    marker \"on top\" in the stacking order.
-   MB2 in the body of a marker \"lowers\" the marker, i.e. moves it to
    the bottom of the stacking order.
-   Delete or backspace in a marker deletes it.
-   Markers have their own translation resources and so the default
    [keystroke commands](#keystroke-accelerators) will not be recognized when the
    cursor is in a marker.

For example, try placing the pointer anywhere in the coords box, then
press MB1 and hold it down, and drag the coords box marker somewhere
else on the screen. You can also resize the coords box by dragging a
corner, or delete it with the delete or backspace key. (The
**Initialize** button will get the original coords box back if you
delete it).

#### [Marker Menu Options]{##markmenu}

-   MB3 (mouse button 3) calls up the marker menu (by default).
-   **Zoom** does an equal aspect zoom of the region outlined by the
    marker. In this way you can mark a region of the image and zoom it
    up.
-   **Fill** exactly zooms the area outlined by the marker, making it
    fill the display window. Since the marker is not likely to be
    exactly square, the aspect ratio of the resultant image will not be
    unitary.
-   **Print** prints the region outlined by the marker to the printer or
    file currently configured by the [Print Panel](#print).
-   **Save** saves the region outlined by the marker to the file
    currently configured by the [Save Panel](#save).
-   **Info** prints a description of the marked region. The text is
    printed in the [Info Panel](#info).
-   **Unrotate** unrotates a rotated marker.
-   **Color** is a menu of possible marker colors.
-   **Type** is a menu of possible marker types. This is still a little
    buggy and it isn\'t very useful, but you can use it to play with
    different types of markers.
-   **Destroy** destroys the marker. You can also hit the delete or
    backspace key in a marker to destroy the marker.

------------------------------------------------------------------------

[Real-Time WCS/Pixel Readout]{##wcspix}
---------------------------------------

XImtool now has the ability to display the actual pixel value of an
image (as well as the scaled value previously shown) and the cursor
position in image WCS values (e.g. RA/DEC, GLAT/GLONG, etc). This is
done using an external task (the \'ism\_wcspix.e\' binary in the new
distribution) to access the image and pass the coordinate/pixel
information to the GUI.

WCS readout is enabled by default but can be toggled or reset using the
*WCS/Pix* button on the Coords tab in the control panel or the *ISM*
toggle on the alt-gui menubar. When enabled, images currently in the
server or subsequently displayed will be passed to the external process
where they are cached for access. Cursor movements generate an event
that maps the current frame buffer position to a position in the cached
image. The ISM (ISM is Image Support Module) task then reads the image
to determine the pixel value (or a small table of values around the
current position), and computes one or more coordinates from the image
position. The ISM task also has access to the associated BPM images and
can optionally return bad pixel information during the cursor readout.

By default, the logical and world image coordinates are displayed to
both the Coords panel readout as well as the main display window wcsbox
text marker. Alternate coordinate systems (e.g. transformation of
equatorial to galactic coordinates or some other sky system, physical
coords, amplifier coords, etc) can be selected for display by hitting
the *Options* toggle on the Coords panel. Available coordinate systems
are chosen using the *Type* menu on the panel, the readout format
(sexigesimal, degrees, etc) using the *Format* menu, and the display to
the current panel or main image window using the remaining toggles for
each WCS. Up to four systems may be displayed at one time, the
coordinate panel and wcsbox marker will adjust size automatically
depending on the display.

By selecting the *BPM Data* toggle from the Coords.Options panel ximtool
is able to flag pixels in images with an associated bad pixel mask. This
bad pixel mask is currently assumed to be named in the image header
\"BPM\" keyword by convention. If the cursor passes over a bad pixel in
the mask, the Coords bpm display as well as the main window wcsbox will
change to a red background color. Only the Coords display will show the
value, any non-zero value will be flagged with the color change.

With the ISM enabled the Compass indicator will display a set of arrows
showing North-East if a WCS is available, otherwise just the current X-Y
axes are shown. The pixel table will display actual pixel values from
the image, with the ISM off the pixel table displays the scaled image
values from the frame buffer.

------------------------------------------------------------------------

[Freezing Cursor Readout]{##curfreeze}
--------------------------------------

Holding down the Alt key will now freeze the cursor display readout and
draw crosshairs on the screen at the last position. This can be used for
example to position the cursor but then allow the cursor to be moved to
another window (to enter text, start a program, whatever) without losing
the position information displayed on the screen.

------------------------------------------------------------------------

[Auto-Registration of Images]{##autoreg}
----------------------------------------

The auto-register feature allows you specify a registration of two or
more display frames with an offset. When enabled, this registration is
maintained for all frames in the list if any one of them is panned or
zoomed to a new location in the frame buffer.

For example, to use this feature do the following:

-   Enable Auto-Register (either on the Control Panel or the toolbar on
    the alt-gui) and pan/zoom to some star of interest.
-   Use Mouse-Button-2 to center the star in the frame.
-   Cycle through the frames and you may see a small shift of the star.
    For each frame, position the cursor on the star and type **Ctrl-o**
    to offset it to the center. Repeat as necessary. Small corrections
    will be cumulatively added so you can use the **Ctrl-0** (Ctrl-zero)
    peak-up command to centroid each object in the frame before the
    **Ctrl-o** offset.
-   Pan around the image in one display frame, then switch frames and
    the new frame should also be panned to the new image with the proper
    offset.
-   A **Ctrl-a** command will toggle the feature, offsets are only
    allowed when autoreg is enabled.

Hitting **Register** will zero the offsets, as will toggling the
auto-register function. What you should see is the object centered in
the frame and as you blink through it remains registered but the panner
box marker is moving around. Drag the panner around and all frames still
remain registered with the given offset. The control/info panels now
display what the offset is for each frame.

The register display list is shared with the blink list and can be set
using the Display control panel. By default all frames are included in
the list. For accessing more than four frames, use the box icon in the
Blink/Register box of the Display control panel to bring up a new window
with access to all 16 available frames.

------------------------------------------------------------------------

[Image Cut Graphics]{##cutgraphs}
---------------------------------

XImtool now has the ability to display horizontal and vertical
cut-graphs of the display, these appear as \"flip-out\" panels that
appear on the bottom and right side of the main display window and are
controlled by the small **H** and **V** buttons in the lower right
corner of the window. When both panels are enabled the corner area of
the display also shows an options panel for the graphs. Current options
are:

**Better Speed**
:   Draw the graphics so they update at the fastest possible rate. This
    is done by subsampling pixels to produce a smoother graph but
    without sacrificing too much accuracy.

**Better Accuracy**
:   Draw the graphics using all screen pixels to produce the most
    accurate display. On fast modern machines this can be enabled with
    no apparent loss of speed, however older machines may wish to use
    this only occasionally to limit any lag in the cursor tracking.

**Image Pixels**
:   (*Not Yet Implemented*)
:   

**Jump Cursor**
:   If enabled, large jumps of the cursor do not update the graphics
    display, small movements around an object of interest will update
    the display continuously.

**Smooth Cursor**
:   If enabled, all cursor movements cause the display to be updated.
    This is another option that can be set safely on faster machines but
    will cause a delay on slower ones.

**Graphics Cursors**
:   If enabled, the graphics cursors in either of the plots are active
    and can be used to update the cursor readout on the main image
    window and the complementary cut-graph. This can be used for example
    to freeze the cursor in the main display using the Alt key (see
    above), then moving to one of the graphics windows to perform cut
    graphs in only one axis.

Graphs are (currently) drawn using only the scaled display values to
avoid complications of accessing multiple images in a mosaic display.
Both plots are labeled using the frame z1/z2 values and contain cursor
indicators which update contuously.

------------------------------------------------------------------------

[Peak-Up Cursor Centroid Positioning]{##peakup}
-----------------------------------------------

Several new keystroke commands are available to reposition the cursor to
a centroid or min/max pixel value within a bounding box of the cursor
position, allowing you to approximate the position with the mouse and
fine tune it quickly before typing the application keystroke command.
The initial box size is controlled with a **centerBoxSize** GUI resource
(defaults to 5 pixels) but can be adjusted interactively using the
**Ctrl-\[** and **Ctrl-\]** commands to descrease/increase the box size
respectively. A marker will flash briefly to indicate the box size.

The **Ctrl-0** (zero) key finds either a centroid or the local maximum
pixel value within this box region, **Alt-Ctrl-0 (zero) will find the
local minimum value. In either case the cursor is reposition to the
computed value. The default peak-up action is to find the centroid
position in the box however this can be changed to find the max pixel by
selection the \"[Centroid Peaks](#ccentroid)\" option from the main
Display control panel or by resetting the *peakCentroid* GUI resource
(defaults to True).**

Centroiding is done using only the scaled screen pixel values and only
pixels above the mean value within the box are used. It works best if
the box size is set appropriately, the centroid position may appear to
drift if the box is too large and includes too many background pixels.

------------------------------------------------------------------------

[Integrated Control Panel]{##control}
-------------------------------------

### [Display Panel]{##display}

XImtool has a control panel which can be used to exercise most of the
capabilities the program has for image display. The control panel can be
accessed either via the **Options** menu from the main window menubar,
or by pressing the leftmost button in the row of buttons at the upper
right side of the display in the standard GUI (in the alternate GUI the
*Control Bar* accessed by the rightmost button on the menubar provides
widgets for selecting the desired control panel).

The separate windows previously used for Control/Print/Load/Save/etc
have now been integrated into a single window with the appropriate
control panel selectable with a Tab widget. There are also new Tab
panels for setting the frame tile configuration (see below), more
detailed information on the server status, and selecting the WCS readout
options (see below).

### [View Controls]{##cview}

The **Frame** box will list only the frame buffers you currently have
defined. Currently, the only way to destroy a frame buffer is to change
the frame buffer configuration, new frame buffers (up to 4) will be
created automatically if requested by the client.

The **text display window** gives the field X,Y center, X,Y scale
factors, and the X,Y zoom factors. The scale factor and the zoom factor
will be the same unless autoscale is enabled. The scale is in units of
display pixels per frame buffer pixel, and is an absolute measure (it
doesn\'t matter whether or not [autoscale](#cautoscale) is enabled).
Zoom is relative to the autoscale factor, which is 1.0 if autoscaling is
disabled. This information is also presented in the [Info panel](#info).

The numbers in the **Zoom** box are zoom factors. Blue numbers zoom,
red numbers dezoom. **Zoom In** and **Zoom Out** may be used to go to
larger or smaller zoom factors, e.g. \"Ctrl-5\" followed by \"Zoom
In\" will get you to zoom factor 10. Specific zoom factors may also be
accessed directly as Control [keystrokes](#keystroke-accelerators),
e.g. Ctrl-5 will set zoom factor 5. **Center** centers the
field. **Toggle Zoom** toggles between the current zoom/center values,
and the unzoomed image.

**Aspect** recomputes the view so that the aspect ratio is 1.0. Aspect
also integerizes the zoom factor (use the version in the View menu if
you don\'t want integerization).

**Fit Frame** makes the display window the same size as the frame
buffer. Note that [autoscale](#cautoscale) has much the same effect, and
allows you to resize the display window to any size you want, or view
images to large to fit on the screen.

### [Enhancement Controls]{##cenhance}

At the top is a scrolled list of all the [available colormaps](#cbltin).
Click on the one you want to load it. You can add your own
[colormaps](#cuser) to this list.

The two sliders adjust the **contrast** (upper slider) and
**brightness** (lower slider) of the display. The **Invert** button
inverts the colormap (multiples the contrast by -1.0). Note that due to
the use of the private colormap the sliders are a bit sluggish when
dragged to window the display. If this is annoying, using MB3 in the
display window is faster.

The **Normalize** button (on the bottom of the control panel) will
normalize the enhancement, i.e. set the contrast and brightness to the
default one-to-one values (1.0, 0.5). This is the preferred setting for
many of the pseudocolor colortables and for private colormaps loaded
from disk images.

### [Blink Controls]{##cblink}

**Blink frames** is the list of frames to be blinked. When blink mode is
in effect ximtool just cycles through these frames endlessly, pausing
\"blink rate\" seconds between each frame. The same frame can be entered
in the list more than once. To program an arbitrary list of blink
frames, hit the Reset button and click on each blink frame button until
it is set to the desired frame number. The main control panel allows
only the original four frames to be specified in the blink list, however
access to the full list of 16 frames now supported is gained using the
box icon button next the the **Reset** button to bring up a new control
panel.

The **Blink Rate** can be adjusted as slow or as fast as you want using
the arrow buttons. If you set the blink rate small enough it will go to
zero, enabling single step mode (see below).

The **Register** button registers all the blink frames with the current
display frame. Frames not in the blink list are not affected.

The **Match LUTs** button sets the enhancement of all blink frames to
the same values as the display frame. Frames not in the blink list are
not affected.

The **Blink** button turns blink on and off. When the blink rate is set
to zero the Blink button will single step through the blink frames, one
frame per button press.

**NOTE:** You can blink no matter what ximtool options are in effect,
but many of these will slow blink down. To get the fastest blink you may
want to turn off the panner and coords box, and match the LUTs of all
the blink frames. All the ximtool controls are fully active during blink
mode, plus you can load frames etc.

### [Options:]{##copts}

**[Panner]{##cpanner}**
:   Toggles the display of the Panner marker.

**[Magnifier]{##cmagnifier}**
:   Toggles the display of the magnifier marker.

**[Coords Box]{##ccoords}**
:   Toggles the display of the WCS Coords Box marker.

**[Autoscale]{##cautoscale}**
:   If autoscale is enabled then at zoom=1, the frame buffer will be
    automatically scaled to fit within the display window. With
    autoscale disabled (the default), the image scale is more
    predictable, but the image may be clipped by the display window, or
    may not fill the display window.

**[Antialias]{##cantialias}**
:   When dezooming an image, i.e., displaying a large image in a smaller
    display window, antialiasing causes all the data to be used to
    compute the displayed image. If antialiasing is disabled then image
    is subsampled to compute the displayed image. Antialiasing can
    prevent subsampling from omitting image features that don\'t fall in
    the sample grid, but it is significantly slower than dezooming via
    subsampling. The default is no antialising.

**[Tile Frames]{##ctile}**
:   The default display mode is to view one frame at a time. In tile
    frames mode, 2 or 4 frames may be viewed simultaneously in the
    display window. All the usual operations (zoom and pan, colortable
    enhancement, cursor readback, etc.) still work for each frame even
    when in tile frames mode.

**[Warnings]{##cwarnings}**
:   The warnings options toggles whether you see warning dialog boxes in
    situations like overwriting an existing file, clearing the frame
    buffer, etc.

**[Centroid Peaks]{##ccentroid}**
:   If enabled, the **Ctrl-0** keystroke will reposition the cursor to
    the computed centroid of the centroiding box, otherwise the cursor
    is repositioned to the local maximum value within the box.

### [Colormap Selection]{##ccmap}

By default XImtool will display images using either a grayscale colormap
if loaded by a client, or a private colormap when loading an image from
disk that contains a colormap. Each frame defines its own colormap so
you can define different colormaps or enhancements for each frame, they
will change automatically as you cycle through the frames.

#### [Builtin Colormaps]{##cbltin}

Once loaded, the colormap may either be changed using the builtin
colormap menu under the **View** menu button on the main window, or from
the [Enhancement](#cenhance) box on the [control panel](#control).
Ximtool has about a dozen colormap options builtin, other [user-defined
colormaps](#cuser) may optionally be loaded.

#### [User-defined Colormaps]{##cuser}

The cmap\[12\] and cmapDir\[12\] resources (or [command line
arguments](#comline) are used to tell ximtool which specific colormaps
to make available or where to look for colortables respectively. The
colortables are loaded when ximtool starts up, or when it is
reinitialized (e.g. by pressing the **Initialize** button in the
[control panel](#control)). Ximtool will ignore any files in the
colormap directory which do not look like colortables. New colortables
will also be added for each images loaded from disk.

The format of a user lookup table is very simple: each row defines one
colortable entry, and consists of three columns defining the red, green,
and blue values scaled to the range 0.0 (off) to 1.0 (full intensity).

            R G B
            R G B
            (etc.)

Blank lines and comment lines (\# \...) are ignored.

Usually 256 rows are provided, but the number may actually be anything
in the range 1 to 256. Ximtool will interpolate the table as necessary
to compute the colortable values used in Ximtool. Ximtool uses at most
201 colors to render pixel data, so it is usually necessary to
interpolate the table when it is loaded.

The name of the colortable as it will appear in the Ximtool control
panel is the root name of the file, e.g., if the file is \"rainbow.lut\"
the colortable name will be \"rainbow\". Lower case names are suggested
to avoid name collisions with the builtin colortables. Private colormaps
for disk images will be have the same name as the image loaded. If the
same colortable file appears in multiple user colortable directories,
the first one will be used.

The directory \"luts\" in the ximtool source directory contains a sample
set of colortable files. This can be installed as
/usr/local/lib/imtoolcmap when ximtool is installed.

------------------------------------------------------------------------

[Load Panel]{##load}
--------------------

The Load Panel allows you load images from disk directly to the frame
buffer, this is analogous to loading an image on the command line except
that browsing is possible. At present recognized formats include IRAF
OIF format (i.e. *.imh* extension), simple FITS files, GIF, and Sun
rasterfiles. The task will automatically sense the format of the image
and load it appropriately. Images with private colormaps (such as GIF)
will be loaded using the private colormap (meaning that changing the
brightness/contrast enhancements will render an apparently
random-colored image), all others will be loaded with a grayscale
colormap.

When loading new images the frame buffer configuration table will be
searched for a frame buffer that is the same size or larger than the new
image size, if no frame buffer can be found a custom buffer exactly the
size of the image will be created. This means that the image may not
fill the display window when loaded, or you may see a subsection of the
image in the main display window. Setting the
[**autoscale**](#cautoscale) option on the main Display panel will scale
the entire image to fit the main display window, the full frame buffer
will always be visible in the Panner marker window.

Images with more colors than can be displayed will automatically be
quantized to the number of available colors before display. If the
**Auto Grayscale** button is enabled any image colormap will be
converted to grayscale and loaded as the standard grayscale colormap.

Formats which permit pixels larger than 8-bits/pixel will be sampled on
a grid to determine an optimal range in the data to be used to compute a
linear transformation to the number of display colors. This is the same
z-scale sampling and transformation used by the IRAF **DISPLAY** task
when computing the **z1/z2** values and provides a much better initial
display than simple truncation to 8-bits. This scaling will be done
automatically using a grid of **Nsample** points if the **Zscale**
option is enabled. Otherwise, if the **Zrange** option is set the full
data range will be used to scale the image. Lastly, is neither
**Zscale** nor **Zrange** are enabled, the z1/z2 values may be set
explicitly using the options box.

### [Directory Browsing]{##lbrowse}

The load panel contains a list of files in the current directory that
may be selected for loading by selecting with left mouse button. If the
file is a directory the contents of the new directory will be loaded, if
it\'s a plain file an attempt will be made to load it as an image
otherwise an error popup will appear. Directories in the list are
identified with a trailing \'/\' character, you will always see any
subdirectories listed even if a filter is specified.

The **Root** button will reset the current directory to the system root
directory. The **Home** button will reset the current directory to the
user\'s login directory, the **Up** button moves up one directory level,
and **Rescan** reloads the file list by rescanning the directory. The
current working directory is given below the file selection window.

Selecting the **List Image Headers** option will change the display text
to list all images in the current directory which match the filename
filter. Directory browsing is disabled while this option is in effect.

### [File Patterns]{##lpattern}

By default all files and directories will be listed. You may specify a
filter to select only those files with a given extension such as
\"\*.fits\" using the **Filter** text box. Directories will always be
seen in the list and are identified with a trailing \'/\' character. Any
valid unix pattern matching string will be recognized, multiple
templates may be specified in a comma-delimited list such as
\"\*.imh,\*.fits\" to list both OIF and FITS images.

### [Direct File Load]{##lload}

If you know exactly which file you wish to load, you may enter its name
in the **Load File** text box and either hit \<cr\> or the **Load**
button to load it. An absolute or relative path name may be given, if a
simple filename is specified it will be searched for in the current
working directory which is displayed in the **Directory** label of the
panel.

### [Frame Selections]{##lframe}

By default images will be loaded into the current frame, you may choose
a different frame using the Frame menu button to select from the
available frames.

------------------------------------------------------------------------

[Save Panel]{##save}
--------------------

The Save Panel lets you save the current contents of the main display
window to a disk file (including the Panner/Coords markers, any general
graphics markers, or overlay graphics displayed by the client program).
Presently, only the contents of the main display window may be saved,
there is no facility for saving the undisplayed contents of the entire
frame buffer other than to enable the [autoscale](#cautoscale) feature.
A limited number of formats are currently available, others will be
added in future versions.

**[File Name]{##sfname}**
:   The **File Name** text box allows you to enter the file name of the
    saved file. A \"%d\" anywhere in the name will be replaced by a
    sequence number allowing multiple frames to be saved with unique
    names.

**[Format]{##sformat}**
:   The **Format** box allows you to choose the format of the image to
    be created. Not all formats are currently implemented. The EPS
    format is similar to the \\fIPrint\\fR option however there is no
    annotation.

**[Color]{##scolor}**
:   The **Color** box lets you choose the color type of the image to be
    created. The options will change depending on the format, e.g. FITS
    doesn\'t allow color so no color options will be allowed. Formats
    which allow 24-bit images will be written using the current colormap
    after converting to a 24-bit image, pseudocolor images will be
    written with the current colormap.

------------------------------------------------------------------------

[Print Panel]{##print}
----------------------

The Print Panel allows you dump the contents of the main display window
as Enacpsulated Postscript to either a named printer device or to a disk
file. The **Print To** selects the type of output, the **Print Command**
box will adjust accordingly, either as a Unix printer command or as a
file name. A \"%d\" anywhere in the name for disk output will be
replaced by a sequence number allowing multiple frames to be saved with
unique names. [Selecting printers](#pprinter) from the installed list
will automatically change the command to be used to generate the output.
This command does not necessarily need to be a printer command, the
[printer configuration file](#pprinter) lets you define any command
string to process the image.

### [Color Options]{##pcolors}

The **Color** box lets you choose the color type of the image to be
created. PseudoColor or 24-bit postscript will be created using the
current colormap.

### [Postscript Options]{##popts}

Orientation
:   Set the page orientation.

Paper Size
:   Select the paper size to be used.

Image Scale
:   Set the scale factor used to compute the final image size.

### [Processing Options]{##pproc}

Auto Scale
:   The auto scale toggles whether or not the image is automatically
    scaled to fit the page. If not enabled, the **image scale** will be
    used to dtermine the output image size.

Auto Rotate
:   Auto rotate determines whether or not the image will be rotated to
    fit on the page. When set, an image larger than the current
    orientation will be rotated and possibly scaled to fit the page.

Max Aspect
:   Max Aspect takes images smaller than the page and automatically
    increases the scale so the image fills the page in the current
    orientation.

Annotate
:   The annotate option toggles whether or not the final file includes
    annotation such as the image title, a colorbar, and axis labels.

### [Printer selection]{##pprinter}

The printer selection list lets choose the printer to be used. The
printer configuration file is /usr/local/lib/ximprint.cfg by default or
may be reset using the *printConfig* resource. The format of the file is
simply

        name < tab > command

The **name** value is what appears in the selection list and may be more
than a single word, the *command* can be any command that accepts EPS
input from a pipe, the two fields must be separated by a tab character.
Normally the command will be a simple \'lpr -Pfoo\' or some such, but
can also include converters or previewers. At most 128 printer commands
may be used.

------------------------------------------------------------------------

[Info Panel]{##info}
--------------------

The Info panel was revised to provide a greater variety of status
information. The type of output is controlled by the toggle buttons on
the bottom of the frame, however all output is kept current as the
program runs. Current info options include:

**Frame**
:   Info about the current display frame.

**Server**
:   Info about various server options, e.g. colormaps, memory model,
    antialias type, etc.

**Clients**
:   Show currently connected clients. Lists available connection
    channels and active ISM clients.

**WCS**
:   List all WCS and mappings for the current frame.

**ISM**
:   Log of various ISM status messages.

**Imtoolrc**
:   Show current frame buffer configuration table.

------------------------------------------------------------------------

[Tile Panel (NEW)]{##tileP}
---------------------------

With the additional frames, the default tiling scheme proved inadequate.
A new control panel Tile frame now allows you to select from a number of
tile configurations, the list of frames to be tiled, a **fill style**
(left-to-right or top-to-bottom), as well as optional labels for each of
the tiles (frame number, image title or image name).

Tile configuration will make use of all frames currently selected in the
**Tile Frame** group in the following manner:

**Disabled**
:   Do not tile the display.

**Manual**
:   Tile according to **Manual Configuration** settings.

**Best**
:   Optimize layout for frame buffer aspect.

**Square**
:   Always force a square layout (2x2, 3x3, etc).

**Horizontal**
:   Preferentially tile horizontally (6 frames ==\> 3x2).

**Vertical**
:   Preferentially tile vertically (6 frames ==\> 2x3).

**One Row**
:   Tile all in one row (Nx1).

**One Column**
:   Tile all in one column (1xN).

------------------------------------------------------------------------

[Coords Panel (NEW)]{##coordsp}
-------------------------------

The Coords Panel is meant to provide a full-featured readout as well as
serve as a control panel for the various options. The display window
contains the image name/title and frame buffer info, and a selection of
coordinate and image pixel readouts. The intent is provide more infor-
mation than can fit comfortably on the main image window while still
taking up as little screen space as possible. To this end the
**Options** button is used to hide most of the feature controls when not
in use (see below). Other options on the main panel include:

**WCS/Pix**
:   Toggle the real-time WCS/pixel readout capability (i.e. the ISM used
    to access the disk image). This must be enabled for certain other
    options to work.

**Pix Table**
:   Open a panel showing an image pixel table. The panel shows an array
    of pixels surrounding the cursor position, either the actual pixel
    values if the ISM is enabled, or scaled display values otherwise.
    The size of the table may be selected from the menubar.

**Header**
:   Display the current image header in a new panel. Both the entire
    image header as well as WCS-specific parts of the header are
    available under different tabs. This option is only active when the
    ISM is enabled.

**Compass**
:   Draw an orientation compass on the display panner. If the ISM is
    enabled and a WCS is present in the header, the compass will
    indicate N/E according to the WCS, otherwise the X/Y axes of the
    image are drawn.

**Options**
:   Pop-up/down the option control portion of the panel. When enabled,
    the Coords Panel will change size to reveal the options which can be
    changed (explained below).

The **Readout Values** group controls the selection of WCS type,
location and format to be displayed. The **Type** menu always provides a
selection of the image Logical, Physical or World systems, which may be
identical depending on the image header. If a World system is supplied
in the image addition entries for transformations to other sky systems,
(e.g. FK5 to ICRS or galactic/ecliptic) will also be available. The
selection is dependent on whether the ISM is running as well as WCS
information present in the image. The **Format** menu allows the use to
select a sexigesimal display, conversion to degrees or radians, or
whichever format is most natural for the coordinate being display. The
two toggle to the right control whether this WCS is to be displayed on
the *Panel* (i.e. the Coords Panel window) or the *ImgWin* (i.e. the
text marker on the main image window).

Other options below this group control whether or not to display the WCS
labels, the image name/title, and frame buffer information in the main
Coords Panel display. The **BPM Data** option controls whether or not
the ISM will try to map any bad-pixel mask associated with the image. If
enabled, a bad-pixel mask specified by the image header BPM keyword
(currently fixed by convention but this may be selectable later) will be
mapped along with the image. Aside from wcs/pixel readouts at each
cursor position, any BPM data values found will also be displayed. A
non-zero value will cause the BPM field of the Coords Panel readout as
well as the main image window marker to switch to a red background color
to flag the value.

The last box allows the user to specify a different ISM task to be
executed or to reinitialize the current one. In most cases this won\'t
need to be changed, however a custom ISM could be started when using
special data formats. This command string can also be controlled by the
application *ism\_task* resource.

------------------------------------------------------------------------

[Tcl Interactive Shell]{##tclshell}
-----------------------------------

The *TclShell* is mostly used as a development or debugging tool for the
GUI. It allows the user to type commands directly to the TCL interpreter
letting you send messages to the object manager or execute specific
procedures in the TCL code that makes up the GUI. Most users will never
need this, but for an example of what it does, bring it up and type a
command such as

        send helpButton set background red

Cool, huh.

------------------------------------------------------------------------

[Acknowledgements]{##acknowledgements}
--------------------------------------

*XImtool* was developed by the IRAF Group at the National Optical
Astronomy Observatories in Tucson, AZ. For further information or to
report problems please contact *iraf\@noao.edu*

------------------------------------------------------------------------

This document was last updated 11/6/96.
