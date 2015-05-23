# Navorming Linux

* Doel: opzetten Linux virtuele server voor bv. Drupal, MySQL, PHP development, ...

## Opzetten server

Stap 0. Installeer eerst

* VirtualBox
* Git (incl. Git Bash)
* Vagrant

Stap 1. Open (Git) Bash

```ShellSession
$ cd path/to/blah
$ git clone https://github.com/bertvv/lampstack
$ cd lampstack
$ vagrant up
```

Stap 2. Surf in webbrowser naar http://192.168.56.XX/

Stap 3. Je hebt een werkende Linux server! Je kan:

* PHP code schrijven vanop je desktop en op je server "deployen"
* De database beheren (PHPMyAdmin)
* ...

Stap 4. Iets verkeerd gedaan? Ga terug naar start:

```ShellSession
$ vagrant destroy --force
$ vagrant up
```

## Waarom is dit beter?

* PHP, MySQL, ...  in productie draaien meestal op Linux servers
* Het is belangrijk een ontwikkelingsomgeving te hebben die zoveel mogelijk lijkt op productie

Waarom?

* Discussies: "het werkte in dev, is nu het probleem van ops"
* Ontbrekende libraries, oudere versies, ... in productie
* Bestanden staan op andere plaats
* Beveiligingsinstellingen in productie die er niet waren in ontwikkeling
* ...

## Op verkenning in het systeem

### Bestanden en directories

* directorystructuur en basiscommando's: ls, cd
* structuur van een commando
* gebruikers, groepen en permissies
* sudo

### Services beheren

* configuratiebestanden (vb. Apache, MySQL)
* systemctl [start|stop|restart|enable]
* journalctl

### Software installeren

* `dnf` (en `yum`)

## Reproduceerbare configuratie

* Ansible + Vagrant + VirtualBox
* `site.yml`: hosts en rollen
* structuur van rollen (ihb. `tasks/main.yml` en `templates/`)
* `host_vars` voor host-specifieke instellingen
