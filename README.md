# legendary-octo-telegram
from machine import Pin
from time import sleep

led1 = Pin(1, Pin.OUT)
led2 = Pin(2, Pin.OUT)
led3 = Pin(3, Pin.OUT)
led4 = Pin(4, Pin.OUT)
led5 = Pin(5, Pin.OUT)
led6 = Pin(6, Pin.OUT)
led7 = Pin(7, Pin.OUT)
led8 = Pin(8, Pin.OUT)

buttonA = Pin(9, Pin.IN)
buttonB = Pin(10, Pin.IN)

speed = 1

while True:
    for i in range(1, 9):
      if buttonA.value() == 1:
        if speed < 0.4:
          speed = 0.2
        else:
          speed -= 0.2
        print('Speed Increases: ', speed)
      if buttonB.value() == 1:
        if speed >= 1:
          speed = 1.0
        else:
          speed -= 0.2
        print('Speed Decreased: ', speed)
      if buttonA.value() and buttonB.value() == 1:
        speed = 0.1
    led = Pin(i, Pin.OUT)
    led.on()
    sleep(speed)
    led.off()
  
