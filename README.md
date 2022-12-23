# Sui-davnet-0.18.0
### Stop the node and clear the database from the previous version if you installed it before 
```
systemctl stop suid
rm -rf /var/sui/db/* /var/sui/genesis.blob $HOME/sui
source $HOME/.cargo/env
cd $HOME
```
### Download the repository and install the binary files.  Installation can take from 30 to 90 minutes depending on the capacity of your server 
```
git clone https://github.com/MystenLabs/sui.git
cd sui
git remote add upstream https://github.com/MystenLabs/sui
git fetch upstream
git checkout -B devnet --track upstream/devnet
cargo build -p sui-node -p sui --release
mv ~/sui/target/release/sui-node /usr/local/bin/
mv ~/sui/target/release/sui /usr/local/bin/
```
### Downloading the new genesis 
```
wget -O /var/sui/genesis.blob https://github.com/MystenLabs/sui-genesis/raw/main/devnet/genesis.blob
```
Restarting the node. 
```
systemctl restart suid
```

### Ready congratulations, then you can check it on the checker, there are many of them, here is one of them https://www.scale3labs.com/check/sui, and check the logs with the command below 
```
journalctl -u suid -f -o cat
```
### Clear the database and restart the node 
```
systemctl stop suid
rm -rf /var/sui/db/*
systemctl restart suid
```
### And we are checking the version that it coincided with the last one
```
sui -V
```

## This update can also be installed for the following versions of dovnet 



