
Floppy drive motor FMD03150B4
=============================

Measurement results of my specific motor. Use with caution.


Wiring/Pinout
-------------

[Annotated photo](fmd03150b4_pinout.jpeg)
<!-- font: Bitstream Vera Sans 22 -->

* The front-side (near shaft) cables go to the front-side solder joints.
* The rear-side cables go to the rear-side solder joints.
* Front and rear supply one coil each. Both coils have a resistance of
  about 60&nbsp;&Ohm; each.


Driving via audio signal
------------------------

* Signal needs to be amplified to at least 4 or 5&nbsp;V.
* It's a [bipolar stepper motor][wp-bipolar] so it wants some pattern
  of R+ L+ L- R-.
  * :TODO: figure out which pattern is for cw/ccw.







  [wp-bipolar]: https://en.wikipedia.org/wiki/Stepper_motor#Bipolar_motors
