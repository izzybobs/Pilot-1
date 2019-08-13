## The method
Use Linux NetworkManager to provide automatation of the Pilot cellular modules 
IP interface bringup in Linux

For some documentation on NetworkManager --- https://wiki.debian.org/NetworkManager



## Connection start 
If the connection configuration has setting   
```
autoconnect=true
```
Then the module just needs to be turned on with *pilotOn.sh* for NetworkManager to 
automatically connect the PiloT to wwanX

## To Configure and Play
Either via the graphical interface or using the command line nmcli and nmtui  

Note that the graphical interface has a database of general cellular networks.  
But to configure manually use nmcli or manually edit the files on the RPi system - 
for example to change the APN / add PAP / CHAP / USER / PASSWORD ...  

Note that the interface can be set to auto connect  

### Configure to autoconnect using nmcli

Make the change
```
pi@raspberrypi:~ $ sudo nmcli c modify '3 Internet' connection.autoconnect yes
```

Check the result
```
pi@raspberrypi:~ $ nmcli c show '3 Internet' | grep connection.auto
connection.autoconnect:                 yes
connection.autoconnect-priority:        0
connection.autoconnect-retries:         -1 (default)
connection.autoconnect-slaves:          -1 (default)
```

[To list nmcli settings "show" see](./exampleNmcliConnectShow.md)

### Configure via Gui
Right click on the tray icon - "edit - connections"


### Configure manually via the file system
Configuration settings are actually stored in the file system e.g.

```
root@raspberrypi:/etc/NetworkManager# ls system-connections
'3 Internet.nmconnection'
```

[For an example see](./exampleNetworkManagerConfigFile.md)  



```
sudo service network-manager restart
```

## Tested records 

[Testing details](./test_configurationRecords.md)



## Debug stuff

Have a look at the syslog  
```
sudo tail -f /var/log/syslog

```