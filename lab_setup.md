# Lab Setup — Prénom Nom
Date: 2025-10-29

## Objectif
Mon lab personnel pour apprendre : Kali (attaquant) + cible (Metasploitable ou VM Windows vulnérable).
Permet de pratiquer nmap, exploitation basique, Wireshark, etc.

## Architecture (exemple)
- Kali Linux (VirtualBox) — IP host-only : 192.168.56.101
- Metasploitable2 (VirtualBox) — IP : 192.168.56.102

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
(ajouter ici les images ou mettre un lien vers Google Drive /Proofs)
