
## Credit:
## Midi to Raspberry Pi Converter
##     - Andy Tran (extramaster), 2015
## https://www.extramaster.net/tools/midiToArduino/
##
## Process:
## Midi -> Midi tracks -> Note mappings -> Frequency
##
## CC0

import RPi.GPIO as GPIO
import time

# Set this to be the pin that your buzzer resides in. (Note that you can only have one buzzer actively using the PWM signal at a time).

# GD = GND = Ground
 
# RPI v1 GPIO Layout BCM
# 5V 5V GD 14 15 18 GD 23 24 GD 25 08 07
# 3V 02 03 04 GD 17 27 22 3V 10 09 11 GD

# RPI v2 GPIO Layout BCM
# 5V 5V GD 14 15 18 GD 23 24 GD 25 08 07 SC GD 12 GD 16 20 21
# 3V 02 03 04 GD 17 27 22 3V 10 09 11 GD SD 05 06 13 19 26 GD 

# Note: Raspberry Pi 2 seems to handle software-PWM a lot better then the original Raspberry Pis.
tonePin = 21

GPIO.setmode(GPIO.BCM)  
GPIO.setup(tonePin, GPIO.IN)
GPIO.setup(tonePin, GPIO.OUT)
p = GPIO.PWM(tonePin, 100)

# High-level abstraction of the Arduino's Delay function
def delay(times):
    time.sleep(times/1000.0)
    
# High-level abstraction of the Arduino's Tone function, though this version is blocking
def tone(pin, pitch, duration):
    if pitch == 0:
        delay(duration)
        return
    p = GPIO.PWM(tonePin, pitch)
    
    # Change the duty-cycle to 50 if you wish
    p.start(30)
    delay(duration)
    p.stop()
    
    # Delay used to discourage overlap of PWM cycles
    delay(2)
    
def midi():
    tone(tonePin, 349, 1571.35416667)
    delay(217.013888889)
    delay(394.965277778)
    tone(tonePin, 261, 105.729166667)
    tone(tonePin, 329, 1195.83333333)


while 1:
    midi()
    GPIO.cleanup()

