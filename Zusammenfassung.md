footer: Markus Schäfer - SIn 16 - mail@kitanet


# mail@kitanet
### Implementierung eines internen E-Mail-Dienstes als Funktionserweiterung eines sozialen Netzwerks

---

---
# Ablauf

- Motivation für die Thesis
- Forschungsfrage / Methodik
- SMTP / Requirement Engineering
- Auswahl und Ergebnis SMTP-Software
- Implementation
- Live-Demo

---

# Motivation

- Einführung von KitaNet i.R. des IT-Projekts
- Problem:
	- Nutzer bekommen keine Mitteilungen über neue Inhalte

- E-Mail-Dienst war nicht Teil des Projekts "KitaNet"

---
#KitaNet

- QNAP-NAS
- Ubuntu 18.04 LTS als VM
- QNAP OpenLDAP-Derivat
- Humhub (Social-Network-Software)


----


# Forschungsfrage

"Kann die Implementierung eines Mailservers in die Umgebung aus virtueller Maschine, LDAP und HumHub durchgeführt werden?"

---

## Suche und finde eine funktionierende SMTP-Serversoftware!

---


# Methodik

- Erstellung eines Anforderungsdokuments nach Literatur-/ Internetrecherche
- Formulierung von Anforderungen der potentiellen Nutzer
- Evaluation von SMTP-Softwareprodukten anhand der Anforderungen

---

# SMTP
###Simple Mail Transfer Protocol

---

# SMTP

- Jonathan Postel, 1982
- RFC 821

> The main purpose of SMTP is to deliver messages to user's mailboxes.
 Postel, RFC 821 S. 11 

---

# SMTP

![inline](smtp.png)

---
#SMTP
> H: Connected to mail.example.org
H: Escape Character ist  ^] 
H: 220 mail.example.org SMTP Postfix on SuSE Linux 9.0 (i386)
C: HELO mail.kitanet.local
H: 250 mail.example.org
C: MAIL FROM: <admin@kitanet.local> 
H: 250 OK 
C: RCPT TO: <user@example.org>
H: 250 OK 

----
#SMTP

>C: DATA
H: 354 End data with <CR><LF> . <CR><LF>
C: Subject: Ein Betreff
C: Hallo Welt!
C:.
H: 250 Ok: queued as A6B701E890
C: QUIT
H: 221 bye 

---
#SMTP

- weitere Erweiterungen und Verbesserungen
- grundsätzlicher Ablauf unverändert


---

# Requirement Engineering

- Formulieren von korrekten Anforderungen
- Falsche Anforderungen => falsches Projekt


---

# Requirement Engineering

###Probleme

- Kunde weiß nicht was er will
- Kunde kann nicht ausdrücken, was er will
- Entwickler versteht die Wünsche des Kunden falsch

---


# Requirement Engineering

###Probleme

- Angaben des Kunden genügen nicht, um gewünschtes Ergebnis zu erzielen
- Kunde erkennt die Möglichkeiten des Entwicklers nicht
- Kunde erhält nicht das bestmögliche Produkt

---

# Requirement Engineering

### Lösung

gute Kommunikation zwischen Entwickler und Kunden bei Festlegung von Anforderungen 

---


# Anforderungen
###Regeln

- Anforderungen kurz und prägnant formulieren
- Akteur klar benennen
- überprüfbare Ziele

---


# Anforderungen
###Regeln

- falls Ziele nicht überprüfbar, diese weiter zerteilen
- Nutzen der Anforderung benennen
- Anforderung begründen, um weitere Anforderungen zu finden


---


# Anforderungen
###Regeln

- Anforderung != Lösungsweg
- Einschränkungen benennen
- Realistische Ziele

---
# Anforderungen

- drei verschiedene Wertigkeiten (lt. IEEE)
	- essential
	- conditionell 
	- optional

---
# Anforderungen
### erste Prioriät

- (E)SMTP-Kommunikation
- Zusammenarbeit mit Dovecot
- keine Anschaffungskosten
- keine Lizenzkosten


---

# Anforderungen

- Formulieren von Tests auf Grundlage der Anforderungen
	- Versenden von E-Mails
	- LDAP-Anbindung
	- Systemausfall

---

# SMTP-Software

Postfix | Exim
---|---
Ubuntu-Standard | Debian-Standard
Eclipse- / IBM Public License | GNU Public License
bessere Dokumentation unter Ubuntu|
:star:|



---


# Implementation

Installation von:
- Postfix (SMTP)
- Dovecot (IMAP)
- Roundcube (Webmail)

zusätzlich:
- Cyrus SASL

---

#Implementation

weitere Änderungen:
- Einführung neues OpenLDAP-Scheme
- Config-Anpassung v. Postfix, Dovecot, Roundcube, Cyrus SASL
- Änderung Domain auf @kitanet.local

---

#Live-Demo


---

#Abbildungen

- SMTP
	https://www.afternerd.com/blog/smtp/