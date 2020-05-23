
LED Strip Amplifier
===================

Pinout
------

Sicht auf bedruckte Seite.

```text
   .----------------------.
  o| In_blu       Out_blu |o
  o| In_red       Out_red |o
  o| In_grn       Out_grn |o
  o| In_12V       Out_12V |o
   '----------------------'
                / /
  Power_GND ---´ /
  Power_12V ----´
```

Rückseite der Leiterplatte zeigt, was Widerstandsmessungen schon andeuteten:
In_12V, Out_12V und Power_12V sind miteinander direkt kurzgeschlossen.

Im Leerlauf (nur Power_GND und Power_12V verbunden) liegt die Spannung an
den Eingängen knapp 12 V über Power_GND, d.h. fast bei Power_12V.
(Gemessen z.B. 10,74 V.)



Schaltverhalten
---------------

Der jeweilige Ausgang ist genau dann "an" (d.h. mit Power_GND verbunden),
wenn die Spannung zwischen dem zugehörigen Eingang und In_12V mindestens
8 ± 0,2 V erreicht, d.h. die Spannung zwischen Power_GND und dem Eingang
höchstens 4 ± 0,2 V beträgt.

Ein PWM-Erzeuger, der sich GND mit dem LED-Verstärker teilt, muss also zum
zuverlässigen Einschalten der LED dafür sorgen, dass an seinem Signalausgang
höchstens 3,8 V anliegen.
Zum zuverlässigen Ausschalten der LED muss er die Ausgangsspannung auf
mindestens 4,2 V legen.

Als Spannungsbereich für das PWM-Signal eignet sich somit insb. 5 ± 0,3 V.
Der PWM-Erzeuger könnte damit aus IDE- und USB-Kabeln im normalen Betrieb
gespeist werden, sofern der Stromverbrauch akzeptabel niedrig ist.
Problem dabei: Eignet sich der PWM-Erzeuger dazu, seinen Ausgang aktiv
_nach unten_ zu ziehen?



Hyp: Signaleingang hat Pull-up-Widerstand
=========================================

(Weil im Leerlauf fast VCC anliegt.)

* Obacht: Multimeter verkraftet für Stromstärke-Messung max. 200 mA,
  daher vorher durch Spannungsabfall an Vorwiderstand schätzen!



Ex: kleiner Vorwiderstand
-------------------------

```text
R_vor = 148 Ω
U_{R_vor,min} = 15,2 mV
U_{R_vor,max} = 15,5 mV
I_max = U_max / R_min = 15,5 mV / 148 Ω = 0,10473 mA
I_min = U_min / R_max = 15,2 mV / 148 Ω = 0,10270 mA
I_mess = 0,105 mA

"Amp" := vom Signaleingang zu In_12V.
U_Amp = 11,96 V
R_Amp = U_Amp / I_mess = 11,96 V / 0,105 mA = 113,9 kΩ
```



Ex: riesiger Vorwiderstand
--------------------------

```text
R_vor_min = 680 kΩ
R_vor_max = 700 kΩ
U_{R_vor,min} = 8,8 V
U_{R_vor,max} = 9,2 V
I_max = U_max / R_min = 9,2 V / 680 kOhm = 0,01353 mA
I_min = U_min / R_max = 8,8 V / 700 kOhm = 0,01257 mA
I_mess = 0,014 mA

U_Amp_min: 1,70 V
U_Amp_max: 2,33 V
R_Amp_min = U_Amp_min / I_mess = 1,70 V / 0,014 mA = 121,42857 kΩ
R_Amp_max = U_Amp_max / I_min  = 2,33 V / 0,01257 mA = 185,36197 kΩ

R_Amp_{mess,min} = 108,2 kΩ
R_Amp_{mess,max} = 124,4 kΩ
```


Ex: Ohne Vorwiderstand
----------------------

```text
I_Amp_max = U_Amp_max / R_Amp_min

Beispielhafte Messung:
U_Amp_1 = 10,74 V
I_Amp_1 = U_amp_1 / 108,2 kΩ = 0,099261 mA

Maximal möglich aufgrund Stromquelle:
I_Amp_max = 12 V / 108,2 kΩ = 0,111 mA

Kann also gefahrlos gemessen werden. (Trotzdem im hohen Bereich anfangen!)

I_Amp_{mess,min} = 0,102 mA
I_Amp_{mess,max} = 0,106 mA
```



Ex: PWM von Motortreiber
------------------------

Die spontan herumliegende PWM-Erzeuger-Platine ist laut Beschreibung zum
Betrieb von Motoren gedacht, somit also dafür, ihr Ausgangssignal nach oben
zu ziehen, von ihrem GND weg.
Müssen wir mit einem Pull-down-Widerstand nachhelfen?



























