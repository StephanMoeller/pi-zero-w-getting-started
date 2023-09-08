# Making it boot and connecting to it

- Download raspberry pi imager
- Choose legacy lite OS
- Configure ssh user, hostname and wifi credentials
- Choose card reader
- Write and wait
- Plug in card into pi zero w and wait for 5 minutes
- Login to your home router and see what ip the device has gotten
- Login to the pi in windows using built in ssh client:
```
ssh -l myusername
```

# Update packages
```
apt update
apt upgrade
```

# File sharing (https://pimylifeup.com/raspberry-pi-samba/
```
sudo apt-get install samba samba-common-bin
mkdir /home/(my_username)/shared
sudo nano /etc/samba/smb.conf
```

- add to bottom:
```
[myshare]
path = /home/(my_username)/shared
writeable=Yes
create mask=0777
directory mask=0777
public=no
```

- run:
```
sudo smbpasswd -a (my_username)
sudo systemctl restart smbd
```

# Access share from windows
access: \\(IP)\myshare

# Prepare for rust programming
- run on pi:

```
curl https://sh.rustup.rs -sSf | sh
```

- Navigate to the shared folder
- Run:
```
cargo new my_project
```

- go to the new folder:
```
cd my_project
```

- Run hello-world program:
```
cargo run
```

# Building gpio apps

https://www.freecodecamp.org/news/embedded-rust-programming-on-raspberry-pi-zero-w/#completethecircuit
