<img src="https://raw.githubusercontent.com/wiki/karaage0703/m2_robot/001.jpg" alt="m2_robot" width="640" height="480">

Robot software based on Raspberry Pi2 and Raspbian Jessie or Wheezy

Setup is below

1. Install webiopi and WiringPi2-Pytho and mjpegstreamer

2. Execute below commands
~~~~
$ cd /usr/share/webiopi/htdocs
$ git clone https://github.com/karaage0703/m2_robot.git m2
$ cd m2
$ sudo mv webiopi.service /etc/systemd/system/
~~~~

3. Edit /etc/webiopi/config
~~~~
$ sudo vi /etc/webiopi/config

from:
#myscript = /home/pi/webiopi/examples/scripts/macros/script.py

To:
myscript = /usr/share/webiopi/htdocs/m2/script.py
~~~~

4. Execute webiopi
~~~~
$ sudo systemctl start webiopi
~~~~

5. Access Robot and Enjoy!
Access below address on your browser.

~~~~
http://<ipaddress>:8000/m2/
~~~~

Please check for my website in detail(Japanese only)

http://karaage.hatenadiary.jp/entry/2015/09/02/073000
