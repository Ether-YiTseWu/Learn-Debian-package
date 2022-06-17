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
