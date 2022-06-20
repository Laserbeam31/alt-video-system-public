Documentation for the BTS Rack ALT Video Handling Gear
======================================================

The BTS rack contains video patching, routing, and multiplexing equipment to facilitate the distribution of real-time feeds from the installed
cameras to different places around the theatre and, if necessary, building.

Multiplexer:
------------

The multiplexer "stitches" together multiple separate incoming composite video feeds into one single composite video output. This is useful for routing
multiple video feeds, as one composite stream, to zones such as the SM monitor and the DSM monitor.

In its usual mode of operation, the multiplexer outputs a 4x4 grid of the main stage camera, SR wing camera, SL wing camera, and runaround camera. Each
quarter of the multiplexed output grid is digitallly annotated by the multiplexer. The arrangement/number of video squares in the grid
can be changed if so desired.

The composite video feeds from the cameras are fed directly into the back of the multiplexer on composite inputs dervied (via baluns) from the dedicated 
stage-to-proj Cat5 run.
The multiplexer has "pass through" connections for these camera feeds, which means that each camera's connection is also paralleled straight into the MUSA
patch (see below) for camera-specific patching.

The multiplexer's combined output is fed into a connection on the MUSA patch, so that this output can be routed to where it is needed.

The unit also has advanced functionality for features better suited to its intended use as a processing station for CCTV cameras. These include the
ability to trigger a VCR, as well as the ability to input/output signals from an alarm system, and remote control over RS-232/RS-485.

For more information on the unit's capabilities, see the ZMX multiplexer manual in this repository.

Matrix switcher:
----------------

In essence, the matrix switcher can be thought of as an "electronic patch panel". It takes a series of different composite video inputs, and
can route each input, in its entirety, to one or more of its different outputs.

The matrix input and output connections are brought out on the MUSA patch panel.

To route a given input to certain output(s), press the number corresponding to the input on the top row of matrix buttons. When this button lights up,
sequentially press the buttons on the row below whose numbers correspond to the outputs to which the input in question is to be routed. To save this
output state, press the "Enter" button to the right of the unit.

MUSA patch:
-----------

The MUSA patch is the main means of physically patching the video links from around the theatre to one another, including through devices such as the 
multiplexer
and/or matrix switcher. Each camera, composite cable run, balun, and other  rack video handling appliance, has at least one connection on the MUSA
patch to allow it to be dynamically interfaced with the rest of the system.

For commonly-used inter-port links on the MUSA patch, the "U"-shaped adapters are used, since they are neater than leaving MUSA patch leads hanging out
of the front of the rack.

The following important links are in the MUSA patch:

- Matrix in/out ports. For patching inputs and outputs to multiple places using the matrix switcher. See above;
- Multiplexer. This takes in the feed from the stage camera baluns directly, multiplexes it, and outputs the multiplexed feeds, along
  with identical "copies" of the incoming individual camera feeds, through to the MUSA patch panel;
- Baluns. Cat5 composite and VGA baluns, installed inside the rack, can have video sent to/from them from the MUSA patch. 
  The Cat5 connections on said baluns are brought out to Cat5 ports on the BTS rack's network patch. This is particularly
  useful if patching in a camera or monitor in an unusual location: the remote camera/monitor can be installed with a suitable balun next to it -
  which then runs its signal over the installed Cat5 cabling back to the BTS rack and its corresponding internal baluns. It is important to note that
  whilst the composite-over-Cat5 baluns can be used for eiher transmitting or receiving over Cat5, the same is not true for the VGA baluns. All the
  VGA balun outputs on the BTS rack are _transmit only_. A corresponding VGA _receiver_ balun must therefore be used at the other end of their
  corresponding patched Cat5 run through the building.
  
Technically speaking, the Cat5 VGA transmitter baluns in the rack must take in a VGA signal. However, only composite video is routed through the
multiplexer, matrix switcher, and MUSA patch panel. There are therefore composite-VGA conversion boxes between the VGA baluns and their respective
MUSA inputs, to achieve this signal conversion.

Links to Box 203
----------------

Box 203, colloquially referred to as the "Edge Rack", contains a composite video distribution amplifier (DA). This is a simple device which takes in
a composite feed and amplifies it to multiple separate outputs, for patching to different destinations. Using the links between the BTS MUSA patch
and the Box 203 MUSA patch, it is possible to make use of the DA.

Box 203 also contains composite video patch runs to other parts of the Edge building which have BNC hard-wired into their wall panels. Whereas the ALT 
video
runs are done entirely over Cat5 baluns, certain video runs through the building may be patched directly (without baluns) by means of the installed BNC
runs to certaiin wall boxes.
