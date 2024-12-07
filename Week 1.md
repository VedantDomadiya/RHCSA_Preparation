---

# Week 1: RHCSA Preparation - Access Systems, Manage Files, and User Administration  

As I dive into my preparation for the **Red Hat Certified System Administrator (RHCSA)** exam, I’m sharing my weekly learning highlights. This week was all about accessing systems, managing files, and user administration. I’ve attached my detailed handwritten notes at the end for those who prefer a visual approach!  

---

## Table of Contents  
1. [Access Systems and Get Support](#access-systems-and-get-support)  
   - [SSH Without a Password or Passphrase](#ssh-without-a-password-or-passphrase)  
2. [Manage Files from the Command Line](#manage-files-from-the-command-line)  
   - [Linux File System Hierarchy](#linux-file-system-hierarchy)  
   - [Hard Links vs. Soft Links](#hard-links-vs-soft-links)  
3. [Manage Local Users and Groups](#manage-local-users-and-groups)  
   - [Understanding `/etc/shadow`](#understanding-etcshadow)  
   - [Using the `chage` Command](#using-the-chage-command)  

---

## 1. Access Systems and Get Support  

### SSH Without a Password or Passphrase  
One of the first things I focused on was setting up **password-less SSH authentication**, a critical step for seamless server access.  

1. **Generate an SSH Key Pair**:  
   ```bash
   ssh-keygen -t rsa -b 4096
   ```  
   Leave the passphrase field blank for a seamless login experience.  

2. **Copy the Public Key to the Server**:  
   ```bash
   ssh-copy-id user@remote-server
   ```  

3. **Test the Configuration**:  
   ```bash
   ssh user@remote-server
   ```  

This setup enhances security and eliminates the need for repeated password entry during SSH logins.  

---

## 2. Manage Files from the Command Line  

### Linux File System Hierarchy  
Here are some essential directories and their purposes:  
- `/bin`: Contains essential binaries, like `ls` and `cp`.  
- `/etc`: Stores system configuration files, including `/etc/passwd` and `/etc/shadow`.  
- `/var`: Variable files like logs and mail.  
- `/home`: Houses user-specific directories and data.  

### Hard Links vs. Soft Links  

| **Feature**         | **Hard Link**                                   | **Soft Link (Symlink)**                        |  
|----------------------|------------------------------------------------|-----------------------------------------------|  
| **Definition**       | A direct reference to file data.               | A pointer to another file or directory.       |  
| **Updates**          | Changes to the original file affect the link.  | Dependent on the existence of the original.   |  
| **Cross Filesystems**| Cannot cross filesystem boundaries.            | Can link across different filesystems.        |  
| **Command**          | `ln original_file hard_link_name`              | `ln -s original_file symlink_name`            |  

These links are incredibly useful for organizing and managing files efficiently.  

---

## 3. Manage Local Users and Groups  

### Understanding `/etc/shadow`  
The `/etc/shadow` file plays a critical role in Linux user management. Each line represents a user account and includes:  

- **`username`**: The login name.  
- **`encrypted_password`**: Stores the hashed password.  
- **`last_change`**: Number of days since the password was last changed.  
- **`min_days`**: Minimum days required before a password change.  
- **`max_days`**: Maximum number of days a password is valid.  
- **`warn`**: Warning period before password expiration.  
- **`inactive`**: Days of inactivity before the account is disabled.  
- **`expire`**: Account expiration date.  

### Using the `chage` Command  
The `chage` command helps manage user password policies.  

#### Common Use Cases:  
1. **View Password Policies**:  
   ```bash
   chage -l username
   ```  

2. **Set Maximum Password Age**:  
   ```bash
   chage -M 60 username
   ```  

3. **Force Immediate Password Change**:  
   ```bash
   chage -d 0 username
   ```  

---

## Additional Resources  

For a more detailed understanding, check out the notes and diagrams attached. The visual representation should make these concepts even easier to grasp!  

📄 **Handwritten Notes**: [Attached in the file](#)  
🖼️ **Illustrations and Diagrams**: [Available in the PDF](#)  

Stay tuned for Week 2, where I’ll explore more advanced topics in system administration! 🚀  

---  
