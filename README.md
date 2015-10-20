Full Stack Udacity Project 5
Victor Asselta
October 19th 2015
README.md

Project ip:
54.68.79.232

Project url:
http://54.68.79.232

SSH port:
2200

Summary of installation and configuration:

  All of this was taken from the inital root login and later the grader login .bash_profile files and my notes.
  I apologize if I skip around. I took advantage of being in root to stream line allot of work.
  
  I decided to use a singleton pattern with the apache server .conf and wsgi setup to keep things simple.

Installed Software:
finger, apache2, mod_wsgi, libapache2-mod-wsgi, git, python-pip, flask, python-psycopg2, sqlalchemy, oauth2client

1) download given ssh amazon key and copy contents to local .ssh directory in file named udacity_key.rsa

2) logged in as root on remote server.

3) added user grader and made added to sudoers after checking config in visudo

4) apt-get update, updated this list

5) apt-get upgrade, upgraded all with one exception. boot/grum/menu.lst gave a warning that a previous installation had been modified. I kept the original as I did not know if the modifications had been necessary for this project.

6) apt-get finger, because it was in the course and useful

7) added the user catalog

8) I should mention that after adding these users I created the associated .ssh/<name>.rsa files and chown them to corresponding owner.

9) checked permissions on these files, by default private key created with 600 access

10) login as grader

11) sudo vim etc/ssh/sshd_config .... set root log in to no, changed ssh port from 20 to 2200, disallowed password authentication (well, it was off be default)

12) sudo reboot

13) logged back in and cat sshd_config to make sure changed took

14) attempted root login in another terminal window, failed as expected

15) ufw: checked status, set defaults (deny incoming, allow outgoing), allow 2200/tcp, allow www, allow ntp

16) ufw checked status, enable, checked status

17) sudo dpkg-reconfigure tzdata, chose none, UTC

18) edited 000-default.config so apache would default to future ITS.wsgi file

19) created ITS directory in var/www to hold future application

20) began installation of above software list

21) installed and configured postgresql

22) checked pg_hba.conf, made sure that remote loging disabled. (configured by default)

23) cloned P3 to var/www/ITS, changed psycopg2 protocol from sqllite to postgresql and ITS.db to ITS

24) began lengthy process of updating files to new reality, changing some String types to Text, updating url of client_secrets.json file,...

25) created ITS.wsgi file and copied from working local copy created in previous vagrant file. I built the server locally first and tested my app.

26) began lengthy process of updating ITS database and associated roles

27) added psql users root, www-data, grader, catalog. Made grader superuser

28) created group ITS, added users www-data, catalog, grader

29) began lengthy process of running the app locally and updating each individual table and index permissions to ITS group.

30) created and activated ITS.conf file

31) had to change owner of several files including client_secrets.json and all ITS associated files.

32) set ITS.conf file to run app as grader to get around access issues.

33) system reboot

34) tested, fixed, tested, fixed, and so on and so fourth

35) updated the ITS application readme

Third party resources:
Over the course of this project I have used MANY. The initial configuration was something I've done before so some from memory. Ok very little from memory.
I used, and I don't think this is everything, stackoverflow(quite allot), docs for vagrant, apache2, postgresql, the udacity P5 forum: mostly "P5 How I got through it", and google generally.

Thank you for you time.
Victor Asselta
