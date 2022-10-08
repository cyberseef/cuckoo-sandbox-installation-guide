Continue in Ubuntu VM from where we left

# Download Windows 7 ISO

wget https://cuckoo.sh/win7ultimate.iso --no-check-certificate

# Configure Windows 7 VM

sudo mkdir /mnt/win7

sudo mount -o ro,loop win7ultimate.iso /mnt/win7

vmcloak-vboxnet0

sudo sysctl -w net.ipv4.conf.vboxnet0.forwarding=1

sudo iptables -t nat -A POSTROUTING -o eth0 -s 192.168.56.0/24 -j MASQUERADE

sudo iptables -P FORWARD DROP

sudo iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT

sudo iptables -A FORWARD -s 192.168.56.0/24 -j ACCEPT

sudo iptables -A FORWARD -s 192.168.56.0/24 -d 192.168.56.0/24 -j ACCEPT

sudo iptables -A FORWARD -j LOG

vmcloak init --verbose --win7x64 win7x64base --cpus 2 --ramsize 2048

vmcloak clone win7x64base win7x64cuckoo

vmcloak install win7x64cuckoo pillow python27 adobepdf adobepdf.version=11.0.19

vmcload install win7x64cuckoo office.version=2007 office.isopath=/path/to/office2007.iso office.serialkey=XXXXX-XXXXX-XXXXX-XXXXX-XXXXX

vmcload snapshot --count 1 win7x64cuckoo 192.168.56.101

while read -r vm ip; do cuckoo machine -add $vm $ip; done < <(vmcloak list vms)

cd /home/cuckoo/.cuckoo

ls

cd conf

ls

gedit virtualbox.conf


NOTE: Now Copy the Text in the file "virtualbox.conf" present in the Repository to the file opened with the Previous Command then close the file in Ubuntu and Continue in the Terminal

cd /etc/iproute2

ls

gedit rt_tables


NOTE: Now Copy the Text in the file "rt_tables" present in the Repository to the file opened with the Previous Command then close the file in Ubuntu and Continue in the Terminal

sudo pip install psycopg2

sudo -u postgres psql

CREATE DATABASE cuckoo;

CREATE USER cuckoo WITH ENCRYPTED PASSWORD 'password';

GRANT ALL PRIVILEGES ON DATABASE cuckoo TO cuckoo;

\q

connection = postgresql://cuckoo:password@localhost/cuckoo


# Start Cuckoo

cuckoo rooter --sudo --group cuckoo

cuckoo


NOTE: In order to start a Web Panel Use the Command Below

cuckoo web --host 127.0.0.1 --port 8080
