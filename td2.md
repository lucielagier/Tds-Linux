## Exercise 1: Access general computer informations 

1. Put system up to date
```
sudo apt update
```

2. Display 

— Linux version 
```
uname -a
```
— Current processes and memory usage associated 
```
top
```
— Display it in a more pleasant way ("more readable for humans") 
```
top | head -n 20 ; echo ; df -h ; echo ; lsblk ; echo ; lsusb ; echo ; uname -a ; echo ; hostname
```
— Number of processors 
```
nproc
```
— L1, L2 and L3 cache size 
```
lscpu | grep -E '^Thread|^Core|^Socket|^L1|^L2|^L3'
```
— Disk space — Monted devices 
```
df -h
```
— Connected usb devices 
```
lsusb
```
— Hostname 
```
hostname
```
## Exercise 2: Shell - Variables and scripts scope 

1. Create a variable x and assign it the short text piri pimpin 
```
x="piri pimpim"
```
2. Display the value of this variable
```
echo $x
```
3. Add to this value the following text piri pimpon It should contain the following : piri pimpim piri pimpon 
```
x="$x piri pimpon"
```
4. Create a folder named my_programs, then enter into that folder 
```
mkdir my_programs
cd my_programs

```
5. Create a script named pilou that displays pilou pilou 
```
echo "pilou pilou"
```
6. Run this script 
```
./pilou
```
7. Make this script executable
```
chmod +x pilou
```
 8. Run the script by writting its name only 
```
pilou
```
9. Programs called from the terminal are usually found thanks to a variable named PATH Display the content of the variable PATH 
```
echo $PATH
```
10. Add the path of your current location to the global variable PATH 
```
export PATH=$PATH:/path/to/current/location
```
11. When you are sure of the result, export it 
```
export PATH
```
12. Go to your home directory 
```
cd ~
```
13. Run your script by writting its name only 
```
pilou
```
14. Change the value of the PATH in the .profile file in order to make it permanent 
```
echo 'export PATH=$PATH:/path/to/current/location' >> ~/.profile
```
15. Create a new shell and run your script using its name only 
```
bash
pilou
```
## Exercise 3: Scheduling task - daemon 
1. Create a script say_hello.sh 
— Make it write the current date and time followed by ’Hello’ 1 
— It should write it in a file named ’hellos.txt’ 
— Each new output should be appened to the file (it shouldn’t remove previous hellos) 
```
echo "$(date) Hello 1" >> hellos.txt
```
2. Make the script executable 
```
chmod +x say_hello.sh
```
3. Use crontab to schedule the running of the script every minute 
```
crontab -e

```
## Exercise 4: Hashing
1. Create a folder named hash_checksum. Go into this folder 
```
mkdir hash_checksum
cd hash_checksum
```
2. Inside this folder, create two files named .sensible_addresses and .sen sible_passwords 
```
touch .sensible_addresses .sensible_passwords
```
3. Display the list of files of the folder 
```
ls -a
```
4. Still inside the folder hash_checksum, create a script named gentle_script.sh. This script should display the following text "Have a good day" 
```

```
5. Run the script 
```
./gentle_script.sh
```
6. Compute the sha256sum of gentle_script. Store it into a file named log_sha 
```
sha256sum gentle_script.sh > log_sha
```
7. Now corrupt the file by adding a line of code that deletes any file starting with : ".sensible" 
```
echo 'rm -f .sensible*' >> gentle_script.sh
```
8. Compute again the sha256sum of gentle_script. Store it into the log_sha file 
```
sha256sum gentle_script.sh > log_sha
```
9. Run the script 
```
./gentle_script.sh
```
10. Display again the list of files of the folder 
```
ls -a
```
11. Display the log_sha content : are the hashes any different ? 
```
cat log_sha
```
 Diferrent car le contenu a changé!
 
## Exercise 5: Compressing 
1. Install the QPDF free command-line program. Part of this program is the zlib-flate command that compress and un compress files using the deflate algorithm. 
```
sudo apt-get install qpdf
```
2. Create a directory "compress", go into this directory 
```
mkdir compress
cd compress
```
3. Create a first file "hello" whose content is "Hello" 
```
echo "Hello" > hello
```
4. Compute the deflate compression (level 1) of this file. Store the compres sed file size into a file log_compress
```
zlib-flate -1 < hello > hello.deflate
ls -l hello.deflate | awk '{print $5}' > log_compress
```
5. Create a second file "hello_multiple" whose content is 1000 lines of "Hello" 2 
```
yes "Hello" | head -n 1000 > hello_multiple
```
6. Compute the deflate compression (level 1) of this file. Store the compres sed file size into a file log_compress 
```
zlib-flate -1 < hello_multiple > hello_multiple.deflate
ls -l hello_multiple.deflate | awk '{print $5}' >> log_compress
```
7. Create a third file "hello_mulitple_i" whose content is 1000 lines of "Hello i" (i varying from 1 to 100)
```
for i in {1..100}; do echo "Hello $i"; done > hello_multiple_i
```
8. Compute the deflate compression (level 1) of this third file. Store the compressed file size into log_compress 
```
zlib-flate -1 < hello_multiple_i > hello_multiple_i.deflate
ls -l hello_multiple_i.deflate | awk '{print $5}' >> log_compress
```
9. Display the content of log_compress 
```
cat log_compress
```

## Exercise 6: ACLs : Access Control Lists 

1. Create users — Create a user named client_1 with password passwd-client_1 — Create two other users named contributor_1 and contributor_2 with respective passwords passwd-contributor_1 and passwd-contributor_2 
```
sudo adduser client_1
sudo adduser contributor_1
sudo adduser contributor_2
```
(on ajoute les mdp à chaque exeecution)
2. Create groups — clients — contributors 
```
sudo addgroup clients
sudo addgroup contributors
```
3. Add users to their respective group 
```
sudo usermod -aG clients client_1
sudo usermod -aG contributors contributor_1
sudo usermod -aG contributors contributor_2
```
4. Check the users and groups have been successfully created 
```
groups client_1
groups contributor_1
groups contributor_2
```
5. Create a folder lika_project and give it the following authorizations to groups — clients : read — contributors : read and write 
```

```
6. Also use the command ls -l and notice the change on lika_project folder 
```
```
7. Change user and become as a client, then try deleting the folder 
```
```
8. Now change user and become as a contributor, then try deleting the folder 
```
```
9. Check who is the current user
```
```

