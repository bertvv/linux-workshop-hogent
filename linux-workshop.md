% Linux Workshop
% Bert Van Vreckem
% Vakgroep Informatica, HoGent, 2015-06-22

## Voor we beginnen

Installeer

* Git (incl. Git Bash) <https://git-scm.com/downloads>
* VirtualBox <https://www.virtualbox.org/wiki/Downloads>
    * incl. "Extension pack"
* Vagrant <https://www.vagrantup.com/downloads.html>

## Agenda

* Demo + hands-on: opzetten LAMP stack
* Basistaken Linux systeembeheer

# Opzetten server

## Stap 1

In een Bash shell, doe:

```ShellSession
$ mkdir workshop-linux
$ cd workshop-linux
$ git clone https://github.com/bertvv/lampstack
$ cd lampstack
$ vagrant up
```

# Intermezzo

## Tools

* VirtualBox
* Vagrant
* Ansible

## VirtualBox

Netwerk:

* NAT, NatNetwork
* Bridged
* Host-only
* Internal


# Opzetten server (vervolg)

## Stap 2

Open webbrowser, surf naar <http://192.168.56.77/>

## Er is geen stap 3

* Je hebt een werkende Linux webserver met MySQL databank
* Bestanden (PHP, HTML) in de `www/`-map kan je bekijken via de browser
* Om de databank te beheren, ga naar <http://192.168.56.77/phpmyadmin/>
* Om Drupal te activeren, ga naar <http://192.168.56.77/drupal7/install.php>

# That's it!

## Bedankt!

Slides: <https://github.com/bertvv/linux-workshop-hogent>

Code: <https://github.com/bertvv/vagrant-example>

Meer op:

* Videolessen: <https://www.youtube.com/user/bertvvrhogent/>
* Github: <https://github.com/bertvv/>
* Ansible rollen: <https://https://galaxy.ansible.com/list#/users/8834>
* [\@bertvanvreckem](https://twitter.com/bertvanvreckem)

![CC-BY](http://i.creativecommons.org/l/by/4.0/88x31.png)

