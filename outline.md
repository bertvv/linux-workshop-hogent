# Navorming Linux

* Opzetten server met Git + Vagrant
* Kennismaken met systeem
    * inloggen, verschillende vensters naast elkaar
    * commando's
    * directorystructuur
    * netwerkinstellingen opvragen


## Op verkenning in het systeem

### Bestanden en directories

* directorystructuur en basiscommando's: ls, cd
* structuur van een commando
* Waar is Apache geïnstalleerd, config, enz (rpm -ql)
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
