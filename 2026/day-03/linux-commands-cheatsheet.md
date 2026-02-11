# Linux Commands Cheat Sheet
Focus: Process Management, File System, Networking  
Use case: Day-to-day production troubleshooting

---

## 🧠 Process Management

`ps aux`  
→ Show all running processes with CPU and memory usage

`ps -ef`  
→ Full process list with parent-child relationships

`top`  
→ Real-time view of system processes and load

`htop`  
→ Interactive process viewer (if installed)

`pidof <process_name>`  
→ Get PID of a running process (e.g., pidof nginx)

`pgrep <name>`  
→ Search PIDs by process name

`kill <PID>`  
→ Gracefully terminate a process (SIGTERM)

`kill -9 <PID>`  
→ Force kill a process (SIGKILL)

`pkill <name>`  
→ Kill process by name

`pstree`  
→ View process hierarchy (parent/child)

`systemctl status <service>`  
→ Check service health (systemd systems)

`systemctl restart <service>`  
→ Restart a service safely

---

## 📁 File System & Logs

`ls -lah`  
→ List files with permissions and sizes

`cd <dir>`  
→ Change directory

`pwd`  
→ Show current directory path

`du -sh <dir>`  
→ Check disk usage of a directory

`df -h`  
→ Check disk space usage

`stat <file>`  
→ Detailed file metadata

`tail -f <file>`  
→ Follow log file in real time

`less <file>`  
→ Read large files safely

`grep "error" <file>`  
→ Search for text in files

`find /path -name "<file>"`  
→ Find files by name

---

## 🌐 Networking & Troubleshooting

`ip addr`  
→ Show network interfaces and IP addresses

`ip route`  
→ Show routing table

`ping <host>`  
→ Check network reachability

`ss -tulnp`  
→ Show listening ports and services

`netstat -tulnp`  
→ Legacy port and connection viewer

`curl <url>`  
→ Test HTTP endpoints

`curl -I <url>`  
→ Fetch HTTP headers only

`dig <domain>`  
→ DNS lookup

`nslookup <domain>`  
→ Simple DNS query

`traceroute <host>`  
→ Trace network path to destination

---

## 🔍 System & Debugging

`uptime`  
→ System running time and load average

`free -h`  
→ Memory usage

`vmstat`  
→ CPU, memory, IO overview

`dmesg | tail`  
→ Kernel messages (recent)

`journalctl -u <service>`  
→ View service logs (systemd)

`journalctl -xe`  
→ View system errors

---

## 🧪 Permissions & Ownership

`chmod 755 <file>`  
→ Change file permissions

`chown user:group <file>`  
→ Change file ownership

`whoami`  
→ Current user

`id`  
→ User and group IDs

---

## ✅ Notes
• Always inspect before killing processes  
• Prefer `kill` before `kill -9`  
• Logs + networking checks solve 80% of outages  

