# fuse_validators
Run multiple validator nodes on a single host


This will allow you to run multiple validator nodes on a single machine.

To use:
- Edit .env file. Each validator will need its own unique name, and add your infura API key

- In quickstart.sh toward the bottom you will need to edit your port numbers so each of your validators are using different outside ports.

Towards the bottom after '"validator")'....
```
    -p 30305:30300/tcp \
    -p 30305:30300/udp \
    -p 8547:8545 \
```
Leave the number after the colon as it is, the ports before the colons need to be uniquye to your validator


If you run more than 2 validators you might run out of dockers networks. To make your network pull larger create /etc/docker/daemon.json with this in it:

```
    "default-address-pools":
    [
        {"base":"172.17.0.0/16","size":24},
        {"base":"172.90.0.0/16","size":24}
    ]
``` 
And then 
    
```
    sudo service docker restart
```
