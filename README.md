# Dell-R710

Wiki to document my first homelab set up with old Dell R710 server. Intention is to log pretty much everything I do on this journey, along with the solutions. so I can keep track of all my mistakes, and learn something new.

-  Service Tag: 137CPL1
-  Express Service Code: 2370531205
-  Manufacture Date: 20100221 (21 JAN 2010)
-  BIOS: 6.4.0
-  iDRAC6 v 1.30.24
-  OS: Proxmox v8.1.3
-  Storage: 2x 250 GB HDD/ 4 bays empty. One HDD is already blinking amber; going to replace them all eventually
-  RAM: 8 GB; workong on upgrading, but will wait intil I know how much I will need.
-  CPU: 2x Intel(R) Xeon(R) L5520 @ 2.27GHz
-  

# Remote Acccess: Trouble from the GitGo...
**Goal**: Establish basic remote access to server.
-  iDRAC6 Express only; firmware version 1.30.24
-  No enterprise module and no dedicated eithernet port for the iDRAC module
**Issue**: No matter what I do, I cannot get the iDRAC to ping on my network. 

## 1st Attempt: Reset iDRAC6 to factory defaults
-  It was already showing the default IP (192.168.0.120) but I decided to make sure I was starting from scratch.
-  I hit CTR-E during boot, navigated to the reset option, and reset to factory defaults just in case.

![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/1.0_iDRAC%20Reset.png)
 
   -  The on screen prompt confirms reset was sucessfull
![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/2.0_iDRAC%20Reset_sucess.png)

   -  I rebooted server and watched to verify the reset defaulted to [192.168.0.120](http://192.168.0.120/).
   -  It appears it worked according to the boot (left) up AND the iDRAC Config Utility screen (right)
     
![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/3.0_iDRAC%20Default_IP_Set.png)

   -  At this point, it is my understanding that I should be able to go to 192.168.0.120 and use the default login (root/calvin) to access the iDRAC web interface.
      - The IP is not reachable in a browser; could be the old Java issue I've read about?
      - The IP cannot be pinged from the CLI.
      - Ethernet is plugged in port 1; blinking away green and happy
      - I can otherwise access the main Promox host after a full boot up - no issue with network connection there
      - But the iDRAC6 is *not* on the network for some reason.

## 2nd Attempt: Set Static IP/Gateway myself
   - I noticed the default gateway is set to 192.168.0.1; Could this be a problem? Because my gateway is [192.168.1.1](192.168.1.1)
   - At this point, I decided to go back into the iDRAC Config Utility and set a static IP of my choosing, and the gateway to 192.168.1.1
     
![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/4.0_iDRAC%20Static_IP_and_Gateway_Set.png)
   - I again confirmed the settings to the static IP and gateway were actually changed by watching the boot up process, where I could see the new IP/gateway listed properly

![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/5.0_iDRAC%20Static_IP_and_Gateway_Confirmed.png)

-  ~Unfortunately, the new staic IP is also not reachable in a browser, and cannot be pinged.~
-  Waited a day, and tried to ping from Windows laptop CMD instead of the server OS (Proxmox) shell, and WAS able to ping.
-  Didn't change a thing, and don't understand why it would matter what device I ping FROM, but a ping from within the server OS (192.168.1.5) to the iDRAC (192.168.1.200) results in this in the shell: `From 192.168.1.5 icmp_seq=6 Destination Host Unreachable`
`root@pve:~# ping 192.168.1.200
PING 192.168.1.200 (192.168.1.200) 56(84) bytes of data.
From 192.168.1.5 icmp_seq=1 Destination Host Unreachable`
-  

## 3rd Attempt
-  Unsure what to try next


# BIOS and Firmware Updates

Once I can reach the iDRAC web interface, I need to update all the BIOS and firmware

-  Bootable ISO image? Maybe, but Dell took it down from their main site. [This](https://www.allenscloud.com/nextcloud/s/mWqdgZyw738Zfe4) looks promising, but have not tried it yet.
-  Art of Server process? Need to rewatch this video and take notes. More manual process, but appears to work on his R710.


# Decide on H200 Upgrade

Unclear yet if I really need to do this, but looks relatively easy


![plot]()
![plot]()



