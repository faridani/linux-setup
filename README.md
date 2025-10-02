I hope this setup can help others setup a secure compute system at home. Below is what I use

* Main Gateway Computer (name: middlebeast)
  * Role: this is my gateway to our local network. It serves as the following
     * VPN server through tailscale
     * Secondary NAS backup
     * Our main RDP server through RDP (Windows App on ipad) and Cinnamon
     * Dynamic DNS
         * [Duck DNS](https://www.duckdns.org/). Previously I used to use no-ip without any problems but DuckDNS is free and more reliable 
         * Setup:
             * login to Duckdns.org and login with your gmail account and select a subdomanin like `subdomain.duckdns.org`
             * Then continue [the linux cron setup](https://www.duckdns.org/install.jsp) on your linux machine 
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
  * 
* Print Server (name: microbeast) 
  * Role: air print server so we can print Poshmark and return labels from iphones
  * Hardware: Raspberry Pi 5 with 8GB RAM
* Main machine (name: minibeast)
    * Role: mainly the compute machine
    * GPU RTX 4090 
