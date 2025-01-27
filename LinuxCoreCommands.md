# Linux Core Commands

---

## pwd: Current Working Directory
---

## ls: List Files and Directories
- `ls /home`
- `ls -a`: Show all the dirs and files in the current dir you are in, including hidden files.
- `ls -l`: Show in long list (info like date, edit date, user, and permissions, etc.).
- `ls -al`: Combine commands above.
- `ls [DIR]`: Show the directories in the `[DIR]` you specify.
- `ls -ltrh`: Show all info about files with details.
- `ls f*`: To show files/dirs starting with `f` (or any letter you specify).
- `ls *f`: To show files/dirs ending with `f` (or any letter you specify).
- `ls *.txt`: To show `.txt` files.
- `ls [a-z]*`: To show files/dirs starting with letters A-Z.
- `ls *[a-z]`: To show files/dirs ending with letters A-Z.

---

## cd: Change Current Directory
- `cd /home/documents`: Go to `/home/documents`.
- `cd ~`: Move to the main directory (`/`).
- `cd -`: Move to the last directory used (e.g., `/home/user/Desktop`).
- `cd ..`: Move one step back.
- `cd ../../`: Move two steps back.

---

## cp: Copy Files
- `cp [file1.txt] [file2.txt]`: Copy `[file1.txt]` to `[file2.txt]`.
- `cp -r [dir1] [dir2]`: Copy directory `[dir1]` recursively to `[dir2]`.

---

## mv: Move or Rename Files or Directories
- `mv [file1.txt] [/home/documents/]`: Move (cut) `[file1.txt]` to `/home/documents/`.
- `mv [oldname.txt] [newname.txt]`: Rename `[oldname.txt]` to `[newname.txt]`.
- `mv [oldname.txt] [New_Dir]/[NewName.txt]`: Move(cut) `[oldname.txt]` to `[New_Dir]` and rename it to `[NewName.txt]`.

---

## rmdir: Remove Empty Directory
- `rmdir [dir]`

---

## mkdir: Create Directory
- `mkdir [new_dir]`: Create a directory named `[new_dir]`.

---

## cat: Print the File Content
- `cat [file.txt]`: Display the content of `[file.txt]`.
- `cat [file1.txt] [file2.txt]`: Concatenate and display `[file1.txt]` and `[file2.txt]`.
- `cat > [file.txt]`: Create a file and write in it (`CTRL+C` to save).
- `cat [oldfile.txt] > [newfile.txt]`: Create a new file with the same content as `[oldfile.txt]`.

---

## grep: Search Text in Files
- `grep "any_word" [file.txt]`: Search for `"any_word"` in `[file.txt]`.
- `grep -i "any_word" [file.txt]`: Case-insensitive search.
- `grep "any_word" [file1.txt] [file2.txt]`: Search in multiple files.
- `grep -r "any_word" [DIR]`: Search recursively in all files under `[DIR]`.
- `grep -A 2 "any_word" [file.txt]`: Show 2 lines after each match.
- `grep -B 2 "any_word" [file.txt]`: Show 2 lines before each match.
- `grep -C 2 "any_word" [file.txt]`: Show 2 lines before and after each match.

---

## head: Display the First Lines of a File
- `head [file.txt]`: Display the first 10 lines of `[file.txt]`.
- `head -n 5 [file.txt]`: Display the first 5 lines of `[file.txt]`.
- `head -n 5 [file.txt] [file2.txt]`: Display the first 5 lines of `[file.txt] and [file2.txt]`.

---

## tail: Display the Last Lines of a File
- Same as `head` but displays the last lines instead of the first.

---

## less: Display File Content Page by Page
- `less [file.txt]`: Press `Enter` to continue viewing.

---

## ps aux: Display All Processes in the System
- (like task manager)

---

## isof: Display List of All Open Files
- `isof -i`: Display files with internet addresses (e.g., temp files).

---

## netstat: Display Network Connections
- `netstat -a`: Shows all active connections and listening ports.
- `netstat -at`: Shows all active TCP connections.
- `netstat -antp`: Shows a list of all TCP connections (established and listening)
- along with their numerical addresses and the associated process information

---

## ifconfig: Show Details About Network Interfaces
- Use with `sudo`: `sudo ifconfig`.

---

## sort: Sort Lines of Text Files
- `sort [file.txt]`: Sorts lines alphabetically.
- `sort -n [file.txt]`: Sorts lines numerically.
- `sort -r [file.txt]`: Sorts lines in reverse order.

---

## uniq: Remove Duplicate Lines
- First sort the file: `sort [file.txt]`.
- Remove duplicates: `uniq [file.txt]`.
- Show duplicates only: `uniq -d [file.txt]`.

---

## stat: Display Information About a File
- `stat [file.txt]`: Show size, permissions, and timestamps.
- `stat -c "%A %s %n" [file.txt]`: Custom format: 
  - `%A`: Permissions
  - `%s`: Size
  - `%n`: Name
  - `%y`: last modification time
---

## ping: Test Network Connectivity
- `ping [google.com]`: Send ICMP requests to `[google.com]`.
- `ping -c 4 [google.com]`: Send 4 ICMP requests.

---

## whoami: Display Current User
- `whoami`

---

## passwd: Change Password
- `passwd`: Change current user's password.
- `sudo passwd [username]`: Change another user's password.

---

## kill: Terminate a Process
- Use `ps aux` to find the process ID (PID).
- `kill [1856]`: Terminate process by PID.
- `kill -9 [1234]`: Forcefully terminate process by PID.
- `pkill [process_name]`: Terminate process by name.

---

## find: Search Files and Directories
- `find [DIR] -name [filename.txt]`: Search for a file in `[DIR]`.
- `find [DIR] -type d -name [dirname]`: Search for directories in `[DIR]`.
- `find [DIR] -type f `: Search for directories in `[DIR]`.
- `find [DIR] -name [*.txt] `: Search for files with `".txt"` extension in `[DIR]`.
- `find / -name [file.txt]`: Search the entire system (use `sudo`).
- `find [DIR] -name ["*report*"]`: Search for files containing `"report"` in their names.

---

## nano: Text Editor
- `nano [filename.txt]`: Open file for editing (or create if it doesn’t exist).
- `nano [file1.txt] [file2.txt]`:open multiply files.
- Save: `CTRL+O`, Exit: `CTRL+X`.
- `nano -l [filename.txt]`: Open file and display line numbers.

---

## ln: Create Links (Shortcuts)
- **Hard Link**: `ln [source_file] [link_name]`
        It essentially creates another name for the same file
        Deleting the original file does not affect the hard link, as the data remains accessible through the hard link.
- **Soft Link**: `ln -s [file.txt] [link.txt]`.
        (most like pointer in C language)
        If the original file is deleted, the soft link becomes a "dangling link" and will no longer work
        it works too with directories

---
note

-any name inside [] can be changeable and we don't write the '[]' just the name