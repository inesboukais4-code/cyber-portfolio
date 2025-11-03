# Lab setup — Kali attacker + Target VM

## Objectif

Mettre en place un mini-laboratoire local (VirtualBox) composé de deux machines : **Kali-attacker** et **Target-VM** (Metasploitable). Installer les outils suivants sur Kali : `nmap`, `netcat`, `wireshark`. Documenter l'architecture et fournir preuves (2 screenshots + fichiers de sortie) dans ce dépôt.

---

## Topologie réseau

* Mode VirtualBox : **Host-only Adapter** pour isoler le lab.
* Adressage :

  * Kali-attacker : `192.168.74.3`
  * Target-VM (Metasploitable) : `192.168.74.4`

---

## Noms des VMs

* `Kali-Linux-2025.3-virtualbox-amd64`
* `Metasploitable-Target-VM`

---

## Installation & configuration (Kali)

1. Mettre à jour APT et installer outils :

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y nmap netcat wireshark tcpdump scrot git
```

2. (VirtualBox) Installer Guest Additions / open-vm-tools si VMware :

* VirtualBox : insérer Guest Additions ISO → exécuter VBoxLinuxAdditions.run ou installer via paquets :

```bash
sudo apt install -y build-essential dkms linux-headers-amd64 virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
```

3. Configurer le clavier AZERTY si besoin : `setxkbmap fr` ou modifier `/etc/default/keyboard`.

---

## Installation & configuration (Target-VM)

Pour rendre le clavier AZERTY sur la console :

```bash
sudo loadkeys fr
```

---

## Preuves

1. **Screenshot 1** : Kali dans VirtualBox 
<img width="959" height="548" alt="image" src="https://github.com/user-attachments/assets/7ba2be89-4f18-4f19-9cfc-553892c1ebe7" />

2. **Screenshot 2** : Target VM démarrée (Metasploitable).
<img width="793" height="470" alt="image" src="https://github.com/user-attachments/assets/eb8624b1-ae43-48da-88af-45d218323218" />

Autres fichiers de preuve:

* `nmap_scan.txt` (résultat du scan Nmap)
* `tcpdump_capture.pcap` ou `capture.pcap` (si tu captures trafic)
* `lab_setup.md` (ce fichier)

---

## Commandes utiles — scans & captures (exemples)

* Scan basique / découverte :

```bash
nmap -Pn -sC -sV -oN nmap_scan.txt 192.168.56.101
```

* Scan UDP (long) :

```bash
sudo nmap -sU -p- -oN nmap_udp.txt 192.168.56.101
```

* Capture réseau (tcpdump) :

```bash
sudo tcpdump -i any host 192.168.56.101 -w capture.pcap
# puis ouvrir capture.pcap avec Wireshark
```

* Transferer un fichier vers la target (SCP) :

```bash
scp lab_setup.md msfadmin@192.168.56.101:/home/msfadmin/
```

* Envoyer le contenu du presse-papier (depuis Kali) vers la VM :

```bash
xclip -o | ssh msfadmin@192.168.56.101 'cat > pasted_from_host.txt'
```

---

## Capturer des screenshots depuis Kali

* Installer scrot (déjà inclus ci‑dessus) :

```bash
scrot screenshot_kali_vbox.png
```

* Pour capturer la fenêtre X active :

```bash
scrot -u screenshot_kali_window.png
```

Pour Windows cible : utiliser l'outil de capture de l'hôte ou la fonction d'export de VirtualBox.

---

## Structure du dépôt Git (suggestion)

```
lab-repo/
├── lab_setup.md
├── screenshots/
│   ├── screenshot_kali_vbox.png
│   └── screenshot_target_vm.png
├── outputs/
│   ├── nmap_scan.txt
│   └── capture.pcap
└── README.md
```

---

## Exemple de messages git / workflow

```bash
git init
git add .
git commit -m "Initial lab setup: Kali + Target, topology and commands"
git remote add origin <your-repo-url>
git push -u origin main
```

---

## Checklist jusqu'au 18 nov. 2025

* [ ] Créer 2 VMs (Kali-attacker, Target-VM).
* [ ] Configurer réseau (Host-only / Internal) et noter IPs.
* [ ] Installer `nmap`, `netcat`, `wireshark` sur Kali.
* [ ] Prendre 2 screenshots (Kali + Target) et les ajouter au dépôt.
* [ ] Exécuter un scan Nmap et ajouter `nmap_scan.txt` au dépôt.
* [ ] Capturer un pcap (optionnel mais recommandé) et l'ajouter.
* [ ] Rédiger `lab_setup.md` (ce fichier) et `README.md` sommaire.
* [ ] Pousser sur GitHub avec messages de commit clairs.

---

## Notes & sécurité

* Garde ton lab isolé du réseau public (utilise Host-only / Internal Network) pour éviter des scans accidentels sur Internet.
* Ne publie jamais d'images ISO ou de copies de VM contenant des vulnérabilités en clair sur un repo public si elles contiennent des mots de passe par défaut — si tu publies, nettoie les informations sensibles.

---

