# Week 2: Deep Dive into RHCSA Preparation

Hello everyone! Welcome to Week 2 of my Red Hat Certified System Administrator (RHCSA) preparation journey. This week, I focused on a variety of essential topics related to file permissions, SELinux, performance tuning, and scheduling tasks. Here's a detailed review of my learnings.

---

## Topics Covered This Week

### 1️⃣ **Control Access to Files**
- **Understanding File Permissions**: Learned how to manage file permissions using `chmod`, `chown`, and `chgrp` to control user access.
- **Default Permissions and File Access**: Explored `umask` for setting default permissions and practiced applying ACLs (Access Control Lists) for more granular file access control.
- **Hands-on Lab**: Gained practical experience by modifying permissions and testing scenarios for multi-user environments.

#### Code Snippets:
```bash
# Changing file ownership
sudo chown user:group filename

# Modifying permissions
chmod 755 filename

# Viewing current umask
umask

# Setting default permissions
umask 022

# Applying ACL to a file
setfacl -m u:username:rw file
```

### 2️⃣ **Manage SELinux Security**
- **SELinux Modes**: Learned about the three modes of SELinux:
  - **Enforcing**: Fully enforces the SELinux policy.
  - **Permissive**: Logs policy violations but does not enforce them.
  - **Disabled**: Completely turns off SELinux.
- **File Contexts and Booleans**: Adjusted file contexts using `chcon` and `restorecon` and managed booleans with `setsebool` for policy customization.
- **Troubleshooting SELinux**: Debugged access issues by analyzing logs in `/var/log/audit/audit.log` and using tools like `audit2allow`.

#### Code Snippets:
```bash
# Checking SELinux status
sestatus

# Changing SELinux mode
sudo setenforce 0   # Permissive mode
sudo setenforce 1   # Enforcing mode

# Adjusting file contexts
sudo chcon -t httpd_sys_content_t /var/www/html
restorecon -Rv /var/www/html

# Viewing audit logs
sudo tail -f /var/log/audit/audit.log
```

### 3️⃣ **Tune System Performance**
- **Process Management**:
  - Monitored processes using `top`, `htop`, and `ps`.
  - Killed unnecessary processes with `kill` and `pkill`.
- **Scheduling and Prioritizing**: Adjusted process priorities with `nice` and `renice` commands.
- **Performance Profiles**: Used `tuned` and `tuned-adm` to optimize the system for various workloads.

#### Code Snippets:
```bash
# Viewing processes
ps aux | grep process_name

# Killing a process
kill -9 PID

# Adjusting process priority
nice -n 10 command
renice -n 5 -p PID

# Applying a performance profile
tuned-adm list
sudo tuned-adm profile virtual-guest
```

### 4️⃣ **Schedule Future Tasks**
- **Recurring Jobs**:
  - Scheduled tasks using `cron` jobs by editing the `crontab` file.
  - Managed system-wide scheduled tasks via `/etc/cron.d/`.
- **One-time Jobs**: Utilized the `at` and `batch` commands for scheduling one-off tasks.
- **Temporary Files Management**: Practiced managing temporary files using `tmpwatch` and understanding their cleanup policies.

#### Code Snippets:
```bash
# Scheduling a cron job
crontab -e
# Example: Run backup.sh every day at midnight
0 0 * * * /path/to/backup.sh

# Listing cron jobs
crontab -l

# Scheduling a one-time job
at 2pm
> /path/to/script.sh

# Managing temporary files
sudo tmpwatch --mtime 24 /tmp
```

---

## Key Takeaways

### 🔑 File Permissions in Action
File permissions are critical for ensuring system security. By practicing with ACLs and default permissions, I now feel confident about tailoring access controls for multi-user environments.

### 🔐 SELinux Mastery
Working with SELinux was both challenging and rewarding. I understood how to:
- Resolve access denials by analyzing audit logs.
- Modify SELinux policies to meet specific requirements.

### 📊 Performance Tuning
The ability to monitor and optimize system performance is invaluable. Tuning profiles and process scheduling are tools I can see myself using often in real-world scenarios.

### 🕒 Task Scheduling Simplified
Scheduling tasks efficiently saves time and ensures important jobs are not missed. I practiced setting up automated backups and cleanup jobs using `cron` and `at` commands.

---

## Resources and Notes
I've attached my handwritten notes below, which include detailed examples, configurations, and command usages I practiced this week.

> 📝 **Handwritten Notes**: [Download Notes Here](https://www.linkedin.com/posts/vedantdomadiya_week2-rhcsa-linux-vedantdomaidya-activity-7273670223394676736-uulc?utm_source=share&utm_medium=member_desktop)

For an even deeper dive, check out my blog post with diagrams and additional insights:

[📖 Read the Blog on Medium](https://medium.com/@VedantDomadiya/week-2-deep-dive-into-rhcsa-preparation-a10517ae42e4)

---

## Let's Connect
If you're considering starting your RHCSA journey or have questions about the topics I covered, feel free to message me. I'd be happy to help you out!

Stay tuned for next week's updates! 🚀
