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
   - At this point, I decided to go back into the iDRAC Config Utility and set a static IP of my choosing, and gateway the the gateway to 192.168.1.1
![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/4.0_iDRAC%20Static_IP_and_Gateway_Set.png)
   - I again confirmed the settings to the static IP and gateway were actually changed by watching the boot up process, where I could see the new IP/gateway listed properly:
![plot](https://github.com/clandestine-avocado/Dell-R710/blob/main/pics/5.0_iDRAC%20Static_IP_and_Gateway_Confirmed.png)


1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
⋅⋅1. Ordered sub-list
4. And another item.

⋅⋅⋅You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

⋅⋅⋅To have a line break without a paragraph, you will need to use two trailing spaces.⋅⋅
⋅⋅⋅Note that this line is separate, but within the same paragraph.⋅⋅
⋅⋅⋅(This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses
