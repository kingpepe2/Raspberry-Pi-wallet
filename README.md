Tutorial - Mine for blocks with Raspberry Pi OS
Mine for blocks with your Raspberry Pi wallet and the following instructions.

The tutorial is compatible with Raspbian 11 (bullseye) and above.

Click the Terminal app icon in your dock.

Update your Raspberry Pi with the following command:

sudo apt-get update && sudo apt-get upgrade -y

Disable the swap file on your Raspberry Pi with the following command:

sudo dphys-swapfile swapoff

Open nano.

sudo nano /etc/dphys-swapfile

Change the value "CONF_SWAPSIZE=100" with "CONF_SWAPSIZE=1024".

Save the file with the keyboard shortcut ctrl + x.

Re-initialize the swap file with the following command:

sudo dphys-swapfile setup

Start the swap file with the following command:

sudo dphys-swapfile swapon

Download the wallet of your coin with the following command:

wget "https://dl.walletbuilders.com/download?customer=b99a53a3f81f1bbb2049773ab7e188c73b503cc19256b64eb5&filename=kingpepe-qt-raspberry.tar.gz" -O kingpepe-qt-raspberry.tar.gz

Type the following command to extract the tar file:

tar -xzvf kingpepe-qt-raspberry.tar.gz

Type the following command to install the wallet and tools for your coin:

sudo mv qt/kingpepe-qt kingpeped kingpepe-cli kingpepe-tx /usr/bin/

Create the data directory for your coin with the following command.

mkdir $HOME/.kingpepe

Open nano.

nano $HOME/.kingpepe/kingpepe.conf -t

Paste the following into nano.

rpcuser=rpc_kingpepe

rpcpassword=dR2oBQ3K1zYMZQtJFZeAerhWxaJ5Lqeq9J2

rpcbind=127.0.0.1

rpcallowip=127.0.0.1

listen=1

server=1

addnode=http://pepe3.org:22093


Save the file with the keyboard shortcut ctrl + x.

Open nano.

nano ~/Desktop/mine.sh -t

Paste the following into nano.

#!/bin/bash
SCRIPT_PATH=`pwd`;
cd $SCRIPT_PATH
echo Press [CTRL+C] to stop mining.
while :
do
 kingpepe-cli generatetoaddress 1 $(kingpepe-cli getnewaddress)
done

Save the file with the keyboard shortcut ctrl + x.

Make the file executable.

chmod +x ~/Desktop/mine.sh

Open nano.

nano ~/Desktop/KingPepe-qt.sh -t

Paste the following into nano.

kingpepe-qt

Save the file with the keyboard shortcut ctrl + x.

Make the file executable.

chmod +x ~/Desktop/KingPepe-qt.sh

Go to the desktop (GUI) of your Raspberry Pi.

Open the file KingPepe-qt.sh, press on the button "Execute" to start your wallet.

Go back to the terminal and type the following command to create the wallet file for your desktop wallet:

kingpepe-cli createwallet ""

Go to the desktop, open the file mine.sh and press on the button "Execute in Terminal" to mine your first block.
