
joona@Kone:~$ sudo systemctl status apache2
[sudo] password for joona: 
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; preset: enab>
     Active: active (running) since Tue 2025-01-28 17:48:44 EET; 22min ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 3598 (apache2)
      Tasks: 55 (limit: 13905)
     Memory: 21.0M
        CPU: 205ms
     CGroup: /system.slice/apache2.service
             ├─3598 /usr/sbin/apache2 -k start
             ├─3599 /usr/sbin/apache2 -k start
             └─3600 /usr/sbin/apache2 -k start

tammi 28 17:48:44 Kone systemd[1]: Starting apache2.service - The Apache HTTP S>
tammi 28 17:48:44 Kone apachectl[3597]: AH00558: apache2: Could not reliably de>
tammi 28 17:48:44 Kone systemd[1]: Started apache2.service - The Apache HTTP Se>
...skipping...
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; preset: enab>
     Active: active (running) since Tue 2025-01-28 17:48:44 EET; 22min ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 3598 (apache2)
      Tasks: 55 (limit: 13905)
     Memory: 21.0M
        CPU: 205ms
     CGroup: /system.slice/apache2.service
             ├─3598 /usr/sbin/apache2 -k start
             ├─3599 /usr/sbin/apache2 -k start
             └─3600 /usr/sbin/apache2 -k start

tammi 28 17:48:44 Kone systemd[1]: Starting apache2.service - The Apache HTTP S>
tammi 28 17:48:44 Kone apachectl[3597]: AH00558: apache2: Could not reliably de>
tammi 28 17:48:44 Kone systemd[1]: Started apache2.service - The Apache HTTP Se>
~
~
joona@Kone:~$ cd ..
joona@Kone:/home$ cd ..
joona@Kone:/$ cd var
joona@Kone:/var$ cd log
joona@Kone:/var/log$ ls
alternatives.log  boot.log.6      journal              vboxadd-setup.log.2
apache2           boot.log.7      lastlog              vboxadd-setup.log.3
apt               bootstrap.log   lightdm              vboxadd-setup.log.4
atop              btmp            private              wtmp
boot.log          cups            README               Xorg.0.log
boot.log.1        dpkg.log        speech-dispatcher    Xorg.0.log.old
boot.log.2        exim4           unattended-upgrades  Xorg.1.log
boot.log.3        faillog         vboxadd-install.log  Xorg.1.log.old
boot.log.4        firebird        vboxadd-setup.log
boot.log.5        fontconfig.log  vboxadd-setup.log.1
joona@Kone:/var/log$ sudo ls
alternatives.log  boot.log.6	  journal	       vboxadd-setup.log.2
apache2		  boot.log.7	  lastlog	       vboxadd-setup.log.3
apt		  bootstrap.log   lightdm	       vboxadd-setup.log.4
atop		  btmp		  private	       wtmp
boot.log	  cups		  README	       Xorg.0.log
boot.log.1	  dpkg.log	  speech-dispatcher    Xorg.0.log.old
boot.log.2	  exim4		  unattended-upgrades  Xorg.1.log
boot.log.3	  faillog	  vboxadd-install.log  Xorg.1.log.old
boot.log.4	  firebird	  vboxadd-setup.log
boot.log.5	  fontconfig.log  vboxadd-setup.log.1
joona@Kone:/var/log$ sudo tail -f /var/log/apache2/error.log
[Tue Jan 28 17:48:44.858396 2025] [mpm_event:notice] [pid 3598:tid 3598] AH00489: Apache/2.4.62 (Debian) configured -- resuming normal operations
[Tue Jan 28 17:48:44.858501 2025] [core:notice] [pid 3598:tid 3598] AH00094: Command line: '/usr/sbin/apache2'
^C
joona@Kone:/var/log$ sudo tail -f /var/log/apache2/access.log
127.0.0.1 - - [28/Jan/2025:17:49:08 +0200] "GET / HTTP/1.1" 200 10956 "-" "curl/7.88.1"

