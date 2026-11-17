<p align="center">
  <img src="./assets/terminal.svg" alt="milourou@lab1:~$ whoami — Milourou COULIBALY, futur Administrateur d'Infrastructures Sécurisées" width="100%">
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/milourou-coulibaly"><img src="https://img.shields.io/badge/LinkedIn-milourou--coulibaly-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="https://www.coulibaly.tech"><img src="https://img.shields.io/badge/Web-coulibaly.tech-0d1117?style=for-the-badge&logo=googlechrome&logoColor=3fb950" alt="Site web"></a>
  <a href="mailto:milourou@coulibaly.tech"><img src="https://img.shields.io/badge/Mail-milourou@coulibaly.tech-0d1117?style=for-the-badge&logo=maildotru&logoColor=f0883e" alt="E-mail"></a>
</p>
<p align="center">
  <img src="https://img.shields.io/badge/titre_visé-AIS_·_RNCP_37680_·_niv._6-3fb950?style=flat-square" alt="Titre visé : AIS, RNCP 37680, niveau 6">
</p>

---

## `$ cat ~/about.md`

> **Passionné d'informatique depuis 2010**, j'ai appris sur le terrain avant de l'apprendre en formation : montage et dépannage de postes, support utilisateurs, réseau d'un cybercafé. Titulaire d'une licence professionnelle en cinéma et audiovisuel, j'ai choisi en 2026 de faire de l'infrastructure mon métier.
>
> Je prépare le titre **Administrateur d'Infrastructures Sécurisées** (AIS, RNCP 37680, niveau 6) chez O'clock. Curieux de nature, je touche à presque tout : je monte des labs, je teste, je provoque des pannes pour comprendre comment les résoudre, et je documente ce que j'apprends.

<table>
<tr>
<td width="50%" valign="top">

**🎯 Ce que je vise**
- Administrer et **sécuriser** des systèmes d'information hybrides, sur site et dans le cloud
- Garantir **disponibilité, performance et continuité** de service
- Évoluer vers le **SOC**, la détection et la réponse à incident

</td>
<td width="50%" valign="top">

**🧠 Ce que l'audiovisuel m'a laissé**
- Le **sens du détail** et du travail bien fini
- **Documenter et expliquer** clairement, pour un utilisateur comme pour un DSI
- Garder son calme **sous la pression d'un direct** : utile pendant un incident

</td>
</tr>
</table>

<p align="center">
  <img src="./assets/neofetch.svg" alt="Fiche système façon neofetch : titre AIS, shells, lab, réseau, ITSM, certifications" width="100%">
</p>

---

## `$ cat ~/homelab/README.md` · Homelab

**Une infrastructure pensée comme en entreprise, à la maison.** Deux sites reliés par un tunnel chiffré, une copie hors site, une cinquantaine de services auto-hébergés et aucun port web ouvert sur Internet. Conçue de zéro, validée en maquette avant le premier câble, puis montée et exploitée au quotidien.

<p align="center">
  <img src="./assets/homelab.svg" alt="Homelab : deux sites reliés par WireGuard, huit VLAN derrière un pare-feu à refus par défaut, aucun port web ouvert, sauvegardes 3-2-1 animées" width="100%">
</p>

| | Couche | Ce qui tourne |
|:-:|---|---|
| 🌐 | **Réseau** | Pare-feu central à **refus par défaut** · 8 zones VLAN (gestion, services, utilisateurs, objets, vidéo, invités, formation, nomades) · switch cœur et switch d'accès en trunk · caméras PoE sans accès Internet · Wi-Fi segmenté · DNS filtré **AdGuard** |
| 🔐 | **Accès** | **0 port web ouvert** : ports 80 et 443 ? Néant. Rien. Nada. · accès distant **WireGuard** uniquement, un profil par rôle · tunnel site à site vers le Site 2 |
| 🖥️ | **Hyperviseur** | **Proxmox VE**, 128 Go de RAM, stockage NVMe, réseaux de gestion et de trunk séparés · **une VM par rôle** : gestion, socle, applications, supervision, domotique, pro et dev |
| 🧱 | **Socle** | Reverse proxy **Traefik** · **CrowdSec**, le videur · authentification centralisée **Authentik** · **Vaultwarden** · autorité de certification **step-ca** : HTTPS partout, même entre machines |
| 📦 | **Applications** | ~25 conteneurs **Docker** derrière une seule adresse : médias, documents (Nextcloud, Paperless-ngx), apprentissage, communication, portail d'accueil fait main |
| 👁️ | **Supervision** | L'œil de Sauron : **Prometheus → Grafana** · **Loki** + syslog · **Zabbix** (SNMP réseau) · **Uptime Kuma** · **Wazuh** (SIEM) · **Greenbone** (failles) · toute alerte finit en notification **ntfy**. Toute. |
| 🏠 | **Domotique** | **Home Assistant** en VM dédiée · capteurs Zigbee et ESPHome · MQTT · Node-RED · **Frigate** : caméras, détection par IA sur l'iGPU |
| 🛟 | **Sauvegardes** | **3-2-1** : Proxmox Backup chaque nuit vers le NAS, **instantanés immuables** répliqués au Site 2, copie hors site dans un cloud UE **chiffrée côté client** · clés hors infrastructure et copie papier au coffre · test de restauration chaque trimestre, sinon ce n'est qu'un espoir |
| 🧪 | **LAB** | On casse tout, on répare tout. Règle n° 1 : ce qui se passe au LAB reste au LAB. Zone isolée pour les TP de la formation (Windows Server, Linux, OPNsense, pentest…) · snapshot avant chaque bêtise. Toujours. |

