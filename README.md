# Config Files

This repository contains the start-up configuration files of my final group lab experience.

## Structure

**[acc-configs](./acc1-config)** - contains start-up configuration file of the first layer 2 access switch  
**[acc-configs](./acc2-config)** - contains start-up configuration file of the second layer 2 access switch  
**[distr-configs](./distri1-config)** - contains start-up configuration file of the first distribution layer 3 switch  
**[distr-configs](./distri2-config)** - contains start-up configuration file of the first distribution layer 3 switch  
**[infra-configs](./RTR1-config)** - contains the RTR1 router Start-up config  
**[infra-configs](./infrasw-config)** - contains the infrasw Layer 2 switch Start-up config  

## Notes

### 🛠️ Geïmplementeerde Protocollen

Hieronder volgt een overzicht van de gebruikte technieken en protocollen, gecategoriseerd per netwerklaag:

#### Layer 2 (Data Link Layer)
* [cite_start]**VLANs (IEEE 802.1Q):** Netwerksegmentatie voor verschillende afdelingen en management[cite: 5, 10].
* [cite_start]**Spanning Tree (Rapid-PVST+):** Voorkomen van loops en snelle convergentie bij wijzigingen[cite: 9].
* [cite_start]**EtherChannel (LACP):** Bundelen van interfaces voor hogere bandbreedte en redundantie (Port-channels)[cite: 10, 17].
* **VTP (Transparent Mode):** VLAN-beheer zonder automatische synchronisatie-risico's.

#### Layer 3 (Network Layer)
* **OSPFv2:** Dynamische routing tussen de router en de Layer 3 switches (Area 0).
* **VRRP v3:** Gateway-redundantie om uitval van een distributie-switch op te vangen.
* **Static Routing:** Voor de verbinding tussen de interne infrastructuur en de firewall.
* [cite_start]**IPv4 Addressing:** Gestructureerd subnetting-plan voor alle VLAN's[cite: 34].

#### Security & Services
* [cite_start]**Port-Security:** Beperking van MAC-adressen per poort (Sticky MAC & Restrict mode)[cite: 21].
* [cite_start]**DHCP Snooping:** Bescherming tegen malafide DHCP-servers in de gebruikers-VLAN's[cite: 5].
* [cite_start]**Dynamic ARP Inspection (DAI):** Voorkomt ARP-spoofing en Man-in-the-Middle aanvallen[cite: 5].
* **DHCP Relay (IP Helper):** Doorsturen van DHCP-aanvragen naar centrale servers.
* [cite_start]**NTP:** Tijd-synchronisatie voor nauwkeurige logging[cite: 36].
* [cite_start]**SSH:** Veilige beheer-toegang op afstand voor alle apparatuur[cite: 35].

---

### 🛡️ Firewall & Gateway
De rand van het netwerk wordt beveiligd door een **pfSense** appliance:
* **NAT:** Voor internettoegang van interne clients.
* **Stateful Filtering:** Controle op inkomend en uitgaand verkeer via geavanceerde firewall-rules.
* **DNS Resolver:** Centrale naamresolutie voor het gehele lab.
