Documentation for the BTS ALT Catwalk Monitor Remote Power Switch 
=================================================================

Using the illuminated switch installed in the BTS rack, marked "CATWALK MONITORS", it is possible to remotely power on and off the VGA balun
connecting the two catwalk monitors to the analogue video system. Turning off this balun has the effect of kicking the monitors into standby.
Without this switch, the only way to put the monitors into standby would be to ascend to the catwalk and either unplug the balun or press the local
power button on each monitor.

Given that the best way to make working at height safer is to eliminate the need to ascend to height at all, this remote switch plays an invaluable
role in making use of the video system safer :)

Technical details:
------------------

There are two buttons fitted in a 1U plate in the BTS rack. Each button is electrically connected to a port on the Cat5e patch in the rack. Using
the Cat5e patch, it is possible to link the buttons to any other Cat5e port in the ALT. Each button has electrical links to its 5V power LED, and
its actual swiitched terminals.

At the other end, a modified balun power supply connects into a Cat5e port somewhere else in the ALT (typically only on the catwalk) which
is in turn patched back to the BTS rack buttons through the building patch. This modified
power supply has its low-voltage output wires intercepted such that the switched terminals of the button in the rack are able to break the circuit on
the supply's low-voltage side, and also such that power is sent (over a separate pair of Cat5e conductors) to light up the rack button's internal
LED when the switch is turned on and the downstream balun therefore receiving power.

As of 07/06/2022, only one rack button is connected to one modified balun power supply: that of tha catwalk monitors. 
The other button in the rack panel is a spare to allow
for future expansion if another modified balun power supply is assembled.

Cat5e wiring standard for the rack buttons and modified balun PSU(s):
---------------------------------------------------------------------

| Name            | Cat5e Colours     |
|-----------------|-------------------|
| Switched line(+)| Brown/green       |
| LED power       | Orange(+)/blue(-) |

For reduced voltage drop over long runs, the twisted pairs are commoned. Hence why only colours are stated in the above table.

**Since the buttons run over the same Cat5e patch as the rest of the ALT networking/video gear, it is imperative that neither they, nor a
modified balun power cable, get erroneously patched to some other IP/balun device. Even though they all use the same Cat5e connectors,
this runs the risk of causing major damage. In the context of video systems, it is never safe to assume that two devices are interoperable
simply because they have the same physical connectors.**