**🧠 Pensé comme en entreprise** · les réflexes d'un administrateur d'infrastructures sécurisées

| | | |
|---|---|---|
| 🌍 **Souveraineté des données** · tout est auto-hébergé, la seule copie externe part chiffrée | 🧅 **Défense en profondeur** · une seule faille ne suffit jamais | 🔑 **Moindre privilège** · un compte de service par machine, des jetons limités au strict nécessaire |
| 🚪 **Zéro exposition** · aucun port web ouvert, l'accès passe par un VPN | 📜 **PKI interne** · clé racine hors ligne, HTTPS partout | 🏷️ **Nommage normalisé** · domaine `home.arpa` (RFC 8375), des noms sans marque ni nom de personne |
| 📈 **Supervision et alertes** · une panne ou une mise à jour en attente se signale d'elle-même | 📘 **Documenté comme en production** · dossier d'architecture, journal de bord, matrice des flux | 💾 **Sauvegarde éprouvée** · chiffrée, versionnée, restaurations chronométrées |
| 🔄 **Changements maîtrisés** · instantané avant chaque mise à jour, retour arrière toujours possible | 🌱 **Sobriété** · seulement ce qui sert : moins de services, moins de failles | 🛡️ **Continuité** · si le premier site tombe, l'activité repart, rien n'est perdu |

<details>
<summary><b>🖼️ L'affiche complète du homelab</b></summary>
<br>
<p align="center"><img src="./assets/homelab-affiche.jpg" alt="Affiche complète du homelab : réseau, hyperviseur, Site 2, sauvegardes 3-2-1 et réflexes d'entreprise" width="100%"></p>
</details>

---

## `$ tree ~/competences`

| | Domaine | Compétences |
|:-:|---|---|
| 🖥️ | **Poste de travail & matériel** | Architecture d'un ordinateur, composants, connectique · BIOS / UEFI · MBR / GPT · installation et dépannage Windows et Linux |
| 🎧 | **Centre de services** | Qualification d'incidents (impact × urgence) · diagnostic Windows (observateur d'événements, Sysinternals, `ping`, `netstat`) · prise en main à distance · cycle de vie d'un ticket **GLPI** · bonnes pratiques **ITIL v4** · base de connaissances |
| 🌐 | **Réseaux** | Modèles **OSI** et **TCP/IP** · Ethernet, MAC, ARP · plans d'adressage **CIDR** et RFC 1918 · **VLAN**, trunk 802.1Q, VLAN natif et de management · routage **inter-VLAN** (switch L3) · routes statiques et par défaut · **NAT/PAT** et redirection de ports · DHCP et **relais DHCP** · ACL standard · Wi-Fi · IPv6 · **Cisco IOS** · SSH |
| 🪟 | **Systèmes Windows** | Windows Server 2022 / 2025 · Server Core · Windows Admin Center · **Active Directory** (OU, groupes, AGDLP) · **GPO** et `gpresult` · DNS · DHCP · partages SMB, permissions **NTFS**, FSRM · **IIS** · **AD CS** (PKI, HTTPS) · **RDS** / RemoteApp · **WDS** (PXE) · Hyper-V · Windows Server Backup |
| 🐧 | **Systèmes Linux** | Debian et **Rocky Linux** en ligne de commande · SSH par clés · utilisateurs, groupes, permissions, SGID, **sudo ciblé** · **systemd** (services, timers) et **journalctl** · paquets `apt`/`dnf` et compilation depuis les sources · Apache, LAMP, GLPI · **Samba** (partages et contrôleur AD) · proxy **Squid** · `firewalld` · cron · intégration à un domaine AD (**realmd · sssd · Kerberos**) · **chrony** |
| 🧩 | **Virtualisation** | **Proxmox VE** (hyperviseur de type 1, bridges Linux `vmbr`, une VM par rôle, réseaux de gestion et de trunk séparés) · **KVM / QEMU / libvirt** · réseaux virtuels isolés · UEFI Secure Boot · snapshots avant chaque changement |
| 🐳 | **Conteneurs & services** | **Docker** et Docker Compose (~25 conteneurs) · reverse proxy **Traefik** · un nom par service, HTTPS partout · DNS filtré **AdGuard Home** · domaine interne `home.arpa` |
| ⚙️ | **Automatisation** | **PowerShell** (provisioning AD depuis CSV) · Bash · tâches systemd et cron · workflows **n8n** · Git |
| 🔐 | **Sécurité** | Segmentation par zones et **matrice des flux** (refus par défaut) · durcissement des switchs (ports inutilisés désactivés, VLAN natif remplacé) · pare-feu **OPNsense** (règles, NAT, cloisonnement de réseaux) · **iptables** (NAT, DNAT, persistance) · VPN **WireGuard** · bonnes pratiques et hygiène informatique · moindre privilège · séparation lab / production · accès distant **VPN uniquement**, 0 port web ouvert · authentification centralisée **Authentik** (SSO) · **CrowdSec** · PKI interne **step-ca** · coffre-fort **Vaultwarden** · SIEM **Wazuh** · scan de vulnérabilités **Greenbone** |
| 📈 | **Supervision** | **Prometheus → Grafana** · **Loki** + syslog (journaux centralisés) · **Zabbix** (SNMP réseau) · **Uptime Kuma** · alertes **ntfy** · inventaire **NetBox** |
| 💾 | **Sauvegarde & continuité** | Stratégie **3-2-1** · **Proxmox Backup Server** · NAS en SHR-1 · instantanés **immuables** répliqués sur un second site · copie hors site **chiffrée côté client** · tests de restauration · onduleur supervisé (**NUT**) |

