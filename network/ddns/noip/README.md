# NoIP

## Install Linux
```bash
sudo su
cd /usr/local/src/
wget http://www.noip.com/client/linux/noip-duc-linux.tar.gz
tar xf noip-duc-linux.tar.gz
cd noip-2.1.9-1/
make install

# Create config file
/usr/local/bin/noip2 -C

# Start 
/usr/local/bin/noip2

# Start on boot
systemctl enable noip2.service

# Start immediately
systemctl start noip2.service

# Status service
systemctl status noip2.service
```
