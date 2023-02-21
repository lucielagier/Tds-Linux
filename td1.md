# TD1

## Exercise 1

1.  Go to the root directory
```
cd /
```
2. Display the content of the current (root) directory
```
ls 
```
3. Check your current location
```
pwd
```
4. Try to create a directory named test
```
mkdir test
```
Ne fonctionne pas!

5. Go to the general home directory (should contain folders named after
each user)
```

```
Ne peux pas être faite car on a pas differents "users"
6. Go to your home directory
```
cd home/
```
7. Go back to the general home directory (located "just above")
```
cd ..
```
8. Go again "just above", you should be back to the root directory
```
cd ..
```
9. Go directly to your home directory (named after you). It should be a
very simple command, which take no name as parameter of the path
```
cd 
```
10. Try to create a directory named test
```
cd /home/
mkdir test
```
12. Go into this new directory
```
cd test
```
12. Check your current location
```
pwd
```

## Exercise 2

1. Go to your home directory (should be named after you, you might be
there by default)
```
cd /home
```
2. Check your current location
```
pwd
```
3. Create a folder linux_ex_1
```
mkdir linux_ex_1
```
4. Go into this folder
```
cd linux_ex_1/
```
5. Create an empty text file named [first_name]_[last_name].txt (e.g. alexis_bogroff.txt)
```
vim lucie_lagier.txt
```
(pour en sortir echap puis ":wq")
6. Create a folder notes
```
mkdir notes
```
7. Move your text file into this folder
```
mv lucie_lagier.txt notes/
```
8. Rename the text file by appending the current year [first_name]_[last_name]_[current_year].txt
```
mv notes/lucie_lagier.txt notes/lucie_lagier_2023.txt
```
9. Make a copy of this folder, name it notes_2023
```
cp -r notes/ notes_2023
```
10. Delete the first folder (notes) using the verbose option
```
rm -rv notes
```

## Exercise 3

1. Create a script script_1.sh in the folder linux_ex_1
```
vim script_1.sh
```
2. In the script, write the commands that would output the following :
Script running please wait ...
Done.

On appuie sur "i" puis:
```
echo "Script running please wait ..."
echo "Done."
```
3. Quit editing and save the script
echap puis
```
:wq
```
4. Display the content of the script (using a command, not from an editor)
```
cat script_1.sh
```
5. Run the script
```
source script_1.sh
```

## Exercise 4: Accessing or modifying a file : permissions and root privilege

## Exercise 4:.1 Change the rights for accessing or modifying a file

1.  Create a file credentials in the folder linux_ex_1
```
cd linux_ex_1
touch credentials
```
(a) Write any kind of (fake) personal information within the file
```
blabla...
```
(b) Display the file content
```
cat credentials
```
(c) Display the current permissions
```
ls -l credentials
```

2. Change the current permissions to : read only for all users
```
chmod u=r creddentials
```
(a) Display the new permissions
```
ls -l credentials
```
(b) Modify and save the file
```
:wq
```
(c) Display the file content
```
cat credentials
```
3. Change the permissions back to read and write for all users
```
chmod ugo+rw credentials
```
(a) Display the new permissions
```
ls -l credentials
```
(b) Modify and save the file
```
:wq
```
(c) Display the file content
```
cat credentials
```
On the same file :
1. Add the execute permission to the owner
```
chmod u+x credentials
```
(a) Display the new permissions
```
ls -l creddentials
```
2. Remove the read permission to other users
```
chmod o-r credentials
```
(a) Display the new permissions
```
ls -l creddentials
```
3. Change the permissions to read, write and execute for all users
```
chmod u+rwx credentials
```
(a) Display the new permissions
```
ls -l creddentials
```

## Exercise 4:.2 Access root files

1. Go to the root folder
```
cd /
```
2. Create a file in root user mode named .private_file
```
sudo touch /.private_file
```
(a) Write some information in the file
```
sudo vi /.private_file
```
Puis on presse i, on écrit et":wq" 
(b) Display the file content
```
sudo cat /.private_file
```
(c) Display all the files in the folder including hidden files
```
sudo ls -a /
```
3. Modify the file in normal user mode
```
sudo chown lucie /.private_file
sudo chmod u+rwx /.private_file
```
(a) Write some new information in the file
```
#idem 
```
(b) Display the file content
```
sudo cat /.private_file
```
4. Modify the file in root user mode
```
sudo vi /.private_file
```
(a) Write some new information in the file
```
#idem
```
(b) Display the file content
```
sudo cat /.private_file
```
5. Change permissions to read, write and execute for all users

```
sudo chmod a+rwx /.private_file
```
(a) Modify the file content in normal user mode
```
#idem
```
(b) Display the file content
```
sudo cat /.private_file
```
## Exercise 4:.3 Change a file owner

1. Change permissions of .private_file to read and write for all users, in
normal user mode
```
sudo chown lucie .private_file
sudo chmod a+rw .private_file
```
2. Set the new file owner as the current user
```
sudo chown $USER .private_file
```
3. Change permissions of .private_file to read and write for all users, in
normal user mode
```
chmod a+rw .private_file
```

## Exercise 4:.4 Manage Packages (tools / functions)

1. Update your main package manager named apt
```
apt update
```
2. Upgrade apt
```
apt upgrade
```
3. Install the package cmatrix
```
apt install cmatrix
```
4. Launch cmatrix
```
cmatrix
```
5. Quit cmatrix
Press "Ctrl+c"
6. Install the package tmux
```
apt install tmux
```
7. Launch tmux
```
tmux
```
8. Say "Hello session 0" using bash in your current tmux session
```

```
9. Launch cmatrix in your current tmux session
```

```
10. Detach from the current tmux session (without stopping cmatrix)

Press "Ctrl+b" + "d"

11. Create a new tmux session
```
tmux new -s nv_session
```
12. Say "Hello session 1" using bash in your new tmux session
```

```
13. Detach from the current tmux session

Press "Ctrl+b" + "d"

14. List all running sessions
```
tmux ls
```
15. Attach again to session 0
```
tmux attach-session -t 0
```
16. Detach again

Press "Ctrl+b" + "d"

17. Attach again to session 1
```
tmux attach-session -t 1
```
18. Detach again

Press "Ctrl+b" + "d"

19. List all running sessions
```
tmux ls
```
20. Kill all tmux sessions and quit tmux
```
tmux kill-session -a
```
21. List all sessions
```
tmux ls
```

## Exercise 4:.5 Use functions arguments / parameters

1. Display the cmatrix help function
```
tmux -d
```
2. Launch cmatrix and make it display white characters (in place of the
green)
```

```
3. Re-launch cmatrix and slow down the speed of characters actualization
```

```
4. Stop cmatrix
```

```
5. Launch cmatrix with both :
— A slow speed of characters actualization
— Blue characters
```

```
6. Display cmatrix manual (different from the help notice)
```

```
7. Display the tmux help function 
```

```
8. Display the tmux manual
```

```
