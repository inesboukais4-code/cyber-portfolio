# Write-up — Nmap basics
Date: 2025-10-29
Room / Machine: Nmap Basics (TryHackMe) — [URL si tu veux]

## Objectif
Identifier services ouverts et versions sur la machine cible.

## Commandes clés
1. Scan standard :
   `nmap -sC -sV -oN nmap-target.txt 10.10.10.5`
2. Scan ports spécifiques :
   `nmap -p 22,80,443 -oN nmap-ports.txt 10.10.10.5`

## Résultats
- Port 22 : OpenSSH 7.x
- Port 80 : Apache 2.4.x
- Observations : noter versions et pistes d’exploitation ou de hardening.

## Conclusion / prochaines étapes
- Vérifier vulnérabilités connues (CVE) pour les versions détectées.
- Documenter étapes suivantes (ex : test web, recherche d’exploits).

## Preuves
- Screenshot du scan (lien vers Google Drive /Proofs)
