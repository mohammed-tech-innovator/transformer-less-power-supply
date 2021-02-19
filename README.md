# transformer-less-power-supply
converting AC to low voltge DC without transformer
this transformer less power supply uses DC to DC converter to step down the output of a bridge rectifier . simple LC filter is used to smooh the output of the rectifier.
It doesn't matter whither the AC input is 110v or 220v of any value up to certain limit . or even DC input . 
the microcontraller used is the Attiny85 running at 16 MHz . while the PWM frequency 490Hz .
snychronous buck converter is used which increases the efficiency . the output of the buck converter is the input to another LC filter the output of the filter is applied to a zener dioed for protection .
on the other hand this configration is less immune to noise , and produces some systemic noises resulting from the PWM .
