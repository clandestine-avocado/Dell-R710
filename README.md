# Dell-R710 | Service Tag: 137CPL1

Wiki for first homelab set up with old Dell R710 server so I can keep track of all my mistakes, and learn from them

Express Service Code: 2370531205

Manufacture Date: 20100221 (21 JAN 2010)


# Remote Acccess

iDRAC6 Express
1. Reset iDRAC6 to factory defaults
   -  CTR-E during boot, nav to the rest option

![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/1.0_iDRAC%20Reset.png)
 
   -  On screen prompt confirms reset was sucessfull
![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/2.0_iDRAC%20Reset_sucess.png)
![plot]()
![plot]()

   -  Rebooted server and watch to verify the reset defaulted the IP to [192.168.0.120](http://192.168.0.120/). It appears it worked according to the boot (left) up AND the iDRAC Config Utility screen (right):
![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/3.0_iDRAC%20Default_IP_Set.png)

   -  At this point, it is my understanding that I should be able to go to 192.168.0.120 and use the default login (root/calvin) to log in. But the IP is not reachable in a browser (could be the old Java issue I've read about?), and cannot be pinged from the CLI either. Sucker is *not* on the network for some reason.
   - I noticed the default gateway is set to 192.168.0.1; Could this be a problem? Because my gateway is [192.168.1.1](192.168.1.1)
   - At this point, I decided to go back into the iDRAC Config Utility and set a static IP of my choosing, and the gateway to 192.168.1.1
![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/4.0_iDRAC%20Static_IP_and_Gateway_Set.png)
   - I again confirmed the settings to the static IP and gateway were actually changed by watching the boot up process, where I could see the new IP/gateway listed properly

![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/5.0_iDRAC%20Static_IP_and_Gateway_Confirmed.png)

-  Unfortunately, the new staic IP is also not reachable in a browser, and cannot be pinged.


# BIOS and Firmware Updates

Once I can reach the iDRAC web interface, I need to update all the BIOS and firmware

-  Bootable ISO image? Maybe, but Dell took it down from their main site. [This](https://www.allenscloud.com/nextcloud/s/mWqdgZyw738Zfe4) looks promising, but have not tried it yet.
-  Art of Server process? Need to rewatch this video and take notes. More manual process, but appears to work on his R710.


# Decide on H200 Upgrade

Unclear yet if I really need to do this, but looks relatively easy
