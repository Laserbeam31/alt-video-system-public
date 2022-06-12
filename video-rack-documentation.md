Documentation for the BTS Rack ALT Video Handling Gear
======================================================

The BTS rack contains video patching, routing, and multiplexing equipment to facilitate the distribution of real-time feeds from the installed
cameras to different places around the theatre and, if necessary, building.

Multiplexer:
------------

The multiplexer "stitches" together multiple separate incoming composite video feeds into one single composite video output. This is useful for routing
multiple video feeds, as one composite stream, to zones such as the SM monitor and the DSM monitor.

In its usual mode of operation, the multiplexer outputs a 4x4 grid of the main stage camera, SR wing camera, SL wing camera, and runaround camera. Each
quarter of the multiplexed output grid is labelled according to its corresponding camera. The arrangement/number of video squares in the grid
can be changed if so desired.

The composite video feeds from the cameras are fed directly into the back of the multiplexer on composite inputs dervied (via baluns) from the dedicated 
stage-to-proj Cat5 run.
The multiplexer has "pass through" connections for these camera feeds, which means that each camera's connection is also paralleled into the MUSA
patch (see below) for camera-specific patching.

The multiplexer's combined output is fed into a connection on the MUSA patch, so that this output can be routed to where it is needed.

The unit also has advanced functionality for features better suited to its intended use as a processing station for CCTV cameras. These include the
ability to trigger a VCR, as well as the ability to input/output signals from an alarm system, and remote control over RS-232/RS-485.

For more information on the unit's capabilities, see the ZMX multiplexer manual in this repository.

Matrix switcher:
----------------

MUSA patch:
-----------
