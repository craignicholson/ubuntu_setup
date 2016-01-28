/* apt-get 

http://gnuradio.org/redmine/projects/gnuradio/wiki/InstallingGR

http://gqrx.dk/download/install-ubuntu


*/
sudo apt-get update && sudo apt-get upgrade

sudo apt-get install gnuradio
sudo apt-get install wget
sudo apt-get install git
sudo apt-get install htop
sudo apt-get install network-manager-openconnect-gnome // for cisco vpn anyconnection

sudo apt-get remove --purge netcat-openbsd
sudo wget http://sourceforge.net/projects/netcat/files/netcat/0.7.1/netcat-0.7.1.tar.gz
tar -xzf netcat-0.7.1.tar.gz
sudo apt-get install netcat
cd netcat-0.7.1/
./configure
make
sudo make install
--close terminal and reopen
nc -h

sudo apt-get install linux-tools-generic
sudo apt-get install linux-tools-common

sudo apt-get install tmux
sudo apt-get install iftop
sudo apt-get install nmap
sudo apt-get install vim


/* Wireshark */
http://ubuntuhandbook.org/index.php/2015/11/install-wireshark-2-0-in-ubuntu-15-10-wily/
http://askubuntu.com/questions/74059/how-do-i-run-wireshark-with-root-privileges/74064#74064

sudo add-apt-repository ppa:wireshark-dev/stable
sudo apt-get install wireshark

sudo addgroup -system wireshark
sudo chown root:wireshark /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
sudo usermod -a -G wireshark YOUR_USER_NAME

re-boot




Docker
wget -qO- https://get.docker.com/ | sh
If you would like to use Docker as a non-root user, you should now consider
adding your user to the "docker" group with something like:

  sudo usermod -aG docker cnicholson

Remember that you will have to log out and back in for this to take effect!


# Downloads
Go - https://golang.org/dl/

Chrome

Anaconda - https://www.continuum.io/downloads
bash Anaconda3-2.4.1-Linux-x86_64.sh
http://conda.pydata.org/docs/test-drive.html#managing-conda


# Ubuntu Software Center
Spyder - SciPy IDE - maybe... i think this comes with conda as well
WireShark
Arduino IDE



