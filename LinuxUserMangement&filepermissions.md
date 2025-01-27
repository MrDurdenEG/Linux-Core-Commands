# User Management

### Create a New User

 `sudo useradd testuser`

### Set or Change the User Password

`sudo passwd testuser`

### Create a New Group

`sudo groupadd testgroup`

### Add a User to a Group

`sudo gpasswd -a testuser testgroup`

### Remove a User

`sudo userdel testuser`

### Remove a Group

`sudo groupdel testgroup`

---

## SU and SUDO

### `su` (Switch User)

- **Switch to Another User:**
  `su testuser`

- **Switch as the User Logged In Directly (with their environment):**
  `su - testuser`

- **Execute a Specific Command as Another User:**

  `su - testuser -c "command"`

### `sudo` (Execute Commands as Administrator)

- Prepend `sudo` to run commands with administrative privileges:

  `sudo <command>`

---

### Important Notes:

- Use `sudo` for commands related to user and group management, password changes, and other administrative tasks.
- `su` is used for switching users, but `sudo` is preferred for running administrative tasks.

-------

# Linux File Permissions Guide 

## 1. Permission Types

### There are three types of permissions:

Read (r): Allows viewing the contents of a file or listing the contents of a directory.

Write (w): Allows modifying a file or adding/removing files in a directory.

Execute (x): Allows executing a file (if it's a program or script) or accessing a directory


---

## 2. Permission Groups

### Permissions are assigned to three groups:

Owner: The user who owns the file or directory.

Group: The group that owns the file or directory.

Others: All other users who are not the owner or part of the group.


---

#### Use the `ls -l` command to view file permissions

`-rw-r--r-- 1 user group 4096 Oct 10 12:34 file.txt`

`drwxr-xr-x 2 user group 4096 Oct 10 12:34 directory `

**The first character indicates the file type (- for regular files, d for directories).**

The next 9 characters represent permissions for the owner, group, and others (in that order).

**`-rw-r--r--` means:**

Owner: Read and Write (rw-)

Group: Read (r--)

Others: Read (r--)

---

### to change the Permissions
`sudo chmod [who][operator][permissions] file`

#### Who:
- `u`: Owner
- `g`: Group
- `o`: Others
- `a`: All (default)

#### Operator:
- `+`: Add permission
- `-`: Remove permission
- `=`: Set permission explicitly

#### Permissions:
- `r`: Read
- `w`: Write
- `x`: Execute

##### Example:

`sudo chmod u+rw file.txt`     

**Add read and write for the owner**

## We can also edit file permissions using the `chmod` command. For example:  

### **`chmod 777`**  
This corresponds to a permission level for:  
- **Owner** (first digit)  
- **Group** (second digit)  
- **Others** (third digit)  

Each digit is the sum of:  
- **4** = Read (`r`)  
- **2** = Write (`w`)  
- **1** = Execute (`x`)  

#### Examples of Permissions:  
- **`7`** = Read + Write + Execute (4 + 2 + 1)  
- **`5`** = Read + Execute (4 + 1)  
- **`0`** = No permissions  

### Common Examples of `chmod` Commands:

1. **`chmod 777 filename`**  
   - **Owner, Group, Others**: Full permissions (Read + Write + Execute).  
   - **Use Case**: Makes the file accessible and modifiable by everyone.  

2. **`chmod 700 filename`**  
   - **Owner**: Full permissions (Read + Write + Execute).  
   - **Group, Others**: No permissions.  
   - **Use Case**: Protects files for the owner's exclusive access.  

3. **`chmod 764 filename`**  
   - **Owner**: Full permissions (Read + Write + Execute).  
   - **Group**: Read + Write.  
   - **Others**: Read-only.  
   - **Use Case**: Collaborative editing for group members, read-only for others.  

4. **`chmod 755 filename`**  
   - **Owner**: Full permissions (Read + Write + Execute).  
   - **Group, Others**: Read + Execute.  
   - **Use Case**: For scripts/programs—owner can modify, others can execute.  

5. **`chmod 644 filename`**  
   - **Owner**: Read + Write.  
   - **Group, Others**: Read-only.  
   - **Use Case**: Protects the file's content while allowing others to view it.  

These examples provide a flexible way to manage file access and security.
