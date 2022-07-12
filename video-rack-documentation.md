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

The composite video feeds from the stage cameras are fed directly into the back of the multiplexer on composite inputs dervied (via baluns) from the 
dedicated stage-to-proj Cat5 camera cable.
The multiplexer has "pass through" connections for these camera feeds, which means that each camera's connection is also paralleled straight into the MUSA
patch (see below) for camera-specific patching.

Two more additional inputs to the multiplexer are also brought through directly to the MUSA patch, so that custom feeds may be inputted for multiplexing 
into a larger grid if so desired.

The multiplexer's combined output is fed into a connection on the MUSA patch, so that this output can be routed to where it is needed.

The unit also has advanced functionality for features better suited to its intended use as a processing station for CCTV cameras. These include the
ability to trigger a VCR, as well as the ability to input/output signals from an alarm system, and remote control over RS-232/RS-485.

For more information on the unit's capabilities, see the "zmx_multiplexer_manual.pdf" file in this repository.

Matrix switcher:
----------------

In essence, the matrix switcher can be thought of as an "electronic patch panel". It takes a series of different composite video inputs, and
can route each input, in its entirety, to one or more of its different outputs.

The matrix input and output connections are brought out on the MUSA patch panel.

To route a given input to certain output(s), press the number corresponding to the input on the top row of matrix buttons. When this button lights up,
sequentially press the buttons on the row below whose numbers correspond to the outputs to which the input in question is to be routed. To save this
output state, press the "Enter" button to the right of the unit.

For more information, see the "extron_crosspoint_matrix_manual.pdf" file in this repository.

MUSA patch:
-----------

The MUSA patch is the main means of physically patching the video links from around the theatre to one another, including through devices such as the 
multiplexer
and/or matrix switcher. Each camera, composite cable run, balun, and other rack video handling appliance, has at least one connection on the MUSA
patch to allow it to be dynamically interfaced with the rest of the system.

For commonly-used inter-port links on the MUSA patch, the "U"-shaped adapters are used where possible, since they are neater than leaving MUSA patch leads 
hanging out of the front of the rack.

The following important links are in the MUSA patch:

- Matrix in/out ports. For patching inputs and outputs to multiple places using the matrix switcher. See above;
- Additional (non-hard-wired) multiplexer inputs. These are in addition to the stage cameras which are hard-wired to multplexer inputs;
- Multiplexer output;
- Composite over Cat5 baluns. There are two of these installed in the rack with their composite ends connected to the MUSA patch, and their Cat5 ends
  connected up to the Cat5 patch. They are bi-directional, meaning that the same balun can be used either as a sender or a receiver;
- VGA over Cat5 baluns. These are actually two types of balun: a sender (VGA-Cat5) and a receiver (Cat5-VGA). One receiver (for inputting e.g.
  custom video to the system) and multiple senders are installed in the rack. By means of composite-VGA/VGA-composite conversion boxes (also installed
  inside the rack), these Cat5 baluns are interfaced to standard composite connections on the MUSA patch, from which they can then interoperate with
  the rest of the composite video gear.

Qvis DVR:
---------

The Qvis DVR in the BTS rack takes in four composite video inputs, multiplexes them into a 4x4 grid on a single output, and sends this
multiplexed output over VGA and composite connections. The advantage of a VGA output connection is that, even with a multiplexed grid, each constituent
composite feed in the grid is displayed at its full resolution. This is because the overall VGA picture resolution is higher than composite video resolution.

Importantly, the DVR can send any of its incoming composite video feeds as an RTSP stream over IP 
(see: https://en.wikipedia.org/wiki/Real_Time_Streaming_Protocol) by means of its Ethernet port.

In general, the multiplexed feed emanating from this unit should not be used as a substitute for the usual multiplexer. It should be used
to generate a secondary (possibly higher-resolution, depending on whether the VGA or composite output is used) multiplexed feed in addition to the
above multiplexer unit, or as a means of transmitting composite streams via an Ethernet network.

**Connections:**

|   Connection type   |   Number    |          Use                                                                                                              |                     Connection point                                |
|---------------------|-------------|---------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| Composite input     | 4           | Ingest a single composite video feed                                                                                      | MUSA patch panel (bottom row)                                       |
| Composite output    | 1           | Output a composite multiplexed view of the four inputs. This is of lower resolution than the equivalent VGA connection    | MUSA patch panel (top row)                                          |
| VGA output          | 1           | Output a multiplexed view of the four inputs. Being VGA, this output can show each consituent feed in its full resolution | Cat5 patch panel (_via hidden black passive VGA-Cat5 sender balun_) |
| Ethernet output     | 1           | Network access. Used for distributing RTSP streams (see above) and also for accessing the unit's web control panel        | Cat5 patch panel                                                    |

NB: The VGA and composite outputs always show the same feed, just at different resolutions.

**Networking:**

The unit generates a separate RTSP stream for each of its four input connections.

An easy way to view the network RTSP stream is by using VLC on a computer on the same network as the DVR. In VLC, select "Open Network Stream" and enter
the following address:

`rtsp://[username]:[password]@XXX.XXX.XXX.XXX:554/cam/realmonitor?channel=Y&subtype=0`

Where `XXX.XXX.XXX.XXX` is the IP address of the DVR on the particular network to which it is connected, `[username]` is the system username,
`[password]` is the system password, and `Y` is the number of the composite input to be displayed.

Using the BTS Rack's Cat5 patch - through which all the Cat5-capable video gear is patched - the DVR's Ethernet connection may be connected either
to the BTS VLAN or the BUCS "Docking" network. The latter is very useful since it is effectively the same network as Eduroam, thus meaning that any device
connected to the Eduroam WiFi can view the RTSP stream from the DVR, when it is also connected to Docking.

Whereas the BTS VLAN has no access controls, devices connected to Docking must have their MAC address authorised on ClearPass before a connection
is established. This is best done on an individual basis. As of July 2022, the DVR's Ethernet connection is authorised under John Lucas's BUCS ID.
It is important to note that personal BUCS device authorizations expire after a year.

For more information on the DVR unit's capability and advanced configuration options, consult the "qvis_izeuss_dvr_manual.pdf" file in this repository.

Links to Box 203:
-----------------

Box 203, colloquially referred to as the "Edge Rack", contains a composite video distribution amplifier (DA). This is a simple device which takes in
a composite feed and amplifies it to multiple separate outputs, for patching to different destinations. Using the links between the BTS MUSA patch
and the Box 203 MUSA patch, it is possible to make use of the DA.

Box 203 also contains composite video patch runs to other parts of the Edge building which have BNC hard-wired into their wall panels. Whereas the ALT 
video
runs are done entirely over Cat5 baluns, certain video runs through the building may be patched directly (without baluns) by means of the installed BNC
runs to certaiin wall boxes.
