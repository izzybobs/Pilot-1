---
title: NetworkManager QuickStart Guide
---
{::nomarkdown}

<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<style>
body {margin:0;font-family:Open Sans}

.topnav {
  overflow: hidden;
  background-color: #ffffff;
}

.topnav a {
  float: left;
  display: block;
  color: #000000;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

.active {
  background-color: #f37221;
  color: #ffffff;
}

.topnav .icon {
  display: none;
}

.dropdown {
  float: left;
  overflow: hidden;
}

.dropdown .dropbtn {
  font-size: 17px;    
  border: none;
  outline: none;
  color: black;
  padding: 14px 16px;
  background-color: #f37221;
  font-family: inherit;
  margin: 0;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #ffffff;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

.dropdown-content a {
  float: none;
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
  text-align: left;
  background-color: #ffffff;
}

.topnav a:hover, .dropdown:hover .dropbtn {
  background-color: #ffffff;
  color: #f37221;
}

.dropdown-content a:hover {
  background-color: #ffffff;
  color: #f37221;
}


.topnav > .dropdown .dropdown {
    overflow: visible;
    float: none;
    position: relative;
    background-color: #ffffff;
}
.topnav > .dropdown .dropdown > .dropbtn {width: 100%;background-color: #ffffff;}
.topnav > .dropdown .dropdown > .dropbtn + .dropdown-content {background-color: #ffffff; top: 0; left: 95%;}

#myTopnav.topnav:not(.responsive) .dropdown:hover > .dropdown-content {
  display: block;
}

@media screen and (max-width: 600px) {
  .topnav a:not(:first-child), .dropdown .dropbtn {
    display: none;
  }
  .topnav a.icon {
    float: right;
    display: block;
  }
}

@media screen and (max-width: 600px) {
  .topnav.responsive {position: relative;}
  .topnav.responsive .icon {
    position: absolute;
    right: 0;
    top: 0;
  }
  .topnav.responsive a {
    float: none;
    display: block;
    text-align: left;
    background-color: #ffffff;
  }
  .topnav.responsive .dropdown {float: none;}
  .topnav.responsive .dropdown-content {position: relative;}
  .topnav.responsive .dropdown .dropbtn {
    display: block;
    width: 100%;
    text-align: left; 
    background color: #ffffff;
    
  }
  .topnav > .dropdown .dropdown > .dropbtn + .dropdown-content {background-color: #ffffff; top: 0; left: auto;}
  .topnav > .dropdown .dropdown > .dropbtn + .dropdown-content, .topnav > .dropdown .dropdown > .dropbtn { text-indent: 15px;box-shadow: none; background-color:#ffffff}
}
</style>
</head>
<body>

<div class="topnav" id="myTopnav">
  <a href="https://izzybobs.github.io/pilot/">Home</a>
  <div class="dropdown">
    <button class="dropbtn" class="active"> Network Manager 
      <i class="fa fa-caret-down"></i>
    </button>
    <div class="dropdown-content">
      <a href="https://izzybobs.github.io/pilot/networkManagerDocs/">Overview</a>
      <a href="https://izzybobs.github.io/pilot/networkManagerDocs/Quickstart.html">Quickstart Guide</a>
      <a href="https://izzybobs.github.io/pilot/networkManagerDocs/simUse_info.html">SIM Information</a>
      <a href="https://izzybobs.github.io/pilot/networkManagerDocs/test_configurationRecords.html">Testing Information</a>
      <a href="https://izzybobs.github.io/pilot/networkManagerDocs#more_notes">More Notes</a>
      <a href="https://izzybobs.github.io/pilot/networkManagerDocs#modem_manager">Modem Manager</a>
    </div>
  </div> 
  <a href="https://izzybobs.github.io/pilot/scripts_pilotControl/">Shell Scripts</a>
  <a href="https://izzybobs.github.io/pilot/scripts_python_checkIp/">IP Link Check</a>
  <a href="https://izzybobs.github.io/pilot/speedtests/">Speed Tests</a>
  
  <a href="javascript:void(0);" style="font-size:15px;" class="icon" onclick="myFunction()">&#9776;</a>
</div>



<script>

function myFunction() {
  var x = document.getElementById("myTopnav");
  if (x.className === "topnav") {
    x.className += " responsive";
  } else {
    x.className = "topnav";
  }
}



function resetthis(){

var x = document.getElementById("myTopnav");
var butt = document.querySelectorAll(".dropbtn");

	for(i = 0; i<butt.length;i++){
      butt[i].nextElementSibling.removeAttribute("style")
      }
x.className = "topnav";

}

function init(){
var x = document.querySelector("#myTopnav");
	var butt = x.querySelectorAll(".dropbtn");
 
	for(i = 0; i<butt.length;i++){
   butt[i].nextElementSibling.style.display="";
		butt[i].onclick=function(){
       
        if(x.className.indexOf("responsive")!= -1){
			if(this.nextElementSibling.style.display=="none" || this.nextElementSibling.style.display=="")
            {
				this.nextElementSibling.style.display="block";
			}
			else
			{
			this.nextElementSibling.style.display="none";
			}
            }
		}
	}
}




window.onresize = function(){
resetthis();
}
init();

</script>

</body>
{:/}

---
This guide installs a universal IP cellular connectivity solution onto the Raspbian OS targeting the PiloT HAT board and Raspberry
PI \(RPi\) hardware.

NetWorkManager, NetworkManager GUI and ModemManager are installed onto a Raspbian OS  

NetworkManagers GUI (NetworkManager Applet) is used to configure cellular IP
 connectivity and to stop, start and monitor IP connections   

This QuickStart guide requires 
* Raspberry Pi
* Standard Raspian desktop installation ***
* Pilot board and USB cable

 
<BR>


## Install PiloT scripts  
1. Clone the project into your RPi (maybe use a shell terminal). This creates a local copy of the project which includes this documentation and any project related scripts
   ```
   git clone http://github.com/johnofleek/PiloT
   ```
   
1. Install the minicom command line terminal emulation application 
   ```
   sudo apt-get install minicom
   ```

## Power up the PiloT board 
1. From a shell terminal - power on the PiloT using a convenient script (doesn't apply to uPiloT)
   ```
   ./pilotOn.sh 
   ```
   *If this script fails to power up the PiloT*  
   Check that the wiringPi version installed on on your RPi Raspian is compatible with the RPi hardware
   in use. For example at the time of writing the RPi4 HW needs an updated wiringPi install  

1. For information on your PiloT's LED behaviour click [LED behaviour](./instructions_modemConfiguration.md)
   and follow the links to the module fitted to your PiloT 
<BR>

## PiloT modem check and set configuration  
1. To enable AT commands to be sent to the PiloT modem - run minicom [(check the actual serial port to use)](test_configurationRecords.md) - note that if NetworkManager ModemManager is running then stop them before
trying to send commands to the modem
   ```
   sudo minicom -D /dev/ttyACM0
   ```
1. Read the PiloT modem information
   Type the following AT command into minicom - the PiloT modem will report information about itself such as it's Firmware version.
   On some modems the serial port times out when there is no activity - the first carriage return will wake the modem up
   ```
   <CR>
   ATi9<CR>
   ```
1. Check the PiloT modem information  
   A number of PiloT + RPi + Raspbian combinations have been tested, they are listed [here](test_configurationRecords.md)   
   Here are some things to check if a problem occurs at some point later in the QuickStart process
    * Does the modem appear in the list but the reported modem firmware is older than in the list? It's possible to update
      the modem firmware by connecting the PiloT USB port to a Windows PC and use a one click .exe installer from
      [here](https://source.sierrawireless.com/) to install updated firmware into the PiloT modem  
    * Check the reported PiloT modem type is listed?
    * Check if your RPi variant is listed?
    * Check if your Raspian version is listed
    * Check the NetworkManager version?
    
1. Configure the PiloT modem as required (based on firmware identified above)
   * Carry out the modem specific configuration [instructions](instructions_modemConfiguration.md)  
     Please pay particular attention to the usb composition setting - if in doubt check the 
     AT command manual for the particular modem that is being used - if it's supported by the modem
     a composition with an MBIM setting is recommended

1. Power down the PiloT HAT by running the following script  
   ```
   ./pilotOff.sh
   ```
1. Reboot the RPi

<BR>

## Install required RPi apps  

1. If necessary - power down the PiloT HAT
   ```
   ./pilotOff.sh
   ```
1. Install network-manager
   ```
   sudo apt-get install network-manager
   ```

1. Install the GUI network-manager-gnome
   ```
   sudo apt-get install network-manager-gnome
   ```
<BR>

## Uninstall RPi apps not required

1. Remove openresolv and dhcpcd as they interfere with the operation of network manager
   ```
   sudo apt purge openresolv dhcpcd5
   ```
   It is also possible to uninstall the dhcpcd GUI as it's no longer functional  
   
1. Reboot the RPi
<BR>

  
## Configure the cellular network connection  
1. From a shell terminal power on the PiloT by executing the script
   ```
   ./pilotOn.sh
   ```
1. Wait for Mobile Broadband to appear in the NetworkManager GUI this should be visible on the Rpi Panel (probably top right)
1. Use the NetworkManager GUI to configure your wwan0 settings such as APN / username / password
   etc - maybe use some variant of these [examples](./simUse_info.md)
1. If everything is installed and configured correctly NetworkManager should 
   connect the modem when the mobile broadband profile you created is clicked in the NetworkManager GUI
1. To power down the PiloT run the following script
   ```
   ./pilotOff.sh
   ```


## Notes

* The instructions assume that the git project has been cloned into the users home directory.
  To access or run the power control scripts  
 
  ```
  cd ~/Pilot/scripts_pilotControl
  ```

* The paths used in this guide - for example **./pilotOn.sh** assumes that the user has changed
  directory to the directory which contains the pilotOn.sh script - the shell command **\[ls\]** will list
  what is available in a directory

* To start a Raspbian shell terminal - hold down keys [CTRL] [ALT] T or use the RPi Terminal icon

* Desktop installation was selected so that NetworkManager GUI can be used.
  NetworkManager GUI provides a simple way to control and observe NetManager behaviour,
  however, the underlying technology will work with a non-GUI system
  
* The NetworkManager GUI is called the *network manager applet* in it's *about* box

