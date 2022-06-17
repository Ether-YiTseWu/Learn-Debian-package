# Learn-Debian-package
Canonical interview take home test

# Task
1. Get the source code of that Debian package.
2. Add an executable bash script called “testing.sh”
   Executing testing.sh will echo “this is a test from Yi-Tse Wu ” on the console.
3. Please echo string “this is a test from Yi-Tse Wu” during the Debian package installation time.
4. Host all of your change to a public git repository (e.g. launchpad git, Github or GitLab)
5. Dput the source change to your ppa.
6. Install your package from your ppa.
7. Past the message printed by the installation.
   The string “this is a test from Yi-Tse Wu” is expected.
8. Past the executing result of  `dpkg -S testing.sh; testing.sh`
   The string “this is a test from {your name}” is expected.
9. Record things that you experienced for this task on this mail as a document.
   Image the steps is to guide people who did not experience this task to finish this task.

# My Solution
## Step 1
1.	sudo nano /etc/apt/sources.list
2.	Uncomment the third line
3.	sudo spt-get update
4.	apt-get source hello

## Step 2
1.	Create a shell named testing.sh in /hello-2.10/src which contains just one line script, echo "this is a test from Yi-Tse Wu"

## Step 3
1.	Create a file named “postinst” in /hello-2.10/debian
2.	Write a command, echo "this is a test from Yi-Tse Wu", in postinst
3.	Create a file named “install” in /hello-2.10/debian 
4.	Write a command, src/testing.sh usr/bin, in install
5.	Delete a file named “format” in /hello-2.10/Debian/source
6.	debuild -us -uc (for test)
7.	sudo dpkg -i hello_2.10-2_armhf.deb (for test)
8.	debuild -S (for uploading to launchpad)
9.	debsign -k <MYKEY> hello_2.10-2_source.changes (for uploading to launchpad)

## Step 4
1.	Add the computer SSH key into Github
2.	git config --global user.email tailer954@gmail.com
3.	git config --global user.name "Steven-YiTseWu"
4.	git init 
5.	git add -A 
6.	git commit -m 'Added my project' 
7.	git remote add origin git@github.com:Steven-YiTseWu/Learn-Debian-package.git 
8.	git branch -m master main
9.	git push -f origin main
 
## Step 5
1.	Create a launchpad account and build a PPA named yitse-hello
2.	Generate GPG Key and send it to ubuntu server   
   A.	gpg --gen-key    
   B.	gpg –fingerprint
   C.	gpg --keyserver hkps://keyserver.ubuntu.com --send-keys myKey
3.	Upload the fingerprint to PPA, and verify it according to mail send by launchpad
4.	Upload the SSH key to launchpad
5.	Install dput, sudo apt-get install dput
6.	Install debuild, sudo apt-get install devscripts build-essential lintian
7.	sudo nano ~/.dput.cf
8.	dput -f my-ppa hello_2.10-2_source.changes

## Step 6
1.	sudo add-apt-repository ppa:stevenyitsewu/yitse-hello
2.	sudo apt update
3.	sudo apt-cache policy hello, find two same name packages
4.	sudo apt install hello=2.10-2
5.	dpkg -S testing.sh; testing.sh
