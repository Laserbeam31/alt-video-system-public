Documentation for the BTS Composite Stage Cameras in the ALT
============================================================

The ALT has installed composite video cameras which, with the assistance of the BTS rack equipment such as the multiplexer and matrix switcher, allow
real-time composite feeds to be patched to screens around the theatre and, if necessary, the wider Edge building.

Camera positioning:
-------------------

The video system has provision for four standing cameras:

- The main stage camera. This is attached to a piece of scaffolding tube protruding from FoH catwalk 2. It has IR night vision and can therefore
  be used to view the stage during blackouts, as well as when it is illuminated. The camera handles the transition between day- and night-vision 
  automatically. It is important to note that night vision is only in black-and-white.
  
- The stage wing cameras. These are fixed by the fire exit doors of each wing and allow relevant crew members (particularly the SM and DSM) to
  see the state of the wings.
  
- The runaround camera. As of 20/06/2022 this is not in place. This is mounted by the stage-right fire exit door and has a view round the
  back of the stage. This is occasionallly useful for the DSM/SM to view the movement of cast members during quick scene transitions.
 

Power and data arrangements:
----------------------------

The main stage camera is connected back to the BTS proj rack with a combined 12VDC and composite video cable. A 12V power supply in the proj rack provides 
the low-voltage supply.

The stage cameras have their video and power connections provided by a custom-made distribution box which sits on top of the stage-right fire exit porch.
This box takes in a Cat5 cable from the proj, as well as a local 12VDC supply from a "wall-wart" power supply, and contains switches and composite-Cat5 
baluns which
bring these connections out to three BNC connectors for the cameras' video outputs, and three 12VDC barrel connectors for the cameras' power inputs. 
At the proj end, the aforementioned Cat5 cable is connected (via composite-Cat5 baluns) into the BTS rack's video handling gear.

Technical details:
------------------

The stage-to-proj Cat5 run terminates in the bespoke distribution box at the stage end, and in a set of loose baluns at the proj rack end.

Within the bespoke distribuion box, the following pairs from the stage-to-proj Cat5 cable are used for each of the three cameras' corresponding balun:

- Runaround camera balun: brown / brown stripe Cat5 pair
- SR wing camera balun: blue / blue stripe Cat5 pair
- SL wing camera balun: green / green stripe Cat5 pair
