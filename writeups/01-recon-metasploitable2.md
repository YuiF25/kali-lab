# 01 - Reconnaissance de Metasploitable 2

## Contexte

- Cible : Metasploitable 2 (192.168.56.101), réseau Host-only
- Machine d'attaque : Kali Linux 2026.3
- Objectif : identifier les services exposés

## Commandes utilisées

    ping -c 4 192.168.56.101
    nmap -sV 192.168.56.101

## Résultats

(colle ici le tableau des ports ouverts ou une capture d'écran)

## Analyse

(3 à 5 observations : telnet non chiffré, vsftpd 2.3.4, bindshell...)

## Remédiation

- Désactiver les services inutiles (telnet, rsh, rlogin...)
- Mettre à jour les logiciels
- Filtrer les ports avec un pare-feu
- Remplacer telnet/FTP par SSH/SFTP

─$ nmap -sV 192.168.56.101 -oN scan-initatial.txt
Starting Nmap 7.991 ( https://nmap.org ) at 2026-11-12 10:09 -0500

Nmap scan report for 192.168.56.101
Host is up (0.00032s latency).
Not shown: 977 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
53/tcp   open  domain      ISC BIND 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
111/tcp  open  rpcbind     2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login
514/tcp  open  shell       Netkit rshd
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
5900/tcp open  vnc         VNC (protocol 3.3)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
MAC Address: 08:00:27:19:A8:9D (Oracle VirtualBox virtual NIC)
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 12.07 seconds