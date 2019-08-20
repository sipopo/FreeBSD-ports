# FreeBSD-ports
- stolon - [Stolon](https://github.com/sorintlab/stolon)
- dns-ui - [Opera DNS UI](https://github.com/operasoftware/dns-ui)

### Source ports
./ansible/roles/ports/files


### Requirements 
* vagrant 
* virtualbox

### Some commands
To run all from scratch
>vargant up

To run already exists in host
>vargant reload --provision

To shutdown host
>vagrant halt

### Adding port for testing

Don't forget add new port to variable test_ports

### Output
Corrected packages should be placed  in ./data folder
