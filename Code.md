```

import Tkinter as Tk
import tkFont
from gpiozero import LED
import RPi.GPIO 

RPi.GPIO.setmode(RPi.GPIO.BCM)


# Hardware

led1 = LED(18) # Red LED
led2 = LED(24) # Yellow LED
led3 = LED(12) # Green LED


# GUI 

window = Tk.Tk()
window.title("LED Toggler")
myFont = tkFont.Font(family = "Helvetica", size = 12, weight = "bold")


# Event Function

def ledToggle1():
    led1.on()
    led2.off()
    led3.off()


def ledToggle2():
    led2.on()
    led1.off()
    led3.off()
    

def ledToggle3():
    led3.on()
    led1.off()
    led2.off()
    


def close():
    RPi.GPIO.cleanup()
    window.destroy()


# Widgets

led1Button = Tk.Button(window, text = "Turn Red LED On", font = myFont, command = ledToggle1, bg = "red", height = 2, width = 30)
led1Button.grid(row = 0, column = 1)


led2Button = Tk.Button(window, text = "Turn Yellow LED On", font = myFont, command = ledToggle2, bg = "yellow", height = 2, width = 30)
led2Button.grid(row = 0, column = 2)


led3Button = Tk.Button(window, text = "Turn Green LED On", font = myFont, command = ledToggle3, bg = "green", height = 2, width = 30)
led3Button.grid(row = 0, column = 3)


exitButton = Tk.Button(window, text = "Exit", font = myFont, command = close, bg = "purple", height = 1, width = 24)
exitButton.grid(row = 1, column = 2)

window.protocol("WM_DELETE_WINDOW", close) # for clean exit

window.mainloop()

```
