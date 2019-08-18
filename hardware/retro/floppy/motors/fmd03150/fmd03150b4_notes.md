
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


Rear plate
----------

[Outside photo](fmd03150b4_rear_plate_outer.jpeg) /
[Inside photo](fmd03150b4_rear_plate_inner.jpeg)

* The outside has the type label, it says:
  ```text
      MC
  FMD03150B4
    ¦315E
    S K01
  ```
* It can be removed by gently opening either of both clamps on the sides.
* On the inside it has an angle-shaped spring and three dots forming a smiley.



Driving via audio signal
------------------------

* Signal needs to be amplified to at least 4 or 5&nbsp;V.
* It's a [bipolar stepper motor][wp-bipolar] so it wants some pattern
  of R+ L+ L- R-.
  * :TODO: figure out which pattern is for cw/ccw.







  [wp-bipolar]: https://en.wikipedia.org/wiki/Stepper_motor#Bipolar_motors