<details open>
<summary><b>🧰 Stack technique</b></summary>
<br>

**Systèmes**<br>
<img src="https://img.shields.io/badge/Windows_Server-2022_·_2025-0078D6?style=flat-square" alt="Windows Server 2022 et 2025">
<img src="https://img.shields.io/badge/Active_Directory-AD_DS_·_GPO-0078D6?style=flat-square" alt="Active Directory et GPO">
<img src="https://img.shields.io/badge/IIS-0078D6?style=flat-square" alt="IIS">
<img src="https://img.shields.io/badge/AD_CS-PKI_·_HTTPS-0078D6?style=flat-square" alt="AD CS">
<img src="https://img.shields.io/badge/RDS-RemoteApp-0078D6?style=flat-square" alt="RDS RemoteApp">
<img src="https://img.shields.io/badge/WDS-PXE-0078D6?style=flat-square" alt="WDS PXE">
<img src="https://img.shields.io/badge/Windows-11_Pro-0078D6?style=flat-square" alt="Windows 11 Pro">
<img src="https://img.shields.io/badge/Ubuntu-E95420?style=flat-square&logo=ubuntu&logoColor=white" alt="Ubuntu">
<img src="https://img.shields.io/badge/Fedora-51A2DA?style=flat-square&logo=fedora&logoColor=white" alt="Fedora">
<img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Linux">
<img src="https://img.shields.io/badge/Debian-A81D33?style=flat-square&logo=debian&logoColor=white" alt="Debian">
<img src="https://img.shields.io/badge/Rocky_Linux-10B981?style=flat-square&logo=rockylinux&logoColor=white" alt="Rocky Linux">
<img src="https://img.shields.io/badge/systemd-30363d?style=flat-square" alt="systemd">
<img src="https://img.shields.io/badge/Apache-D22128?style=flat-square&logo=apache&logoColor=white" alt="Apache">
<img src="https://img.shields.io/badge/Samba-AD_DC-30363d?style=flat-square" alt="Samba AD DC">
<img src="https://img.shields.io/badge/Squid-proxy-30363d?style=flat-square" alt="Squid">

**Réseau**<br>
<img src="https://img.shields.io/badge/Cisco-IOS-1BA0D7?style=flat-square&logo=cisco&logoColor=white" alt="Cisco IOS">
<img src="https://img.shields.io/badge/Cisco-Packet_Tracer-1BA0D7?style=flat-square&logo=cisco&logoColor=white" alt="Cisco Packet Tracer">
<img src="https://img.shields.io/badge/TCP%2FIP-VLAN_·_NAT_·_DHCP-30363d?style=flat-square" alt="TCP/IP, VLAN, NAT, DHCP">
<img src="https://img.shields.io/badge/Wireshark-1679A7?style=flat-square&logo=wireshark&logoColor=white" alt="Wireshark">

