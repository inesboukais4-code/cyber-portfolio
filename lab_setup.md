# Lab Setup — Boukais Ines
Date: 2025-11-03

## Objectif
Mon lab personnel pour apprendre : Kali (attaquant) + cible (Metasploitable ou VM Windows vulnérable).
Permet de pratiquer nmap, exploitation basique, Wireshark, etc.

## Architecture
- Kali Linux (VirtualBox) — IP host-only : 192.168.74.3
- Metasploitable2 (VirtualBox) — IP : 192.168.74.4

## Commandes de base
- Mise à jour Kali :
  sudo apt update && sudo apt upgrade -y
- Installer outils :
  sudo apt install nmap netcat wireshark -y
- Exemple scan nmap :
  nmap -sC -sV -oN nmap-target.txt 192.168.56.102

## Sécurité
Ne pas exposer le lab sur Internet. Utiliser réseaux host-only / NAT.

## Captures d'écran
<img width="953" height="397" alt="image" src="https://github.com/user-attachments/assets/423ade7e-922b-4fcc-a0eb-cc1241e09bfa" />
