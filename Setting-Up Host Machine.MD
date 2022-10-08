Open Ubuntu VM and it's Terminal to get Started

# Update System
```
sudo apt-get update && sudo apt-get upgrade -y
```
# Add Users
```
sudo adduser cuckoo
```
```
sudo usermod -aG sudo cuckoo
```
```
# Installing Pre-Requisites
```
```
sudo apt-get -y install python python3-pip python-dev virtualenv python-setuptools curl git libffi-dev libssl-dev libjpeg-dev zlib1g swig
```
```
sudo apt-get -y install mongodb
```
```
sudo apt-get -y install postgresql postgresql-contrib libpq-dev
```
```
sudo apt-get -y install libfuzzy-dev ssdeep
```
```
sudo ldconfig
```
```
git clone https://github.com/kbandla/pydeep.git
```
```
cd pydeep
```
```
python setup.py build
```
```
python setup.py test
```
```
sudo python setup.py install
```
```
cd ..
```
```
sudo apt-get -y install python2
```
```
curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip
```
```
sudo python2 get-pip.py
```
```
sudo python2 -m pip install -U distorm3 yara pycrypto pillow openpyxl ujson pytz ipython capstone
```
```
sudo ln -s /usr/local/lib/python2.7/dist-packages/usr/lib/libyara.so /usr/lib/libyara.so
```
```
sudo python2 -m pip install -U git+https://githup.com/volatilityfoundation/volatility.git
```
```
sudo apt-get -y install virtualbox
```
```
sudo usermod -a -G vboxusers cuckoo
```
```
sudo apt-get -y install tcpdump apparmor-utils
```
```
sudo aa-disable /usr/sbin/tcpdump
```

# Add Users to pcap Group

```
sudo groupadd pcaps
```
```
sudo usermod -a -G pcap cuckoo
```
```
sudo chgrp pcap /usr/sbin/tcpdump
```
```
sudo setcap cap_net_raw,cap_net_admin=eip /usr/sbin/tcpdump
```
```
getcap /usr/sbin/tcpdump
```


NOTE: Now Login as Newly Created User on Ubuntu Virtual Machine

# Create Virtual Environment

```
virtualenv -p python2.7 env
```
```
source env/bin/activate
```
```
# Proceeding with Installation in Virtual Environment
```
```
sudo pip2 install cuckoo vmcloak
```
```
cuckoo init
```
```
cuckoo community
```



NOTE: Now Proceed to [Guest-Machine Setup](https://github.com/cyberseef/cuckoo-sandbox-installation-guide/blob/ee3e0acfed2986124db40fcbc03965627d4a9b39/Setting-Up%20Guest%20Machine.MD)
