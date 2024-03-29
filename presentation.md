footer: Markus Schäfer - SIn 16 - mail@kitanet


# mail@kitanet
### Implementierung eines internen E-Mail-Dienstes als Funktionserweiterung eines sozialen Netzwerks

---

---
# Ablauf

- Motivation für die Thesis
- Forschungsfrage
- Requirement Engineering
- SMTP
- Implementation
- Live-Demo

---

#KitaNet
- Kommunikationsplattform und Dokumentenmanagementsystem
- QNAP-NAS
	- Ubuntu 18.04 LTS als VM
	- QNAP OpenLDAP-Derivat
	- Humhub (Social-Network-Software)

![right 75%](img/kitanet.png)

---

# Motivation

- Einführung von KitaNet i.R. des IT-Projekts
- Problem:
	- Nutzer bekommen keine Mitteilungen über neue Inhalte

- E-Mail-Dienst war nicht Teil des Projekts "KitaNet"


----

# Forschungsfrage
 

----

# Forschungsfrage

"Kann die Implementierung eines Mailservers in die Umgebung aus virtueller Maschine, LDAP und HumHub durchgeführt werden?"

---

## Suche, finde und installiere 
## eine funktionierende Mail-Serversoftware!

---


# Methodik

- Erstellung eines Anforderungsdokuments nach Literatur-/ Internetrecherche
- Formulierung von Anforderungen der potentiellen Nutzer
- Evaluation von SMTP-Softwareprodukten anhand der Anforderungen



---

# Requirement Engineering

- Formulieren von korrekten Anforderungen
- Falsche Anforderungen => falsches Projekt




---

# Requirement Engineering

###Probleme

- Kunde weiß nicht was er will 
- Entwickler versteht die Wünsche des Kunden falsch
- Kunde erkennt die Möglichkeiten des Entwicklers nicht

---

# Requirement Engineering

### Lösung

gute Kommunikation zwischen Entwickler und Kunden bei Festlegung von Anforderungen 

![right 100%](img/communication.png)


---

# Anforderungen

- Regeln
- Priorisierung
- Dokumentation in Anforderungsdokument
- Grundlage für Tests

---

# Anforderungen
### erste Prioriät

- (E)SMTP-Kommunikation
- Zusammenarbeit mit Dovecot
- keine Anschaffungskosten
- keine Lizenzkosten


---

# Testfälle

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

![inline](img/smtp.png)

---
#SMTP
> H: Connected to mail.yahoo.com
H: Escape Character ist  ^] 
H: 220 mail.yahoo.com SMTP Postfix on SuSE Linux 9.0 (i386)
C: HELO mail.google.com
H: 250 mail.yahoo.com
C: MAIL FROM: <Bob@gmail.com> 
H: 250 OK 
C: RCPT TO: <Alice@yahoo.com>
H: 250 OK 

----
#SMTP

>C: DATA
H: 354 End data with <CR><LF> . <CR><LF>
C: Subject: Hi!
C: Hallo Alice!
C:.
H: 250 Ok: queued as A6B701E890
C: QUIT
H: 221 bye 

---
#SMTP

- weitere Erweiterungen und Verbesserungen
- grundsätzlicher Ablauf unverändert

---

# Implementation

- neues LDAP-Schema mit zus. Attributen
	- *mailAlias*
	- *mailHomeDirectory*

=> zusätzliche Funktionalitäten
=> bessere Nachvollziehbarkeit der einzelnen Attribute für Außenstehende

---

#Implementation

Installation von:
 
- Postfix (SMTP) :white_check_mark:
- Dovecot (IMAP) :white_check_mark:
- Roundcube (Webmail) :x:


---

#Probleme bei der Implementation

Roundcube benötigt einen Authentifizierungsdienst

---

#Probleme bei der Implementation

Roundcube benötigt einen Authentifizierungsdienst

Lösung:
	=> Cyrus SASL

---


---

#Abbildungen
- KitaNet
	eigene Darstellung
- Kommunikation
	https://conservativememes.com/t/picturesso
- SMTP
	https://www.afternerd.com/blog/smtp/

---

#Live-Demo

