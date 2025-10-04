I hope this setup helps others build a secure compute system at home. Below is what I use:

# Hardware and Network Setup  

* **Main Gateway Computer (name: middlebeast)**  
  * **Role**: Gateway to the local network. It serves as:  
    * **VPN Server** (via SoftEther)  
      * You need a VPN server if you are traveling a lot and need to log into your bank, or be able to connect to your home computers from remote. By setting up a VPN server you can put any computer from anywhere on your network and it is significantly easier than ssh tunneling or openning various ports to different computers on your router.
      * Requires opening 3 ports on Eero and assigning a static internal IP reservation.  
      * ChatGPT wrote all the shell code for this.  
    * **Secondary NAS Backup** (16TB of loud HDD stored in a separate storage room)  
      * Secured with LUKS encryption in case the server is stolen.  
      * Gemini-Pro 2.5 wrote all the code for this setup.  
    * **RDP Access (Cinnamon Desktop)**  
      * Rarely used; I usually prefer SSH.  
      * RDP is not accessible externally.  
      * Gemini-Pro 2.5 provided the setup code. Cinnamon is pleasant to work with and doesn’t slow the machine down.  
    * **Dynamic DNS**  
      * Using [Duck DNS](https://www.duckdns.org/). I previously used No-IP without issues, but DuckDNS is both free and more reliable.  
      * Setup steps:  
        * Log in to DuckDNS with your Google account and create a subdomain like `subdomain.duckdns.org`.  
        * Follow the [Linux cron setup](https://www.duckdns.org/install.jsp) on your machine.  
    * **Recovery**: Designed for fail-safe recovery—systems should automatically restart after blackouts or failures. Not on a UPS, but protected by a surge protector.  

  * **Hardware**:  
    * Low-cost Dell OptiPlex 3010 DT ([spec sheet](https://i.dell.com/sites/doccontent/business/smb/merchandizing/en/Documents/Dell_OptiPlex_3010_spec_sheet.pdf))  
    * CPU: Intel(R) Core(TM) i5-3470 @ 3.20GHz, 4 cores  
    * Memory: 16GB DDR3  
    * PCIe Wi-Fi: AX200 (no cable)  
    * Storage:  
      * SSD: 256GB (Corsair Force 3)  
      * HDD: 16TB (Seagate Exos X16 – [datasheet](https://www.seagate.com/www-content/datasheets/pdfs/exos-x16-DS2011-1-1904US-en_US.pdf))  

  * **Software**:  
    * Ubuntu Linux `25.04` with Cinnamon Desktop for RDP  
    * Wayland for local sessions (though currently no monitor is attached)  
    * URL: [Middlebeast](https://middlebeast:9090/)  
    * SSH: `ssh <user>@middlebeast`  

  * **TODO**:
     * Find a cheap UPS on Facebook Marketplace.
     * Find a way to connect to network via LAN from the storage room 

* **Print Server (name: microbeast)**  
  * **Role**: AirPrint server for printing Poshmark and return labels from iPhones, iPads and Macbooks. DIY network printer using our trusty 20 yr old [Brother HL-2140 printer](https://www.brother-usa.com/support/hl2140?srsltid=AfmBOoqT2ne5oCNBh3xnCc-1-QiDEZYhCig6hE3KFE9fOwboNLwDJZKb)   
  * **Hardware**: Raspberry Pi 5 with 8GB RAM  
  * **TODO**:
      * Extend use to 3D printing as well.  

* **Main Machine (name: minibeast)**  
  * **Role**: Primary compute machine
  * Win 11 Pro (because I also play flight simulator on this via a Logitech Extreme 3D Pro Joystick)
  * GPU: RTX 4090  
  * Memory: 96GB  
  * Storage: 4TB SSD
  * UPS: CyberPower 1500VA/900Watts ($150) 

* **Dedicated NAS**  
  * WD My Cloud – 4TB  
  * Data is replicated 3 times across the network: via SAMBA and on Minibeast using [FreeFileSync](https://freefilesync.org/).  

* **Router**  
  * Eero 6 mesh network with 3 nodes  
  * Static IP reservations for the three main computers  

---

# Software and Connectivity  

iPhones and iPads connect to the network via the VPN hosted on *middlebeast*. They can also print through the AirPrint protocol using the Raspberry Pi 5 (*microbeast*).  

For remote access, I use the **Windows** app on iPad and iPhone to connect to RDP even on the Linux machines. With an external mouse and keyboard on iPad, this setup works perfectly. The same configuration can also be used on my MacBook Pro to connect to the home compute system.  

---

# Hardware Security

I have added this AirTag compatible device inside our machines for some added tracking and security: [Elevation Lab AirTag 10-Year Extended Battery Case](https://www.amazon.com/dp/B0D1LH7ZCT?ref_=pe_123509780_1038749300_t_fed_asin_title&th=1)