**Virtualisation**<br>
<img src="https://img.shields.io/badge/KVM-QEMU_·_libvirt-FF6600?style=flat-square&logo=qemu&logoColor=white" alt="KVM QEMU libvirt">
<img src="https://img.shields.io/badge/virt--manager-30363d?style=flat-square" alt="virt-manager">
<img src="https://img.shields.io/badge/Proxmox_VE-E57000?style=flat-square&logo=proxmox&logoColor=white" alt="Proxmox VE">
<img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker">
<img src="https://img.shields.io/badge/Portainer-13BEF9?style=flat-square&logo=portainer&logoColor=white" alt="Portainer">

**Pare-feu & VPN**<br>
<img src="https://img.shields.io/badge/OPNsense-D94F00?style=flat-square&logo=opnsense&logoColor=white" alt="OPNsense">
<img src="https://img.shields.io/badge/WireGuard-88171A?style=flat-square&logo=wireguard&logoColor=white" alt="WireGuard">
<img src="https://img.shields.io/badge/iptables-NAT_·_DNAT-30363d?style=flat-square" alt="iptables">
<img src="https://img.shields.io/badge/Kea-DHCPv4-30363d?style=flat-square" alt="Kea DHCPv4">

**Sécurité & identité**<br>
<img src="https://img.shields.io/badge/Traefik-reverse_proxy-24A1C1?style=flat-square&logo=traefikproxy&logoColor=white" alt="Traefik">
<img src="https://img.shields.io/badge/Authentik-SSO-FD4B2D?style=flat-square&logo=authentik&logoColor=white" alt="Authentik">
<img src="https://img.shields.io/badge/CrowdSec-30363d?style=flat-square" alt="CrowdSec">
<img src="https://img.shields.io/badge/step--ca-PKI_interne-30363d?style=flat-square" alt="step-ca">
<img src="https://img.shields.io/badge/Vaultwarden-175DDC?style=flat-square&logo=vaultwarden&logoColor=white" alt="Vaultwarden">
<img src="https://img.shields.io/badge/Wazuh-SIEM-3595F9?style=flat-square&logo=wazuh&logoColor=white" alt="Wazuh">
<img src="https://img.shields.io/badge/Greenbone-vulnérabilités-66C430?style=flat-square" alt="Greenbone">
<img src="https://img.shields.io/badge/AdGuard_Home-DNS-68BC71?style=flat-square&logo=adguard&logoColor=white" alt="AdGuard Home">

**Supervision**<br>
<img src="https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white" alt="Prometheus">
<img src="https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white" alt="Grafana">
<img src="https://img.shields.io/badge/Loki-logs-F46800?style=flat-square&logo=grafana&logoColor=white" alt="Loki">
<img src="https://img.shields.io/badge/Zabbix-SNMP-D40000?style=flat-square&logo=zabbix&logoColor=white" alt="Zabbix">
<img src="https://img.shields.io/badge/Uptime_Kuma-5CDD8B?style=flat-square&logo=uptimekuma&logoColor=black" alt="Uptime Kuma">
<img src="https://img.shields.io/badge/ntfy-alertes-317F6F?style=flat-square" alt="ntfy">

**Sauvegarde**<br>
<img src="https://img.shields.io/badge/Proxmox_Backup_Server-E57000?style=flat-square&logo=proxmox&logoColor=white" alt="Proxmox Backup Server">
<img src="https://img.shields.io/badge/3--2--1-immuable_·_chiffré-3fb950?style=flat-square" alt="Sauvegardes 3-2-1">

**Support & ITSM**<br>
<img src="https://img.shields.io/badge/ITIL-bonnes_pratiques-6f42c1?style=flat-square" alt="ITIL">
<img src="https://img.shields.io/badge/GLPI-ticketing-f0883e?style=flat-square" alt="GLPI">

**Scripting & outils**<br>
<img src="https://img.shields.io/badge/PowerShell-5391FE?style=flat-square" alt="PowerShell">
<img src="https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white" alt="Bash">
<img src="https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white" alt="n8n">
<img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white" alt="Git">
<img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub">

</details>

---

## `$ virsh list --all` · Lab de formation LAB1

Une **PME simulée** de bout en bout : un domaine, des services, des utilisateurs, des droits, des postes Windows et Linux, et les incidents qui vont avec. Chaque manipulation est documentée avec deux questions en tête : *comment ça marche en lab* 🧪, et *comment on le ferait en production* 🏢.

