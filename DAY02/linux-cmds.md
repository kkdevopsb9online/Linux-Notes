# Linux Commands for DevOps Engineers (Part 2)

# 11. `top` — Monitor Running Processes

## Purpose

Displays real-time running processes, CPU usage, memory usage, and system load.

---

# Syntax

```bash
top
```

---

# Important Shortcuts Inside top

```bash
P   # Sort by CPU usage
M   # Sort by Memory usage
k   # Kill a process
q   # Quit top
```

---

# Real-Time DevOps Use Case

Monitoring server performance during production incidents.

```bash
top
```

Check:
- High CPU processes
- Memory-consuming applications
- Zombie processes
- Load average

---

# Interview Explanation

`top` is a real-time system monitoring tool used heavily in production troubleshooting. DevOps engineers use it to identify performance bottlenecks and resource-heavy applications.

---

# 12. `ps` — Display Running Processes

## Purpose

Shows currently running processes.

---

# Syntax

```bash
ps [options]
```

---

# Common Examples

```bash
ps -ef
ps aux
ps -ef | grep nginx
```

---

# Real-Time DevOps Use Case

Checking whether services are running correctly.

```bash
ps -ef | grep java
```

---

# Interview Explanation

`ps` is widely used to inspect process details such as PID, parent process, CPU usage, and execution state. It is commonly combined with `grep`.

---

# 13. `df` — Check Disk Space Usage

## Purpose

Displays filesystem disk space usage.

---

# Syntax

```bash
df [options]
```

---

# Common Examples

```bash
df -h
df -Th
```

---

# Real-Time DevOps Use Case

Monitoring production server disk utilization.

```bash
df -h
```

Useful for:
- Disk alerts
- Storage troubleshooting
- Kubernetes node monitoring

---

# Interview Explanation

`df -h` is one of the first commands used during server health checks to identify low disk space issues.

---

# 14. `du` — Check Directory/File Size

## Purpose

Displays file and directory sizes.

---

# Syntax

```bash
du [options] path
```

---

# Common Examples

```bash
du -sh /var/log
du -sh *
du -ah
```

---

# Real-Time DevOps Use Case

Finding directories consuming large storage.

```bash
du -sh /opt/*
```

---

# Interview Explanation

`du` is commonly used with `df` to identify which folders consume excessive storage in Linux servers.

---

# 15. `chmod` — Change File Permissions

## Purpose

Modifies file and directory permissions.

---

# Syntax

```bash
chmod permissions file_name
```

---

# Common Examples

```bash
chmod 755 script.sh
chmod +x deploy.sh
chmod -R 755 app/
```

---

# Permission Breakdown

```bash
7 = rwx
5 = r-x
4 = r--
```

Example:

```bash
755
```

Means:
- Owner → Read, Write, Execute
- Group → Read, Execute
- Others → Read, Execute

---

# Real-Time DevOps Use Case

Making deployment scripts executable.

```bash
chmod +x deploy.sh
```

---

# Interview Explanation

`chmod` is essential for Linux security and automation. DevOps engineers use it frequently while handling scripts, SSH keys, and deployment files.

---

# 16. `chown` — Change File Ownership

## Purpose

Changes file or directory owner and group.

---

# Syntax

```bash
chown user:group file_name
```

---

# Common Examples

```bash
chown nginx:nginx app.log
chown -R ubuntu:ubuntu /opt/app
```

---

# Real-Time DevOps Use Case

Fixing permission issues after deployments.

```bash
chown -R tomcat:tomcat /opt/tomcat
```

---

# Interview Explanation

Incorrect ownership causes application access failures. DevOps engineers frequently use `chown` while configuring web servers, CI/CD pipelines, and shared directories.

---

# 17. `tail` — View Last Lines of a File

## Purpose

Displays the last lines of a file.

---

# Syntax

```bash
tail [options] file_name
```

---

# Common Examples

```bash
tail app.log
tail -f app.log
tail -100 app.log
```

---

# Real-Time DevOps Use Case

Real-time log monitoring.

```bash
tail -f catalina.out
```

Very common during:
- Production debugging
- Kubernetes troubleshooting
- Deployment monitoring

---

# Interview Explanation

`tail -f` is one of the most frequently used commands by DevOps engineers for monitoring live logs.

---

# 18. `head` — View First Lines of a File

## Purpose

Displays first lines of a file.

---

# Syntax

```bash
head [options] file_name
```

---

# Common Examples

```bash
head app.log
head -20 app.log
```

---

# Real-Time DevOps Use Case

Checking configuration file headers or startup logs.

```bash
head -50 nginx.conf
```

---

# Interview Explanation

`head` is useful for quickly inspecting large files without opening the entire content.

---

# 19. `awk` — Text Processing Tool

## Purpose

Processes and extracts structured text data.

---

# Syntax

```bash
awk 'pattern {action}' file
```

---

# Common Examples

## Print First Column

```bash
awk '{print $1}' file.txt
```

---

## Print Username from passwd File

```bash
awk -F: '{print $1}' /etc/passwd
```

---

## Print Specific Columns

```bash
df -h | awk '{print $1, $5}'
```

---

# Real-Time DevOps Use Case

Extracting metrics from logs and command outputs.

```bash
kubectl get pods | awk '{print $1}'
```

---

# Interview Explanation

`awk` is heavily used in shell scripting and automation for parsing structured command outputs efficiently.

---

# 20. `sed` — Stream Editor

## Purpose

Used for searching, replacing, editing, and transforming text.

---

# Syntax

```bash
sed 's/old/new/' file
```

---

# Common Examples

## Replace Text

```bash
sed 's/dev/prod/' config.txt
```

---

## Replace Globally

```bash
sed 's/error/warning/g' app.log
```

---

## Edit File Directly

```bash
sed -i 's/8080/9090/g' application.properties
```

---

# Real-Time DevOps Use Case

Updating configuration files dynamically during deployments.

```bash
sed -i 's/IMAGE_TAG=v1/IMAGE_TAG=v2/g' .env
```

---

# Interview Explanation

`sed` is commonly used in automation scripts and CI/CD pipelines to modify configuration values dynamically without manual intervention.

---

# Summary of Commands Covered

| Command | Purpose |
|---|---|
| top | Real-time system monitoring |
| ps | Display running processes |
| df | Check disk space |
| du | Check directory size |
| chmod | Change permissions |
| chown | Change ownership |
| tail | View live logs |
| head | View beginning of files |
| awk | Text processing |
| sed | Text replacement/editing |
