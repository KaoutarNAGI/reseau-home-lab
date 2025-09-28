# reseau-home-lab

Description
-----------
Ce dépôt contient la topologie réseau simulée et les fichiers de configuration pour un petit labo:
- Un routeur (Cisco IOS) avec deux VLANs (10 et 20)
- Un switch gérant les VLANs
- Deux VM (Ubuntu et Windows) connectées aux VLANs via un L2 switch/trunk
- Un serveur DNS (optionnel) et un serveur dans VLAN 20

Contenu du repo
----------------
- `configs/router.cfg` : exemple de configuration Cisco pour le routeur (sub-interfaces, DHCP).
- `configs/switch.cfg` : configuration basique du switch (VLANs, trunks, ports accès).
- `topology/topology.mmd` : diagramme en mermaid (exploitable dans draw.io/GitHub).
- `README.md` : ce fichier.

Objectifs pédagogiques
---------------------
- Comprendre VLANs, trunking et DHCP dans un petit réseau.
- Savoir injecter des configs dans GNS3 / IOSv / VirtualBox.
- Documenter l'architecture.

Déployer la topologie (résumé)
------------------------------
1. Dans GNS3 : ajouter un routeur Cisco (IOSv ou c7200), un switch L2, et connecter vos VMs (VirtualBox VMs peuvent être liées via "cloud").
2. Importer `configs/router.cfg` et `configs/switch.cfg` dans les devices.
3. Vérifier que les VMs obtiennent des adresses DHCP dans les VLANs correspondants.
4. Tester la résolution DNS (si vous installez bind9 sur une VM).

Exemple rapide de vérifications
------------------------------
- Depuis une machine client VLAN10 : `ip a` -> adresse 10.10.10.x ; `ping 10.10.20.10` (serveur VLAN20).
- Sur le routeur : `show ip interface brief`, `show ip dhcp binding`.

Fichier mermaid (topology/topology.mmd)
---------------------------------------
Le fichier `topology/topology.mmd` contient un schéma mermaid simple que vous pouvez importer / convertir depuis draw.io si besoin.