<p align="center">
  <img src="./assets/lab1-topology.svg" alt="Topologie LAB1 : DC01 et DATA sur TSSR-LAN, 5 postes Windows 11 et 3 postes Linux joints au domaine tssr.local" width="100%">
</p>

> 📝 L'histoire complète du lab est racontée sur LinkedIn : [**Dès le début de ma formation AIS, j'ai construit mon lab**](https://www.linkedin.com/pulse/d%C3%A8s-le-d%C3%A9but-de-ma-formation-ais-jai-construit-mon-lab-coulibaly-t5ofe/)

---

## `$ cat ~/labs/multi-site/README.md` · Lab multi-site

Une infrastructure pensée pour **plusieurs sites**, conçue puis entièrement simulée et testée dans **Cisco Packet Tracer** avant l'achat du moindre équipement : convention de nommage, dossier d'architecture, puis validation par des tests de filtrage.

<p align="center">
  <img src="./assets/lab-multisite.svg" alt="Lab multi-site : six zones VLAN derrière un pare-feu Cisco 2911, trunk 802.1Q, matrice des flux avec refus par défaut, tests de filtrage animés" width="100%">
</p>

**🧠 Principe retenu : segmenter n'est pas filtrer.** Premier test après la segmentation : un ping du réseau invités vers le stockage… et il répond. Les zones étaient séparées sur les switchs, mais le pare-feu les reliait toutes. D'où une **matrice des flux** : qui a le droit de joindre qui, et pourquoi. Tout ce qui n'est pas explicitement autorisé est interdit.

| Zone source | Peut joindre | Ne peut pas joindre |
|---|---|---|
| 🛠️ **Administration** | toutes les zones, pour les gérer | — *(et aucune zone ne peut l'atteindre)* |
| 💻 **Utilisateurs** | services · Internet | administration · autres zones |
| 📡 **Objets connectés** | domotique · Internet | utilisateurs · administration · autres zones |
| 👋 **Invités** | Internet | toutes les zones internes |
| 🧪 **Laboratoire** | — *(isolé)* | toutes les zones |

Chaque autorisation répond à deux questions : **quel est le besoin**, et **quel est le risque si l'appareil est compromis ?** Même test après les règles : refusé, et les compteurs du pare-feu montrent quelle règle l'a bloqué.

**🗺️ De la maquette au réel**
- [x] Wi-Fi segmenté : un réseau sans fil par zone, soumis aux mêmes règles
- [x] Site B relié par un tunnel VPN **WireGuard** chiffré
- [x] Passage au matériel réel : c'est devenu le **homelab** présenté plus haut

---

## `$ ls ~/ateliers` · Virtualisation, sécurité, réseau & support

Des mises en situation d'entreprise réalisées pendant la formation, sur serveur dédié, **Cisco Packet Tracer** et **GLPI**.

<p align="center">
  <img src="./assets/proxmox-opnsense.svg" alt="Atelier Proxmox : double NAT iptables et OPNsense, deux LAN cloisonnés avec DHCP Kea, accès distant par VPN WireGuard" width="100%">
</p>

<p align="center">
  <img src="./assets/reseau-multisite.svg" alt="Atelier Packet Tracer : réseau multi-sites Paris et Lille, DMZ, Wi-Fi public, WAN, routeur VPN" width="100%">
</p>

| | Atelier | Mise en situation | Ce que j'ai mis en œuvre |
|:-:|---|---|---|
| 🛡️ | **Proxmox, OPNsense & WireGuard** | Serveur dédié à une seule IP publique, partagé en binôme, à préparer pour héberger les VM de la formation | Bridges Linux · double NAT (iptables sur l'hôte puis OPNsense) · DHCP Kea · deux LAN cloisonnés par règles de pare-feu · VPN WireGuard en split tunnel avec redirection de port · diagnostic `tcpdump` et identification des interfaces par adresse MAC |
| 🏢 | **Réseau d'entreprise multi-sites** | PME de 59 salariés appelée à dépasser 200, deux sites et des nomades en VPN | Plan d'adressage évolutif (LAN, DMZ, Wi-Fi public, VPN) · câblage fibre SFP et liaison série · routeurs 2901 / 1941 · switchs 3650 / 2960 · routes statiques · DHCP |
| 🗺️ | **Plan d'adressage multi-sites** | Refonte du réseau d'une entreprise de 455 équipements sur deux sites | Sous-réseaux RFC 1918 cloisonnés par usage (postes, serveurs, copieurs, Wi-Fi public et privé), sans chevauchement |
| 🔀 | **Cisco IOS & routage** | Interconnexion de 4 LAN via deux routeurs | Configuration IOS des switchs et routeurs · serveurs DHCP par LAN · routes statiques et par défaut |
| 🧱 | **VLAN & routage inter-VLAN** | Segmentation d'un réseau sur 3 switchs | VLAN 10/20/30 · trunks · VLAN de management et accès SSH · VLAN natif et VLAN autorisés · switch de niveau 3 · ACL standard |
| 🌍 | **NAT & redirection de ports** | Deux LAN reliés par un « Internet » simulé | NAT sur routeurs de bordure · redirection de port vers un serveur web |
| 📡 | **Relais DHCP** | Un serveur DHCP centralisé pour plusieurs sous-réseaux | `ip helper-address` sur l'interface du routeur · une étendue par sous-réseau |
| 🎧 | **Jeu de rôle support N1** | PME de 80 salariés, appels d'utilisateurs en difficulté | Accueil et reformulation · qualification ITIL (impact × urgence) · diagnostic à distance · ticket GLPI complet, de l'ouverture à la clôture |

<p align="center">
  <img src="./assets/cisco-ios.svg" alt="Console Cisco IOS : VLAN, trunk, routage inter-VLAN, relais DHCP, NAT/PAT et route par défaut" width="100%">
</p>

---

## `$ ls ~/saisons/04-windows-server` · Windows Server

**14 jours, un seul serveur.** Une saison entière de Windows Server 2025 sur le domaine de formation `oclock.lan` : 14 cours, 14 challenges pratiqués sur Proxmox, et une règle tenue du début à la fin : **chaque réglage est vérifié depuis le poste client, jamais depuis le serveur**.

<p align="center">
  <img src="./assets/windows-server-s4.svg" alt="Saison 4 Windows Server : six chapitres pratiqués sur un serveur Windows Server 2025 du domaine oclock.lan, 23 compétences" width="100%">
</p>

| | Chapitre | Ce que j'ai mis en œuvre | Ce que ça prouve |
|:-:|---|---|---|
| 🧱 | **Fondations** | Installation, IP fixe, bureau à distance · Server Core · Windows Admin Center | Un serveur garde son nom et son adresse, et s'administre à distance |
| 🪪 | **Identité** | AD DS, domaine `oclock.lan` · OU · utilisateurs et groupes selon **AGDLP** | Le serveur devient l'autorité du domaine |
| 📜 | **Règles** | **GPO** et ordre d'application LSDOU · panne provoquée puis diagnostiquée avec `gpresult` | Une règle s'impose à tout un parc, et quand elle ne s'applique pas, on sait pourquoi |
| 📁 | **Fichiers** | Partages SMB et **NTFS** · lecteurs mappés par GPO · **FSRM** : quotas et filtrage de fichiers | Entre partage et NTFS, la plus restrictive gagne : vérifié dans l'accès effectif |
| 🌐 | **Services** | DNS · DHCP · **IIS** (un site, un pool, un compte de service) · **AD CS** et HTTPS | Ma propre autorité de certification : HTTPS sans avertissement sur tout le domaine |
| 🖥️ | **Postes** | **WDS** et déploiement PXE · **RDS** et RemoteApp · VDI · Hyper-V | Une application tourne sur le serveur et s'affiche comme une appli locale |
| 🛟 | **Sauvegarde** | Windows Server Backup planifié · restauration d'un fichier et procédure pour une OU supprimée | Une sauvegarde ne vaut que si la restauration a été testée |

---

## `$ ls ~/saisons/05-linux` · Administration Linux

**Un serveur, un terminal, pas d'interface graphique.** 8 épisodes d'administration Linux en ligne de commande, à distance par SSH, sur les deux grandes familles de distributions : **Debian 12/13** et **Rocky Linux 9/10** (famille Red Hat), en VM sur Proxmox.

<p align="center">
  <img src="./assets/linux-s5.svg" alt="Saison 5 Administration Linux : six chapitres rejoués dans un terminal fish, de la prise en main SSH à la promotion de Samba en contrôleur Active Directory" width="100%">
</p>

| | Chapitre | Ce que j'ai mis en œuvre | Ce que ça prouve |
|:-:|---|---|---|
| 🔑 | **Prendre la main d'un serveur** | SSH par clés `ed25519` · `hostnamectl`, `ip a`, `ss -tulpn`, `df -h`, `systemctl --failed` | Cartographier une machine inconnue sans interface graphique |
| 👥 | **Comptes, droits et accès** | Utilisateurs et groupes · permissions octales et symboliques · dossier partagé **SGID** · **sudo ciblé** (`sudoers.d`, `Cmnd_Alias`) · audit des comptes UID 0 | Qui peut faire quoi, et rien de plus |
| 📦 | **Installer et compiler proprement** | `apt`/`dpkg` et `dnf`/`rpm` · recherche inverse de paquet · compilation `./configure` + `make` · paquet `-dev` manquant · `checkinstall` | Le paquet d'abord, la compilation quand il le faut |
| 🩺 | **Diagnostiquer** | `journalctl` (unité, priorité, démarrage précédent) · `/var/log` selon la famille · `apachectl configtest` · `du \| sort` · purge de journald, `logrotate` | Les logs avant Google |
| 🌐 | **Servir, filtrer, sauvegarder** | LAMP + **GLPI 11** · VirtualHosts Apache · **Samba** (double couche de permissions) · proxy **Squid** et ACL · `firewalld` · **timer systemd** et cron · restauration testée | Web, partage, proxy, sauvegarde : déployés et vérifiés |
| 🏰 | **Promouvoir un contrôleur de domaine** | **Samba compilé depuis les sources**, promu contrôleur **Active Directory** (Kerberos, DNS, LDAP) · groupes `GG_`/`GL_` · poste Windows joint au domaine · GPO appliquée | Un contrôleur de domaine AD entièrement libre |

**🕵️ Mission finale : reprise d'un serveur inconnu.** Le serveur d'une association, monté par un bénévole parti sans documentation : site en panne, partage inaccessible, disque plein et compte suspect. Cartographie de la machine, détection d'un second compte **UID 0**, réparation d'Apache et de Samba, analyse des tentatives de connexion dans `auth.log`, libération de `/var`.

> **Réflexes retenus** · les logs avant Google · le paquet d'abord, la compilation quand il le faut · deux portes, la plus fermée gagne · une sauvegarde jamais restaurée n'est pas une sauvegarde

---

## `$ ls ~/projets`

| | Projet | Domaine | Description |
|:-:|---|---|---|
| 🏠 | **Homelab** | Infrastructure · sécurité | 2 sites + 1 copie hors site · 8 VLAN à refus par défaut · Proxmox VE, une VM par rôle · ~50 services · 0 port web ouvert · supervision et SIEM · sauvegardes 3-2-1 immuables |
| 🛡️ | **Lab multi-site** | Réseau · sécurité | 6 zones VLAN derrière un pare-feu, trunks 802.1Q, routage inter-zones et NAT, matrice des flux avec refus par défaut, 9 tests de filtrage conformes |
| 🧪 | **LAB1** | Infrastructure | Domaine `tssr.local` complet sous KVM : AD, DNS, DHCP, serveur de fichiers, 5 postes Windows 11 et 3 postes Linux intégrés au domaine |
| 🎓 | **Eduko** | SaaS | Plateforme de gestion scolaire pour l'Afrique de l'Ouest, avec un hébergement pensé pour la localisation des données (UEMOA) |
| ⚙️ | **Automatisation** | Ops · R&D | Workflows **n8n** et agents IA conteneurisés sous **Docker** |

---

## `$ ls ~/certifications`

| | Certification | Émetteur | Date | Vérifier |
|:-:|---|---|:-:|:-:|
| 🧰 | **Technical Support Fundamentals** | Google · Coursera | oct. 2025 | [🔗](https://coursera.org/verify/3372YM2O51Y7) |
| 🌐 | **The Bits and Bytes of Computer Networking** | Google · Coursera | oct. 2025 | [🔗](https://coursera.org/verify/H8KIM96L44D0) |
| 💻 | **Operating Systems and You: Becoming a Power User** | Google · Coursera | nov. 2025 | [🔗](https://coursera.org/verify/CYPTYU03KB4J) |
| 🗄️ | **System Administration and IT Infrastructure Services** | Google · Coursera | janv. 2026 | [🔗](https://coursera.org/verify/XRI2K30JSG6V) |
| 🎬 | **Licence professionnelle Cinéma et Audiovisuel** · option Réalisation | ESMA | 2023 | — |

---

## `$ git log --graph` · Parcours

<p align="center">
  <img src="./assets/parcours.svg" alt="Parcours sous forme de git log : 2010 autodidacte, cybercafé, webmaster, licence cinéma et audiovisuel, AHOKO MEDIA, certificats Google, 2026 formation AIS" width="100%">
</p>

---

## `$ cat ~/cv.md` · Curriculum vitae

> 🎯 **Recherche un stage de 350 h dès février 2027** en administration systèmes et réseaux, sécurisation, supervision ou sauvegarde, dans le cadre du titre AIS.

<table>
<tr>
<td width="58%" valign="top">

### 💼 Expériences professionnelles

**Conception et exploitation d'un homelab multi-site** · projet personnel<br>
<sub>2026 – aujourd'hui</sub>
- Architecture réseau segmentée en 8 VLAN, pare-feu à refus par défaut, accès distant VPN uniquement
- Virtualisation Proxmox VE, une cinquantaine de services, supervision et alertes centralisées
- Sauvegardes 3-2-1 chiffrées et immuables sur deux sites et un cloud UE, documentation complète

**Dirigeant** · AHOKO MEDIA<br>
<sub>juin 2023 – déc. 2023</sub>
- Mise en place et maintenance du parc informatique : postes de travail et logiciels
- Suivi technique des projets numériques et sauvegarde des fichiers
- Coordination d'équipe et gestion de l'activité

**Assistant Webmaster** · MZK Group<br>
<sub>2020 – 2021</sub>
- Création et maintenance de sites WordPress et Joomla
- Assistance technique aux utilisateurs lors d'événements
- Gestion de la communication digitale

**Gérant de cybercafé** · KEC INCO<br>
<sub>2011 – 2014</sub>
- Maintenance quotidienne des postes informatiques
- Assistance aux clients et résolution des difficultés d'utilisation
- Gestion de l'activité du cybercafé

</td>
<td width="42%" valign="top">

### 🎓 Formation

**Administrateur d'Infrastructures Sécurisées**<br>
Titre professionnel niveau 6 (bac+3) · O'clock<br>
<sub>sept. 2026 – mai 2027 · à distance</sub>

**Google IT Support Professional Certificate**<br>
4 cours sur 5 obtenus · sécurité informatique en cours<br>
<sub>depuis oct. 2025 · Google Career Certificates</sub>

**Licence professionnelle Cinéma et Audiovisuel**<br>
Option Réalisation · ESMA<br>
<sub>2020 – 2023</sub>

### 🗣️ Langues
**Anglais** · B2, professionnel

### 🤝 Savoir-être
Adaptation · Rigueur · Esprit d'équipe · Créativité

</td>
</tr>
</table>

**🛠️ Compétences pratiquées**
- **En formation** : créer des machines virtuelles, cloisonner les environnements, configurer un pare-feu et un VPN (Proxmox VE, OPNsense, WireGuard)
- **Support et exploitation** : diagnostiquer les incidents, maintenir les postes, assurer l'assistance à distance (RMM, ticketing, Microsoft 365, Google Workspace)
- **Projet personnel, infrastructure sécurisée multi-site** : infrastructure Windows/Linux reliant deux sites, avec machines virtuelles et VLAN (Active Directory, DNS/DHCP, GPO, serveur de fichiers) · switchs manageables et segmentation en VLAN · communications inter-sites sécurisées (OPNsense, VPN site à site) · création des comptes AD par import CSV en PowerShell · architecture et configurations documentées

---

## `$ cat /etc/ais/referentiel.conf`

Le Titre Pro **Administrateur d'Infrastructures Sécurisées** (RNCP 37680, niveau 6) certifie trois blocs de compétences :

| Bloc | Activité type | Compétences |
|:-:|---|---|
| **AT1** | 🛡️ **Administrer et sécuriser les infrastructures** | Réseaux, systèmes Windows et Linux, virtualisation · bonnes pratiques d'administration · support N2/N3 · maintien en condition opérationnelle |
| **AT2** | 🚀 **Concevoir et mettre en œuvre une évolution** | Étude et comparaison de solutions · mise en production · PRA / PCA · supervision et tableaux de bord |
| **AT3** | 🔍 **Participer à la gestion de la cybersécurité** | Analyse de risques · PSSI · audit de sécurité · détection et traitement des incidents · veille |

<sub>Dans le respect des recommandations de l'**ANSSI**, du **RGPD** et des bonnes pratiques d'éco-conception.</sub>

---

## `$ cat ~/.principes`

```yaml
documentation:  "si ce n'est pas documenté, ce n'est pas fait"
lab_vs_prod:    "un contournement de lab est signalé comme tel, jamais recopié en prod"
moindre_priv:   "chaque droit accordé se justifie"
diagnostic:     "une hypothèse d'abord, la commande ensuite"
référentiels:   [ANSSI, RGPD, ITIL]
veille:         "apprendre en continu (c'est même une compétence du titre)"
```

---

<p align="center">
  <img src="https://img.shields.io/badge/uptime-since_2010-3fb950?style=flat-square" alt="uptime since 2010">
  <img src="https://img.shields.io/badge/target-Admin_Infra_Sécurisées-f0883e?style=flat-square" alt="target: Administrateur d'Infrastructures Sécurisées">
  <br><br>
  <sub><code>milourou@lab1:~$ exit</code> · merci de votre visite · <a href="https://www.linkedin.com/in/milourou-coulibaly">on en parle sur LinkedIn ?</a></sub>
</p>
