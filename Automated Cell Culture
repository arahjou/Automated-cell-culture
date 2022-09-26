#!/usr/bin/python
# Import lib(s)
from threading import Thread
import time
import Adafruit_ADS1x15
import smtplib
import RPi.GPIO as GPIO
from time import sleep

#set GPIO numbering mode and define output pins
GPIO.setmode(GPIO.BOARD)

# Create an ADS1115 ADC (16-bit) instance.
adc = Adafruit_ADS1x15.ADS1115()

# Gain of 1 for reading voltages from 0 to 4.09V.
GAIN = 1
pHChannel = 0
sleepTime = 1

#Controlling the main motor. This motor turns a propiller to
# homogenis the media 30s every two hours.
def Motor_0():
    while True:
        print("one")
        GPIO.setmode(GPIO.BOARD)
        GPIO.setup (7, GPIO.OUT)
        GPIO.output(7, True)
        time.sleep(10)
        GPIO.setmode(GPIO.BOARD)
        GPIO.setup (7, GPIO.OUT)
        GPIO.output(7, False)
        time.sleep(5)
        GPIO.cleanup()

# Reading analog data from pH sensor     
def readingData(channel):
    print("two")
    pHdata = adc.read_adc(0, gain=GAIN)
    return pHdata

# Reacting to pH changes by controlling motor 1 and 2 plus sending an email
def pHsensor():
    while True:
        print("three")
        value = readingData(pHChannel)
        y= float(-0.0007)*(value)
        pH = float(y) + float(24.018)
        print(pH)
        # Pause for a second.
        time.sleep(sleepTime)
        GPIO.setmode(GPIO.BOARD)
        GPIO.setup(11,GPIO.OUT)
        GPIO.setup(13, GPIO.OUT)
        if value > 25350:
            GPIO.output(11,True)
            time.sleep(2)
            GPIO.output(11,False)
            GPIO.output(13,True)
            time.sleep(2)
            GPIO.output(13,False)
            #server = smtplib.SMTP('smtp.gmail.com', 587)
            #server.starttls()
            #server.login("pi.pro.biology@gmail.com", "raspberry2018#")
            #smg = "Cells are delivered to container."
            #server.sendmail("pi.pro.biology@gmail.com", "ali.rahjouei@mdc-berlin.de", smg)
            #server.quit()
            GPIO.cleanup()
        elif value < 25350:
            GPIO.output(11,False)
            GPIO.output(13, False)
            GPIO.cleanup()

t1 = Thread(target = Motor_0)
t2 = Thread(target = pHsensor)

t1.start()
t2.start()
GPIO.cleanup()
