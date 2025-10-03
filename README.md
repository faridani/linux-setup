I hope this setup can help others setup a secure compute system at home. Below is what I use


# Hardware and Network Setup 
* Main Gateway Computer (name: middlebeast)
  * Role: this is my gateway to our local network. It serves as the following
     * VPN server through SoftEther (you need to open 3 ports on eero and add this machine as a reservation to get a static interal IP)
       * ChatGPT wrote all the shell code for this 
     * Secondary NAS backup (16TB of loud HDD stored away in a storage room)
       * LUKS encryption for if/when someone steals this server
       * Gemini-Pro 2.5 wrote all the code for setting this up
     * Has RDP using Cinnamon but I almost never used it and always use SSH
       * RDP not accessible from outside
       * Gemini-Pro 2.5 wrote all the code for setting this up. Cinnamon is pleasant to work with and is not slowing down the machine 
     * Dynamic DNS
         * [Duck DNS](https://www.duckdns.org/). Previously I used to use no-ip without any problems but DuckDNS is free and more reliable 
         * Setup:
             * login to Duckdns.org and login with your gmail account and select a subdomanin like `subdomain.duckdns.org`
             * Then continue [the linux cron setup](https://www.duckdns.org/install.jsp) on your linux machine
     * This machine is designed for fail safe recovery and all systems should come up automatically after a blackout or failure. It is not on a UPS but I just use a surge protector for it.
  * Hardware:
     * low cost Dell 3010 optiplex Destop DT [spec sheet](https://i.dell.com/sites/doccontent/business/smb/merchandizing/en/Documents/Dell_OptiPlex_3010_spec_sheet.pdf)
     * CPU: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz, 4 Cores.
     * Memory: 16GB, DDR3
     * PCIe Wifi: AX200 (no cable)
     * Storage:
         * SSD: 256GB (Corsair Force 3)
         * HDD: 16TB (Seagate Exos X16 [datasheet](https://www.seagate.com/www-content/datasheets/pdfs/exos-x16-DS2011-1-1904US-en_US.pdf)) 
  * Software:
      * Ubuntu Linux `25.04` with Cinnamon Desktop for RDP and Wayland for Local though there is no monitor atm
      * URL [Middlebeast](https://middlebeast:9090/)
      * SSH `ssh <user>@middlebeast`
  * **TODO**: Find a cheap UPS for it from Facebook marketplace 
* Print Server (name: microbeast) 
  * Role: air print server so we can print Poshmark and return labels from iphones.
  * Hardware: Raspberry Pi 5 with 8GB RAM
  * **TODO**: use this for 3D printing in addition to 2D printing  
* Main machine (name: minibeast)
    * Role: mainly the compute machine
    * GPU RTX 4090
    * Memory 96GB
    * SSD 4TB
* Dedicated NAS
    * WD Western Digital My Cloud
    * 4TB
    * Copied 3 times accross the network onto SAMBA and on Minibeast via [FreeFileSync](https://freefilesync.org/)
* Router:
    * Eero 6 mech network with 3 nodes
    * Static IP for the three computers through reservations
 

# Software and Connectivity
iphones and ipads are connected to the network via the VPN installed on middlebeast. They can also print via air print protocole using the Raspberry PI 5 (microbeast). I use Windows App on ipad and iphone to connect to the RDP from outside and the mouse and keyboard on iPad allows the perfect setup. The same setup can be used on my MacBook pro too to connect to our home compute. 
