Documentation for the BTS Rack ALT Video Handling Gear
======================================================

The BTS rack contains video patching, routing, and multiplexing equipment to facilitate the distribution of real-time CCTV cueing feeds from the installed
cameras to different places around the theatre and, if necessary, building. The rack additionally contains a section dedicated to VGA distribution; this is for
connection of computers or projectors for presentation/film-screening purposes.

Install cameras:
-----------------

There are three cameras permanently installed in/around the ALT stage. These are used for live cueing purposes. For example, the DSM may want to check whether the
stage wings are clear before calling a particular scene. All install cameras are IR-capable, meaning that they can generate a meaningful black-and-white picture 
in darkness.

- The **FoH camera** is located on the underside of the FoH 2 catwalk. This connects back to the BTS Proj Rack using a combined power+video loom over the auditorium
  roof sheets;
- The **wing cameras** are located above the fire exit doors in the stage-left and -right wings. They connect back to the BTS Proj Rack using multiple BNC baluns
  connected to the twisted pairs of a long Cat5e cable run over the auditorium roof sheets;
- The **runaround camera** is positioned over the up-stage runaround. It is screwed to the underside of the stage-right air conditioning duct support. This camera
  uses baluns to share cores in the same stage-Proj Cat5e run as the wing cameras.

The Cat5e cable whose constituent twisted pairs are shared by the wing and runaround cameras is terminated at the stage end in a junction box containing the 
necessary baluns to break the connection out to three BNC panel-mount connectors, one for each camera. At the Proj end, this cable terminates in baluns 
installed inside the BTS Rack, leading to BNC ports on the MUSA panel and multiplexer (see below).

Multiplexer:
------------

The multiplexer "stitches together" multiple separate incoming composite video feeds into one single composite video output. This is useful for routing
multiple video feeds, as one composite stream, to zones such as the SM monitor and the DSM monitor.

In its usual mode of operation, the multiplexer outputs a 4x4 grid of the main stage camera, SR wing camera, SL wing camera, and runaround camera. Each
quarter of the multiplexed output grid is digitallly annotated by the multiplexer. The arrangement/number of video squares in the grid
can be changed if so desired.

The composite video feeds from the stage cameras are fed directly into the back of the multiplexer on composite inputs derived (via baluns) from the 
dedicated stage-to-proj Cat5 camera cable.
The multiplexer has "pass through" connections for these camera feeds, which means that each camera's connection is also paralleled straight into the MUSA
patch (see below) for camera-specific patching.

Two more additional inputs to the multiplexer are also brought through directly to the MUSA patch, so that custom feeds may be input for multiplexing 
into a larger grid if so desired.

The multiplexer's combined output is fed into a connection on the MUSA patch, so that this output can be routed to where it is needed.

The unit also has advanced functionality for features better suited to its intended use as a processing station for CCTV cameras. These include the
ability to trigger a separate VCR, as well as the ability to input/output signals from an alarm system, and remote control over RS-232/RS-485.

For more information on the unit's capabilities, see the "zmx_multiplexer_manual.pdf" file in this repository.

Matrix switchers:
----------------

In essence, a matrix switcher can be thought of as an "electronic patch panel". It takes a series of different video inputs, and
can route each input, in its entirety, to one or more of its different outputs.

To route a given input to certain output(s), press the number corresponding to the input on the "inputs" row of matrix buttons. When this button lights up,
sequentially press the buttons on the "outputs" row whose numbers correspond to the outputs to which this input is to be routed. To save this
output state, press the "Enter" button to the right of the unit.

The Video Rack contains two matrices: the top large 8x8 matrix, used for switching the composite video feeds for the stage CCTV cameras (see below), and
a smaller 4x4 matrix for switching the VGA connections used when routing VGA sources for presentation purposes. For all intents and purposes, the 4x4 VGA matrix
and the 8x8 composite matrix form the backbone of the system's two main components: the CCTV system (composite), and the projection/slideshow system (VGA).

The reason behind splitting the CCTV and presentation systems across two different matrices is twofold: first, it maintains a logical segregation between the two
systems, given that they serve quite different purposes; second, VGA has a vastly superior image quality compared with composite, so is better suited for 
presentation use - which requires a better image quality than the standard composite signals used for CCTV.

The 8x8 composite video matrix's input and output connections are all brought out on the MUSA patch panel. The I/O from the 4x4 VGA matrix is brought out 
via a combination of the MUSA panel (for bridging to the CCTV system, if necessary; see below), the Cat5 panel (for VGA baluns), and the general Video Panel 
(see below). There is also a hard-wired connection between an output of the 4x4 VGA matrix and the BTS Projector, reflecting the intention that this section
of the video system is designed for presentation/screening use.

For more information on the 8x8 composite video matrix, see the "extron_crosspoint_matrix_manual.pdf" file in this repository.

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
`[password]` is the system password, and `Y` is the number of the composite input to be displayed. By default, the username and password are both `admin`.

Using the BTS Rack's Cat5 patch - through which all the Cat5-capable video gear is patched - the DVR's Ethernet connection may be connected either
to the BTS VLAN or the BUCS "Docking" network. The latter is very useful since it is effectively the same network as Eduroam, thus meaning that any device
connected to the Eduroam WiFi can view the RTSP stream from the DVR.

Whereas the BTS VLAN has no access controls, devices connected to Docking must have their MAC address authorised on ClearPass before a connection
is established. This is best done by contacting BUCS.

For more information on the DVR unit's capability and advanced configuration options, consult the "qvis_izeuss_dvr_manual.pdf" file in this repository.

MUSA patch:
-----------

MUSA connectors may be regarded as "easily pluggable BNC". They are a coaxial (coax) connector with no latch, thus allowing easy patching.

The MUSA patch is the main means of physically patching the CCTV video links from around the theatre to one another, including through devices such as the 
multiplexer and/or 8x8 composite matrix switcher. Each camera, composite cable run, BNC balun, and other in-rack CCTV appliance, has at 
least one connection on the MUSA patch to allow it to be dynamically interfaced with the rest of the system.

For commonly-used inter-port MUSA links, the "U"-shaped rigid adapters are used where possible, since they are neater than leaving patch leads 
protruding from the front of the rack.

The following important links are in the MUSA patch:

- Matrix in/out ports. For patching inputs and outputs to multiple places using the 8x8 composite matrix switcher. See above;
- Additional (non-hard-wired) multiplexer inputs. These are in addition to the stage cameras which are hard-wired to multplexer inputs;
- Multiplexer output;
- DVR composite output;
- Composite over Cat5 baluns. There are two of these installed in the rack with their composite ends connected to the MUSA patch, and their Cat5 ends
  connected up to the Cat5 patch. They are bi-directional, meaning that the same balun can be used either as a sender or a receiver;
- VGA over Cat5 sender baluns. These are formed of two in-rack components: a composite-VGA converter which ingests a composite signal from the MUSA panel, and a VGA over Cat5
  transmitter balun. The Cat5 output from this balun is then brought out to the BTS Rack's Cat5 patch;
- A single port containing the output from a unidirectional VGA-composite converter, whose input originates from the 4x4 VGA matrix. This acts as a "bridge" between the VGA
  presentation system (routed through the 4x4 VGA matrix) and the CCTV system (routed through the 8x8 matrix), in the event that a VGA source on the presentation system's
  4x4 matrix needs to be fed to the CCTV system;
  
For a detailed layout of the MUSA patch, see the "MUSA" tab of the "BTS_rack_patch_layout_plan" spreadsheet in this repository.

Cat5 patch panel
----------------

Apart from regular Cat5 tie lines around the ALT, this patch panel contains inputs/outputs from the aforementioned video baluns used in the CCTV system as
a means of ingesting composite signals and outputing VGA CCTV feeds for stage monitors etc. 

This panel also contains the input to a single Cat5-VGA receiver balun. This forms part of the presentation system rather than the CCTV system, and as such 
its VGA output is sent, within the rack, to the 4x4 VGA matrix. This receiver balun is intended to be used as a means of connecting laptops etc for presentation use.

General-use video panel
-----------------------

The Video Panel contains direct video connection points to the MUSA panel (for the CCTV system, on a BNC port) and the 4x4 VGA matrix (for the presentation system). 
The main intention with these ports is for temporary connection of displays etc directly to the rack, possibly during patching, testing, or diagnostics, 
without the need for intermediate balune.

Links to Box 203:
-----------------

Box 203, colloquially referred to as the "Edge Rack", contains a composite video distribution amplifier (DA). This is a simple device which takes in
a composite feed and amplifies it to multiple separate outputs, for patching to different destinations. Using the links between the BTS MUSA patch
and the Box 203 MUSA patch, it is possible to make use of the DA.

Box 203 also contains composite video patch runs to other parts of the Edge building which have BNC hard-wired into their wall panels. Whereas the ALT 
video
runs are done entirely over Cat5 baluns, certain video runs through the building may be patched directly (without baluns) by means of the installed BNC
runs to certaiin wall boxes.
