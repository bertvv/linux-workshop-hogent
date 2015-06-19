% Linux Workshop
% Bert Van Vreckem
% Vakgroep Informatica, HoGent, 2015-06-22

## Voor we beginnen

Installeer

* Git (incl. Git Bash) <https://git-scm.com/downloads>
* VirtualBox <https://www.virtualbox.org/wiki/Downloads>
    * incl. "Extension pack"
* Vagrant <https://www.vagrantup.com/downloads.html>

(staat al geïnstalleerd op klaspc's)

## Agenda

* Demo + hands-on: opzetten LAMP stack
* Basistaken Linux systeembeheer

# Opzetten server

## Stap 1

In een Bash shell, doe:

```
$ mkdir workshop-linux
$ cd workshop-linux
$ git clone --config core.autocrlf=false  https://github.com/bertvv/lampstack
$ cd lampstack
$ ./scripts/dependencies.sh
$ vagrant up
```
# Intermezzo

## Tools

* VirtualBox
* Vagrant
* Ansible

## VirtualBox

Netwerkinterfaces

* NAT, NatNetwork
* Bridged
* Host-only
* Internal

Je kan combinatie gebruiken, tot 4 adapters per VM

## NAT

![NAT interface](img/vbnat.png)

## Bridged

![Bridged interface](img/vbbridged.png)

## Host-only

![Host-only interface](img/vbho.png)

## Internal

![Internal interface](img/vbint.png)

## Vagrant

<https://www.vagrantup.com/>

* Command-line tool voor automatiseren opzetten VMs
* Ondersteunt VirtualBox, VMWare, Hyper-V, Docker, enz.
* Start van _base box_ (minimale installatie)
* Configuratie ahv shell script, configuration management system
    * *Ansible*, CFEngine, Chef, Puppet, Salt

---

![Mitchell Hashimoto op Config Management Camp, Gent 2015](img/mitchell_hashimoto.jpg)

## Ansible

<http://www.ansible.com/>

* Configuration management system
* Beschrijf de gewenste toestand van je systeem (Yaml)
    * Ansible brengt systeem naar die toestand
    * Idempotent
* Herhaalbaar (dev -> qa -> prod)
* Schaalbaar (bv. Spotify: 1000'en servers)

## vb. Ansible playbook

```yaml
---
- hosts: webserver
  handlers:
    - name: restart httpd
      service:
        name: httpd
        state: restarted
  tasks:
    - name: Ensure Apache is installed
      yum:
        pkg: httpd
        state: installed
    - name: Ensure Apache is running
      service:
        name: httpd
        state: running
        enabled: true
    - name: Configure Apache
      template:
        src: httpd.conf
        dest: /etc/httpd/httpd.conf
      notify: restart httpd
```

# Opzetten server (vervolg)

## Stap 2

Open webbrowser, surf naar <http://192.168.56.77/>

## Er is geen stap 3

* Je hebt een werkende Linux webserver met MySQL databank en Wordpress
* Om de Wordpress-site te initialiseren, ga naar <http://192.168.56.77/wordpress/>
* Om de databank te beheren, ga naar <http://192.168.56.77/phpmyadmin/>

## VM gebruiken

* Afsluiten: `vagrant halt`
* Iets verkeerd gedaan? `vagrant destroy --force; vagrant up`
* Inloggen op de server kan via:
    * `vagrant ssh` (geen wachtwoord)
    * of `ssh vagrant@192.168.56.77` (wachtwoord vagrant)

## Vagrant >> Wamp/Xampp

* PHP, Java, Javascript, ... draaien in productie meestal op Linux-servers
* Ontwikkelingsomgeving moet zoveel mogelijk lijken op productie

## Waarom?

* Discussies: "Het werkte in dev, nu een probleem van ops"
* Ontbrekende libraries, oudere versies, ... in productie
* Bestanden op andere plaats (padnamen hard coded)
* Beveiligingsinstellingen in productie die er niet waren in dev
* ...

=> Ook een dev heeft noties van Linux nodig!

## State-of-the-art

* Infrastructure as code
* Test driven infrastructure
* Agile in operations (vb. Kanban)
* DevOps

=> Een sysadmin heeft ook skills van een ontwikkelaar nodig!

# Op verkenning in het systeem

## Inloggen

```
$ vagrant ssh
Last login: Fri Jun 19 09:08:31 2015 from 10.0.2.2
Welcome to your Packer-built virtual machine.
[vagrant@lampstack ~]$ pwd
/home/vagrant
[vagrant@lampstack ~]$ _
```

## Commando's

### command --options arguments

commando:

* Bash builtin
* uitvoerbaar bestand in `${PATH}` (doe `echo ${PATH}`)

## Opties

* veranderen het gedrag van een commando
* beginnen met `-` (kort, één letter) of `--` (lang, woord)
* aan elkaar hangen, vb. `ls -la` == `ls -l -a`
* kunnen ook argumenten hebben, vb. `cut -d:`, `cut --delimiter=:`
* let op voor uitzonderingen (bv. `find`)

## Argumenten

* "objecten" waar het commando op werkt
* vaak bestanden of directories

## Hulp zoeken

* man pages, bv. `man passwd`, `man 5 passwd`
* <http://explainshell.com/>
* Stack overflow ;-)
* Paul Cobbaut, [Linux Fundamentals](http://linux-training.be/) (boek)
* Tip: leg een [cheat sheet](https://github.com/bertvv/cheat-sheets) aan
* Mailtje sturen naar bert ;-)

## De UNIX-filosofie

Maak tools die één taak goed kunnen en laat ze samenwerken

## Oefening

* Paul Cobbaut, [deel III (first steps on the command line)](http://linux-training.be/funhtml/pt03.html)
* Waar vind je de configuratie van Apache?
* Waar op de server moeten we een website installeren?
* Wat zijn de netwerkinstellingen van de VM?
    * IP adres, default GW, DNS-server
* Kan je "pingen" tussen hostsysteem en VM?
* Installeer de laatste updates op de VM


# That's it!

## Bedankt!

Slides: <https://github.com/bertvv/linux-workshop-hogent>

Code: <https://github.com/bertvv/vagrant-example>

Meer op:

* Videolessen: <https://www.youtube.com/user/bertvvrhogent/>
* Github: <https://github.com/bertvv/>
* Ansible rollen: <https://https://galaxy.ansible.com/list#/users/8834>
* Twitter: [\@bertvanvreckem](https://twitter.com/bertvanvreckem)

![CC-BY](http://i.creativecommons.org/l/by/4.0/88x31.png)

