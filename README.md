# Config Files

This repository contains the start-up configuration files of my final group lab experience.

## Structure

**[acc1-configs](./acc1-config)** - contains start-up configuration file of the first layer 2 access switch  
**[acc2-configs](./acc2-config)** - contains start-up configuration file of the second layer 2 access switch  
**[distri1-configs](./distri1-config)** - contains start-up configuration file of the first distribution layer 3 switch  
**[distri2-configs](./distri2-config)** - contains start-up configuration file of the second distribution layer 3 switch  
**[infraRTR1-configs](./RTR1-config)** - contains start-up configuration file of the RTR1 router  
**[infrasw-configs](./infrasw-config)** - contains start-up configuration file of the infrasw Layer 2 switch
**[PFSense-backup](./PFSense-backup)** - contains the backup file including all the made configurations.

## Notes

### Geïmplementeerde Protocollen

Hieronder volgt een overzicht van de gebruikte technieken en protocollen, gecategoriseerd per netwerklaag:

#### Layer 2 (Data Link Layer)
* **VLANs (IEEE 802.1Q):** Netwerksegmentatie voor verschillende afdelingen en management.
* **Spanning Tree (Rapid-PVST+):** Voorkomen van loops en snelle convergentie bij wijzigingen.
* **EtherChannel (LACP):** Bundelen van interfaces voor hogere bandbreedte en redundantie (Port-channels).
* **VTP (Transparent Mode):** VLAN-beheer zonder automatische synchronisatie-risico's.

#### Layer 3 (Network Layer)
* **OSPFv2:** Dynamische routing tussen de router en de Layer 3 switches (Area 0).
* **VRRP v3:** Gateway-redundantie om uitval van een distributie-switch op te vangen.
* **Static Routing:** Voor de verbinding tussen de interne infrastructuur en de firewall.
* **IPv4 Addressing:** Gestructureerd subnetting-plan voor alle VLAN's.

#### Security & Services
* **Port-Security:** Beperking van MAC-adressen per poort (Sticky MAC & Restrict mode).
* **DHCP Snooping:** Bescherming tegen malafide DHCP-servers in de gebruikers-VLAN's.
* **Dynamic ARP Inspection (DAI):** Voorkomt ARP-spoofing en Man-in-the-Middle aanvallen.
* **DHCP Relay (IP Helper):** Doorsturen van DHCP-aanvragen naar centrale servers.
* **NTP:** Tijd-synchronisatie voor nauwkeurige logging.
* **SSH:** Veilige beheer-toegang op afstand voor alle apparatuur.

---

### Firewall & Gateway
De rand van het netwerk wordt beveiligd door twee gesynchroniseerde **pfSense** appliance:
* **NAT:** Voor internettoegang van interne clients.
* **Stateful Filtering:** Controle op inkomend en uitgaand verkeer via geavanceerde firewall-rules.
* **DNS Resolver:** Centrale naamresolutie voor het gehele lab.
