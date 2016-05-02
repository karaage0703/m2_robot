<img src="https://raw.githubusercontent.com/wiki/karaage0703/m2_robot/001.jpg" alt="m2_robot" width="640" height="480">

Robot software based on Raspberry Pi2 and Raspbian Jessie or Wheezy

# Robot Setup

## Install WebIOPi and apply patch
Execute following commands:
```sh
$ wget http://sourceforge.net/projects/webiopi/files/WebIOPi-0.7.1.tar.gz
$ tar xvzf WebIOPi-0.7.1.tar.gz
$ cd WebIOPi-0.7.1/
$ wget https://dl.dropboxusercontent.com/u/69652790/bb/WebIOPi-0.7.1.patched.tgz
$ tar zxf WebIOPi-0.7.1.patched.tgz
$ cd WebIOPi-0.7.1/
$ sudo ./setup.sh
```

## Install WebIOPi
Execute following command for changing permittion:
```sh
$ sudo chown -R pi /usr/share/webiopi/htdocs
```

Execute following command for password setting:
```sh
$ sudo webiopi-passwd
```

Execute following command for checking WebIOPi:
```sh
$ sudo /etc/init.d/webiopi start
```

## Install WiringPi2-python
Execute following commands:
```sh
$ cd
$ sudo apt-get update
$ sudo apt-get install python-dev python-setuptools
$ git clone https://github.com/Gadgetoid/WiringPi2-Python.git
$ cd WiringPi2-Python
$ sudo python setup.py install
$ sudo python3 setup.py install
```

## Install mjpg streamer
Execute following commands:
```sh
$ sudo apt-get update
$ sudo apt-get install libjpeg62-dev cmake
$ git clone https://github.com/jacksonliam/mjpg-streamer.git mjpg-streamer
$ cd mjpg-streamer/mjpg-streamer-experimental
$ make
$ cd ..
$ sudo mv mjpg-streamer-experimental /opt/mjpg-streamer
```

## Setting robot program
Execute following commands:
```sh
$ cd /usr/share/webiopi/htdocs
$ git clone https://github.com/karaage0703/m2_robot.git m2
$ cd m2
$ sudo mv webiopi.service /etc/systemd/system/
```

Edit /etc/webiopi/config
~~~~
$ sudo vi /etc/webiopi/config

from:
#myscript = /home/pi/webiopi/examples/scripts/macros/script.py

To:
myscript = /usr/share/webiopi/htdocs/m2/script.py
~~~~

Execute webiopi
~~~~
$ sudo systemctl start webiopi
~~~~

Access Robot and Enjoy!
Access below address on your browser.

~~~~
http://<ipaddress>:8000/m2/
~~~~

# Website
Please check for my website in detail(Japanese only)

http://karaage.hatenadiary.jp/entry/2015/09/02/073000

# License
This software is released under the MIT License, see LICENSE.
