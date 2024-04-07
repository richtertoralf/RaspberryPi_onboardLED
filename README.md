# RaspberryPi_onboardLED
Onboard-LED des RaspberryPi zero 2 W ansprechen

**Problem:**

Ich habe mehrere RaspberryPi Zero 2 W nebeneinander stehen, mit denen ich per SSH verbunden bin. Ich weiß aber gerade nicht, auf welchem RaspberyPi ich mich befinde!

**Lösungsidee:**  
Ich lasse die onboard-LED blinken.  

Getestet am 07.04.2024 auf diesem System:
```
root@raspi102:~# cat /etc/os-release
PRETTY_NAME="Raspbian GNU/Linux 12 (bookworm)"
NAME="Raspbian GNU/Linux"
VERSION_ID="12"
VERSION="12 (bookworm)"
VERSION_CODENAME=bookworm
ID=raspbian
ID_LIKE=debian
HOME_URL="http://www.raspbian.org/"
SUPPORT_URL="http://www.raspbian.org/RaspbianForums"
BUG_REPORT_URL="http://www.raspbian.org/RaspbianBugs"
```

### Onboard-LED blinken lassen ###
```
# Einschalten:
echo 255 | tee /sys/class/leds/ACT/brightness
```
```
# Ausschalten:
echo 0 | tee /sys/class/leds/ACT/brightness
```
```
# Einzeiler, lässt die grüne Onboard-LED 10 x Blinken
for i in {1..10}; do echo 0 > /sys/class/leds/ACT/brightness; sleep 0.5; echo 255 > /sys/class/leds/ACT/brigh
tness; sleep 0.5; done
```
