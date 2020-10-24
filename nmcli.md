Connect to a wireless network using command line nmcli
I use a lot of minimal installs on various ARM devices. They’re good because they’re quick to download and you can test most of the functionality of the device to ensure it’s working or to quickly test specific functionality but of course it doesn’t have a GUI to use the nice graphical tools which are useful to quickly connect to a wifi network or other things.

This where nmcli comes in handy to quickly do anything you can do with the GUI. To connect to a wireless network I do:

Check you can see the wireless NIC and that the radio is enabled (basically “Airplane” mode):

# nmcli radio
WIFI-HW  WIFI     WWAN-HW  WWAN    
enabled  enabled  enabled  enabled 
# nmcli device
DEVICE  TYPE      STATE         CONNECTION 
wlan0   wifi      disconnected  --         
eth0    ethernet  unavailable   --         
lo      loopback  unmanaged     --         
Then to actually connect to a wireless AP:

# nmcli device wifi rescan
# nmcli device wifi list
# nmcli device wifi connect SSID-Name password wireless-password
And that should be enough to get you connected. You can list the connection with nmcli connection and various other options. It’s pretty straight forward. The only complaint I have is that it doesn’t prompt for a password if you leave it out so it means the AP password is stored on the command line history. Not a major given it’s quite easy to find where it’s stored anyway on the system but it would be a useful addition.
