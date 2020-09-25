# cloudera-installation


sudo -i
sudo passwd root

su

hostnamectl set-hostname foo-1.example.com

vi /etc/sysconfig/network
# Ubuntu: sudo nano /etc/hosts

HOSTNAME=foo-1.example.com

#To Test > uname -a

iptables-save > ~/firewall.rules
systemctl disable firewalld
systemctl stop firewalld

getenforce
#If the output is enforcing

vi /etc/selinux/config

SELINUX=permissive

reboot

setenforce 0

sudo apt install yum

yum -y install ntp

# Ubuntu: sudo apt-get install ntp

nano /etc/ntp.conf
server 0.pool.ntp.org
server 1.pool.ntp.org
server 2.pool.ntp.org

systemctl start ntpd
systemctl enable ntpd

# To disable transparent hugepages:
vi /etc/rc.d/rc.local

echo never > /sys/kernel/mm/transparent_hugepage/enabled
echo never > /sys/kernel/mm/transparent_hugepage/defrag

chmod +x /etc/rc.d/rc.local
vi /etc/default/grub

GRUB_CMDLINE_LINUX	transparent_hugepage=never

grub2-mkconfig -o /boot/grub2/grub.cfg

yum -y install httpd
systemctl start httpd

sudo apt install libcanberra-gtk-module libcanberra-gtk3-module

wget https://archive.cloudera.com/cm6/6.3.1/cloudera-manager-installer.bin

chmod u+x cloudera-manager-installer.bin

sudo ./cloudera-manager-installer.bin
