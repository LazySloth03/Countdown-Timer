# Countdown-Timer
A countdown timer using Raspberry Pi

#!/bin/python3

from sense_hat import SenseHat
from time import sleep

countdowner921 = SenseHat()

G = [0, 255, 0]
R = [255, 0, 0]
MR = [255, 0, 225]
X = [0, 0, 0]

s = 10

timer = []

for i in range(64):
  if i  < s:
    timer.append(G)
    print(timer)
  else:
    timer.append(X)
    
countdowner921.set_pixels(timer)

for i in range(0, s):
  sleep(1)
  timer[i] = R
  countdowner921.set_pixels(timer)
  sleep(0.1)
  
for i in range(0, 10):
  countdowner921.clear()
  sleep(0.1)
  countdowner921.set_pixels(timer)
  sleep(0.1)

for i in range(5, -1, -1):
  countdowner921.show_letter(str(i), MR)
  sleep(1)
