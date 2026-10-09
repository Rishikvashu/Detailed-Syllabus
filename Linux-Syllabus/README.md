# 🐧 Linux for DevOps: Complete Syllabus

A module-by-module Linux roadmap for DevOps, from fundamentals to production troubleshooting. Tick the boxes as you go (`- [ ]` → `- [x]`).

> **Rule:** run every command yourself. Break things on purpose, then fix them.

## 📌 How to Use This Roadmap

| Priority | Modules | Why |
|---|---|---|
| 🟢 **Core (start here)** | 01–09, 12, 14 | Most DevOps interview questions come from these |
| 🟡 **Next** | 10, 11, 13, 15, 16 | Real-world sysadmin skills |
| 🔴 **Advanced** | 17, 18, 20 | Differentiates you from other candidates |
| 🏁 **Finish with** | 21 | Labs and interview prep |

## 📑 Table of Contents

1. [Linux Foundations](#01-linux-foundations)
2. [Shell & Command Line](#02-shell--command-line)
3. [Filesystem & File Management](#03-filesystem--file-management)
4. [Permissions & Access Control](#04-permissions--access-control)
5. [Users & Groups](#05-users--groups)
6. [Text Processing & Editors](#06-text-processing--editors)
7. [Package Management & Software](#07-package-management--software)
8. [Process Management](#08-process-management)
9. [systemd & Services](#09-systemd--services)
10. [Boot Process & Kernel](#10-boot-process--kernel)
11. [Storage Management](#11-storage-management)
12. [Networking](#12-networking)
13. [Logging & Monitoring](#13-logging--monitoring)
14. [Bash Scripting](#14-bash-scripting)
15. [Scheduling & Automation](#15-scheduling--automation)
16. [Archiving, Compression & Backup](#16-archiving-compression--backup)
17. [Linux Security & Hardening](#17-linux-security--hardening)
18. [Performance Tuning & Troubleshooting](#18-performance-tuning--troubleshooting)
19. [Time, Locale & Misc Sysadmin](#19-time-locale--misc-sysadmin)
20. [Linux Under Containers & Cloud](#20-linux-under-containers--cloud)
21. [Capstones & Interview Prep](#21-capstones--interview-prep)

---

## 01. Linux Foundations

### 1.1 What is Linux
- [ ] Kernel vs OS vs Distribution
- [ ] Unix history, GNU, Linus Torvalds, open source & GPL
- [ ] Monolithic kernel vs microkernel
- [ ] Kernel space vs user space, system calls

### 1.2 Distributions
- [ ] Debian family: Debian, Ubuntu, Mint
- [ ] RHEL family: RHEL, CentOS Stream, Rocky, AlmaLinux, Fedora
- [ ] Amazon Linux 2 / 2023
- [ ] SUSE, Arch, Alpine (musl libc, BusyBox)
- [ ] LTS vs rolling vs release cycles, EOL

### 1.3 Environment Setup
- [ ] WSL2 (install, distros, `wsl.conf`, resource limits)
- [ ] VirtualBox / VMware / Multipass
- [ ] Cloud VM (EC2), SSH key pairs
- [ ] Dual boot (concept)

### 1.4 Linux Architecture
- [ ] Hardware → Kernel → Shell → Applications
- [ ] Everything is a file (philosophy)
- [ ] Init system, daemons, libraries (shared vs static)

---

## 02. Shell & Command Line

### 2.1 Shell Basics
- [ ] Terminal vs shell vs console vs TTY/PTY
- [ ] Shells: bash, zsh, sh, dash, fish
- [ ] Prompt (`PS1`), command structure (command, options, arguments)
- [ ] Help tools: `man`, `info`, `--help`, `tldr`, `whatis`, `apropos`, `type`, `which`, `whereis`

### 2.2 Navigation
- [ ] `pwd`, `cd` (`-`, `~`, `..`), `ls` (`-l -a -h -R -t -S -i`)
- [ ] Absolute vs relative paths
- [ ] `tree`, `pushd`, `popd`, `dirs`

### 2.3 Shell Features
- [ ] Tab completion, history (`!!`, `!n`, `Ctrl+R`, `HISTSIZE`, `HISTCONTROL`)
- [ ] Globbing / wildcards (`*`, `?`, `[]`, `{}`)
- [ ] Brace expansion, command substitution `$( )`, arithmetic `$(( ))`
- [ ] Quoting (single, double, backslash)
- [ ] Aliases, functions
- [ ] Keyboard shortcuts (`Ctrl+C`, `Z`, `D`, `L`, `A`, `E`, `W`, `U`)

### 2.4 Environment
- [ ] Environment variables vs shell variables
- [ ] `export`, `env`, `printenv`, `set`, `unset`
- [ ] `PATH`, `HOME`, `USER`, `SHELL`, `PWD`, `LANG`
- [ ] Startup files: `/etc/profile`, `~/.bash_profile`, `~/.bashrc`, `~/.profile`
- [ ] Login vs non-login, interactive vs non-interactive shells
- [ ] `/etc/environment`

### 2.5 Redirection & Pipes
- [ ] stdin (0), stdout (1), stderr (2)
- [ ] `>`, `>>`, `<`, `<<`, `<<<`, `2>`, `2>&1`, `&>`, `/dev/null`
- [ ] Pipes `|`, `tee`, `xargs`, process substitution `<( )`
- [ ] Here-documents

### 2.6 Command Chaining
- [ ] `;` `&&` `||` `&` `( )` `{ }`
- [ ] Exit codes (`$?`), `true` / `false`
- [ ] Subshells vs current shell

### 2.7 Job Control
- [ ] Foreground / background (`&`, `fg`, `bg`, `jobs`)
- [ ] `Ctrl+Z`, `disown`, `nohup`
- [ ] `screen`, `tmux` (sessions, panes, detach/attach)

---

## 03. Filesystem & File Management

### 3.1 Filesystem Hierarchy Standard (FHS)
- [ ] `/` `/bin` `/sbin` `/usr` `/usr/local` `/etc` `/var` `/tmp` `/home` `/root`
- [ ] `/opt` `/srv` `/mnt` `/media` `/dev` `/proc` `/sys` `/boot` `/lib` `/run`
- [ ] `/var/log`, `/var/lib`, `/var/cache`, `/var/spool`
- [ ] `/usr` merge (`/bin` → `/usr/bin`)

### 3.2 File Operations
- [ ] `touch`, `cp` (`-r -a -p`), `mv`, `rm` (`-rf`), `mkdir -p`, `rmdir`
- [ ] `cat`, `tac`, `less`, `more`, `head`, `tail` (`-f`, `-F`)
- [ ] `file`, `stat`, `wc`, `du`, `df`, `ncdu`
- [ ] `rename`, `basename`, `dirname`, `realpath`, `readlink`

### 3.3 Finding Files
- [ ] `find` (`-name -type -size -mtime -perm -user -exec -delete -maxdepth`)
- [ ] `locate` / `updatedb`, `which`, `whereis`
- [ ] `find` + `xargs` patterns

### 3.4 Links
- [ ] Inodes, directory entries
- [ ] Hard links vs soft (symbolic) links
- [ ] `ln`, `ln -s`, dangling links

### 3.5 File Types
- [ ] Regular, directory, symlink, block, char, socket, pipe (FIFO)
- [ ] Special files: `/dev/null`, `/dev/zero`, `/dev/random`, `/dev/urandom`

### 3.6 Filesystems
- [ ] ext4, xfs, btrfs, zfs (overview), tmpfs, overlayfs, NFS, FAT/NTFS
- [ ] Journaling, superblock, inode table, blocks
- [ ] `mkfs`, `fsck`, `tune2fs`, `xfs_repair`, `resize2fs`, `xfs_growfs`

### 3.7 Mounting
- [ ] `mount`, `umount`, `findmnt`, `lsblk`, `blkid`
- [ ] `/etc/fstab` (fields, UUID, options: `noatime`, `defaults`, `nofail`)
- [ ] Bind mounts, loop devices
- [ ] Mount options & systemd mount units

### 3.8 Special Filesystems
- [ ] `/proc` (cpuinfo, meminfo, PID dirs, `sys/` tuning)
- [ ] `/sys` (devices, kernel parameters)
- [ ] `/dev`, udev basics

---

## 04. Permissions & Access Control

### 4.1 Basic Permissions
- [ ] `rwx` for user / group / others
- [ ] Numeric (octal) vs symbolic mode
- [ ] `chmod`, `chown`, `chgrp`
- [ ] Permissions on files vs directories

### 4.2 Default Permissions
- [ ] `umask` (calculation, persistent setting)

### 4.3 Special Permissions
- [ ] SUID, SGID, Sticky bit
- [ ] Security implications, finding SUID files

### 4.4 Extended Attributes & ACLs
- [ ] `getfacl`, `setfacl`, default ACLs
- [ ] `chattr` / `lsattr` (immutable, append-only)

### 4.5 sudo
- [ ] `/etc/sudoers`, `visudo`, `/etc/sudoers.d/`
- [ ] `NOPASSWD`, command aliases, user/group specs
- [ ] `sudo` vs `su` vs `su -`, `sudo -i`

### 4.6 Mandatory Access Control
- [ ] SELinux (modes, contexts, booleans, `restorecon`, `audit2allow`)
- [ ] AppArmor (profiles, `aa-status`)

---

## 05. Users & Groups

### 5.1 Account Files
- [ ] `/etc/passwd`, `/etc/shadow`, `/etc/group`, `/etc/gshadow`
- [ ] Fields, UID/GID ranges, system vs normal users

### 5.2 User Management
- [ ] `useradd`, `usermod`, `userdel`, `adduser`, `passwd`, `chage`
- [ ] `/etc/skel`, `/etc/login.defs`, `/etc/default/useradd`
- [ ] Locking/unlocking, `nologin` shell, password aging

### 5.3 Group Management
- [ ] `groupadd`, `groupmod`, `groupdel`, `gpasswd`
- [ ] Primary vs secondary groups
- [ ] `id`, `groups`, `who`, `w`, `last`, `lastlog`, `whoami`

### 5.4 Authentication
- [ ] PAM (modules, `/etc/pam.d/`)
- [ ] Password policies (`pwquality`, `faillock`)
- [ ] LDAP / SSSD / Active Directory (overview)

---

## 06. Text Processing & Editors

### 6.1 Viewing & Filtering
- [ ] `cut`, `sort` (`-n -r -u -k`), `uniq` (`-c`), `tr`, `paste`, `join`, `column`
- [ ] `nl`, `fold`, `fmt`, `expand`, `rev`, `diff`, `cmp`, `comm`
- [ ] `tee`, `split`, `csplit`

### 6.2 grep Family
- [ ] `grep` (`-i -v -r -n -c -l -w -A -B -C -o -E -P`)
- [ ] Basic vs extended vs Perl regex
- [ ] `egrep`, `fgrep`, `ripgrep (rg)`, `zgrep`

### 6.3 Regular Expressions
- [ ] Anchors, character classes, quantifiers, groups, alternation
- [ ] Backreferences, lookahead (PCRE)
- [ ] Greedy vs non-greedy

### 6.4 sed
- [ ] Substitute `s///`, flags (`g`, `i`, `p`)
- [ ] Addressing (line numbers, ranges, regex)
- [ ] `d`, `p`, `i`, `a`, `c`, `y`, in-place `-i`
- [ ] Multi-command scripts

### 6.5 awk
- [ ] Fields (`$1`, `$NF`), `NR`, `NF`, `FS`, `OFS`, `RS`
- [ ] `BEGIN` / `END` blocks, patterns, conditions
- [ ] Variables, arrays, functions, `printf`
- [ ] Real log-parsing one-liners

### 6.6 Structured Data Tools
- [ ] `jq` (JSON), `yq` (YAML), `xmllint`
- [ ] `csvkit` (overview)

### 6.7 Editors
- [ ] vim / vi (modes, motions, operators, visual, search/replace, registers, macros, `.vimrc`)
- [ ] nano (basics)
- [ ] `sed` / `ed` for non-interactive editing

---

## 07. Package Management & Software

### 7.1 Concepts
- [ ] Packages, repositories, dependencies, GPG signing
- [ ] Binary vs source packages

### 7.2 Debian Family
- [ ] `dpkg` (`-i -l -L -S -r -P`)
- [ ] `apt` / `apt-get` / `apt-cache` (update, upgrade, full-upgrade, install, remove, purge, autoremove, search, show, policy)
- [ ] `/etc/apt/sources.list(.d)`, PPAs, keyrings
- [ ] Pinning, holding packages (`apt-mark`)
- [ ] `unattended-upgrades`

### 7.3 RHEL Family
- [ ] `rpm` (`-ivh -qa -ql -qf -e`)
- [ ] `yum` / `dnf` (install, update, remove, history, module, provides, repolist)
- [ ] `/etc/yum.repos.d/`, EPEL
- [ ] `versionlock`

### 7.4 Other Package Systems
- [ ] `apk` (Alpine)
- [ ] `snap`, `flatpak`
- [ ] `pip`, `npm`, `gem` (language package managers, venv concept)

### 7.5 Building from Source
- [ ] Toolchain: `gcc`, `make`, `build-essential`
- [ ] `./configure` → `make` → `make install` (`altinstall`)
- [ ] `--prefix`, build dependencies, `ldconfig`
- [ ] `checkinstall`, `update-alternatives`

### 7.6 Shared Libraries
- [ ] `ldd`, `ldconfig`, `LD_LIBRARY_PATH`, `rpath`
- [ ] Fixing "library not found" errors

---

## 08. Process Management

### 8.1 Process Concepts
- [ ] Program vs process vs thread
- [ ] PID, PPID, UID, states (R, S, D, T, Z)
- [ ] `fork`, `exec`, `clone`, `wait`, init / PID 1
- [ ] Zombie and orphan processes
- [ ] Process tree

### 8.2 Inspecting
- [ ] `ps` (`aux`, `-ef`, `-eo`), `pstree`, `top`, `htop`, `atop`, `pgrep`
- [ ] `lsof`, `fuser`, `/proc/<pid>/` (cmdline, status, fd, maps, environ)
- [ ] `strace`, `ltrace`, `pidstat`

### 8.3 Signals
- [ ] SIGHUP, SIGINT, SIGTERM, SIGKILL, SIGSTOP, SIGCONT, SIGUSR1/2, SIGCHLD
- [ ] `kill`, `killall`, `pkill`
- [ ] `trap` in scripts, graceful shutdown

### 8.4 Priority & Limits
- [ ] `nice`, `renice`, `ionice`, `chrt`
- [ ] `ulimit`, `/etc/security/limits.conf`
- [ ] cgroups basics

### 8.5 Daemons
- [ ] Foreground vs background services
- [ ] Double-fork, `nohup`, `disown`, `setsid`

---

## 09. systemd & Services

### 9.1 systemd Fundamentals
- [ ] Units: service, socket, timer, target, mount, path, slice
- [ ] Unit file locations (`/etc/systemd/system`, `/usr/lib/systemd/system`)
- [ ] SysV init & Upstart (legacy)

### 9.2 systemctl
- [ ] `start`, `stop`, `restart`, `reload`, `enable`, `disable`, `mask`, `status`
- [ ] `is-active`, `is-enabled`, `list-units`, `list-unit-files`
- [ ] `daemon-reload`, `edit`, `cat`, `show`
- [ ] Overrides / drop-ins

### 9.3 Writing a Service Unit
- [ ] `[Unit]`: Description, After, Requires, Wants
- [ ] `[Service]`: Type, ExecStart, ExecStop, Restart, RestartSec, User, Environment, WorkingDirectory
- [ ] `[Install]`: WantedBy
- [ ] Hardening options (`ProtectSystem`, `NoNewPrivileges`, `PrivateTmp`)

### 9.4 Targets & Boot
- [ ] `multi-user.target`, `graphical.target`, rescue, emergency
- [ ] `systemctl isolate` / `set-default`
- [ ] `systemd-analyze` (`blame`, `critical-chain`)

### 9.5 Timers
- [ ] `OnCalendar`, `OnBootSec`, `Persistent`
- [ ] Timer vs cron

### 9.6 Other systemd Tools
- [ ] `journalctl`, `hostnamectl`, `timedatectl`, `localectl`, `loginctl`
- [ ] `systemd-resolved`, `systemd-networkd`

---

## 10. Boot Process & Kernel

### 10.1 Boot Sequence
- [ ] BIOS vs UEFI → bootloader → kernel → initramfs → systemd
- [ ] MBR vs GPT, ESP partition

### 10.2 GRUB
- [ ] `/etc/default/grub`, `grub2-mkconfig` / `update-grub`
- [ ] Kernel parameters, single-user mode
- [ ] Reset root password, recovery

### 10.3 Kernel
- [ ] `uname`, kernel versions, `/boot`
- [ ] Modules: `lsmod`, `modprobe`, `insmod`, `rmmod`, `modinfo`, `/etc/modprobe.d/`
- [ ] `sysctl`, `/etc/sysctl.conf`, `/proc/sys`
- [ ] `dmesg`, kernel ring buffer
- [ ] Kernel upgrade, DKMS, livepatch (overview)

### 10.4 Hardware Info
- [ ] `lscpu`, `lsmem`, `lspci`, `lsusb`, `lshw`, `dmidecode`, `lsblk`

---

## 11. Storage Management

### 11.1 Disk Basics
- [ ] Block devices, sectors, partitions
- [ ] `fdisk`, `gdisk`, `parted`, `lsblk`, `blkid`
- [ ] EBS volumes on AWS (attach, format, mount, resize)

### 11.2 LVM
- [ ] PV, VG, LV concepts
- [ ] `pvcreate` / `vgcreate` / `lvcreate`, `lvextend`, `lvreduce`, `vgextend`
- [ ] Resizing filesystems online
- [ ] Snapshots

### 11.3 RAID
- [ ] RAID 0, 1, 5, 6, 10
- [ ] `mdadm` (create, monitor, replace failed disk)

### 11.4 Swap
- [ ] Swap partition vs swap file
- [ ] `mkswap`, `swapon`, `swapoff`, `swappiness`
- [ ] zram (overview)

### 11.5 Quotas & Monitoring
- [ ] User/group quotas
- [ ] `df`, `du`, `iostat`, `iotop`, inode exhaustion

### 11.6 Network Storage
- [ ] NFS (server/client, exports)
- [ ] Samba (overview)
- [ ] iSCSI, EFS (overview)

---

## 12. Networking

### 12.1 Fundamentals
- [ ] OSI & TCP/IP models
- [ ] IPv4 (classes, CIDR, subnetting, private ranges), IPv6 basics
- [ ] MAC, ARP, ICMP, TCP vs UDP, ports, sockets
- [ ] TCP handshake, states (`ESTABLISHED`, `TIME_WAIT`, `CLOSE_WAIT`)

### 12.2 Interface Configuration
- [ ] `ip` (addr, link, route, neigh), `ifconfig` (legacy)
- [ ] Netplan (Ubuntu), NetworkManager (`nmcli`, `nmtui`), systemd-networkd
- [ ] `/etc/network/interfaces`, ifcfg files
- [ ] Static vs DHCP
- [ ] Bonding, VLANs, bridges (overview)

### 12.3 Name Resolution
- [ ] `/etc/hosts`, `/etc/resolv.conf`, `/etc/nsswitch.conf`
- [ ] DNS record types (A, AAAA, CNAME, MX, TXT, NS, SOA, PTR)
- [ ] `dig`, `nslookup`, `host`, `resolvectl`
- [ ] Recursive vs authoritative, caching, TTL

### 12.4 Diagnostics
- [ ] `ping`, `traceroute`, `tracepath`, `mtr`
- [ ] `ss`, `netstat`, `lsof -i`
- [ ] `curl` (`-v -I -X -H -d -k -L --resolve`), `wget`
- [ ] `nc` (netcat), `telnet`, `nmap`
- [ ] `tcpdump`, Wireshark / `tshark`

### 12.5 Firewalls
- [ ] `iptables` (tables, chains, rules, NAT)
- [ ] `nftables` (overview)
- [ ] `ufw` (Ubuntu), `firewalld` (RHEL)
- [ ] Cloud security groups vs host firewall

### 12.6 Routing & NAT
- [ ] Routing table, default gateway, static routes
- [ ] IP forwarding, masquerading, port forwarding
- [ ] Network namespaces

### 12.7 SSH & Remote Access
- [ ] `ssh`, key-based auth (`ssh-keygen`, `ssh-copy-id`, `authorized_keys`)
- [ ] `sshd_config` hardening (`PermitRootLogin`, `PasswordAuthentication`, `AllowUsers`, `Port`)
- [ ] `~/.ssh/config`, `ssh-agent`, agent forwarding
- [ ] Tunneling (local `-L`, remote `-R`, dynamic `-D`), ProxyJump / bastion
- [ ] `scp`, `sftp`, `rsync` over ssh
- [ ] `fail2ban`

### 12.8 File Transfer & Sync
- [ ] `rsync` (`-avz`, `--delete`, `--exclude`, dry-run), `scp`, `curl`, `wget`

### 12.9 Common Network Services
- [ ] DHCP, DNS (bind / dnsmasq), NTP, SMTP (overview)
- [ ] Web servers: Nginx, Apache (install, config, vhosts, reverse proxy)
- [ ] Load balancing basics (HAProxy / Nginx upstream)

---

## 13. Logging & Monitoring

### 13.1 Logs
- [ ] `/var/log` (`syslog`, `messages`, `auth.log`, `secure`, `kern.log`, `dmesg`)
- [ ] `syslog` / `rsyslog` (facilities, severities, rules)
- [ ] `journald`, `journalctl` (`-u -f -b -p --since --until -o json`)
- [ ] Persistent journal config
- [ ] `logrotate` (config, rotation, compression, postrotate)

### 13.2 Audit
- [ ] `auditd`, `ausearch`, `aureport`, audit rules
- [ ] `last`, `lastb`, `who`

### 13.3 Resource Monitoring
- [ ] CPU: `top`, `htop`, `mpstat`, `uptime`, load average
- [ ] Memory: `free`, `vmstat`, `/proc/meminfo`, cache vs buffers, OOM killer
- [ ] Disk: `iostat`, `iotop`, `df`, `du`
- [ ] Network: `iftop`, `nload`, `sar`, `nethogs`
- [ ] `sar` / `sysstat`, `dstat`, `glances`

### 13.4 Monitoring Tools (Intro)
- [ ] `node_exporter`, Prometheus, Grafana
- [ ] Nagios / Zabbix (overview)

---

## 14. Bash Scripting

### 14.1 Basics
- [ ] Shebang, execute permission, running scripts
- [ ] Variables, constants, `readonly`, positional params (`$0 $1 $@ $* $# $$ $?`)
- [ ] Input: `read` (`-p -s -t`), arguments, `getopts`
- [ ] Comments, exit codes, `echo` vs `printf`

### 14.2 Operators & Tests
- [ ] `[ ]` vs `[[ ]]` vs `test`
- [ ] File tests (`-f -d -e -r -w -x -s -L`)
- [ ] String tests (`-z -n`, `=`, `!=`, regex `=~`)
- [ ] Numeric tests (`-eq -ne -lt -gt -le -ge`), `(( ))`
- [ ] Logical `&&`, `||`, `!`

### 14.3 Control Flow
- [ ] `if` / `elif` / `else`
- [ ] `case`
- [ ] `for` (list, C-style), `while`, `until`
- [ ] `break`, `continue`, `select`

### 14.4 Data Structures
- [ ] Indexed arrays, associative arrays
- [ ] String manipulation (length, substring, replace, trim, case)

### 14.5 Parameter Expansion
- [ ] `${var:-def}`, `${var:=def}`, `${var:?err}`, `${var%pat}`, `${var#pat}`, `${var//a/b}`

### 14.6 Functions
- [ ] Definition, arguments, `return` vs `echo`, `local` variables
- [ ] Sourcing libraries (`source` / `.`)

### 14.7 Robust Scripting
- [ ] `set -euo pipefail`, `IFS`, `set -x`
- [ ] `trap` (`EXIT`, `ERR`, `SIGINT`), cleanup, `mktemp`
- [ ] Quoting rules, avoiding word-splitting
- [ ] Lock files, idempotency, logging functions
- [ ] Input validation, error handling, usage/help
- [ ] `shellcheck`, `shfmt`, `bats` (testing)

### 14.8 Practical Scripts
- [ ] Backup, log rotation/cleanup, disk-usage alert
- [ ] User provisioning, health check, service watchdog
- [ ] Bulk server operations over ssh
- [ ] Software installer/manager (e.g. `python_manager.sh`)

### 14.9 Beyond Bash
- [ ] Python for sysadmin tasks (`subprocess`, `os`, `argparse`, `boto3`)

---

## 15. Scheduling & Automation

### 15.1 cron
- [ ] crontab syntax (`min hour dom mon dow`), special strings (`@reboot`, `@daily`)
- [ ] User crontab vs `/etc/crontab` vs `/etc/cron.d`, `cron.daily` / `hourly`
- [ ] Environment pitfalls, logging, `MAILTO`
- [ ] `flock` to prevent overlap

### 15.2 at / batch
- [ ] One-time job scheduling

### 15.3 systemd Timers
- [ ] Timer units as a cron alternative

---

## 16. Archiving, Compression & Backup

### 16.1 Archiving
- [ ] `tar` (`-c -x -t -v -f -z -j -J --exclude -C`)

### 16.2 Compression
- [ ] `gzip`, `bzip2`, `xz`, `zstd`, `zip` / `unzip`

### 16.3 Disk Imaging
- [ ] `dd`, `ddrescue`, `partclone`

### 16.4 Backup Strategies
- [ ] Full, incremental, differential, 3-2-1 rule
- [ ] `rsync` snapshots, `restic`, `borg`
- [ ] Cloud backups (S3 sync), EBS snapshots

### 16.5 Restore & DR Testing
- [ ] Restore drills and disaster recovery testing

---

## 17. Linux Security & Hardening

### 17.1 Principles
- [ ] Least privilege, defense in depth, attack surface

### 17.2 System Hardening
- [ ] Disable root SSH login, unused services/ports
- [ ] Automatic security updates, patch management
- [ ] Kernel hardening via `sysctl`
- [ ] File integrity: AIDE, Tripwire
- [ ] CIS benchmarks, Lynis
- [ ] Secure mount options (`noexec`, `nosuid`, `nodev`)

### 17.3 Network Security
- [ ] Firewall rules, `fail2ban`, port scanning, TLS/SSL
- [ ] `openssl` (certs, CSR, `s_client`), Let's Encrypt / `certbot`

### 17.4 Cryptography Basics
- [ ] Symmetric vs asymmetric, hashing, signatures
- [ ] GPG, `sha256sum`, `md5sum`
- [ ] LUKS disk encryption

### 17.5 Secrets Handling
- [ ] Avoiding secrets in history/env/scripts, vault concepts

### 17.6 Threats & Detection
- [ ] Rootkits (`rkhunter`, `chkrootkit`), brute force, privilege escalation
- [ ] Auditing logins, suspicious processes/connections

### 17.7 Compliance & MAC
- [ ] SELinux / AppArmor in practice

---

## 18. Performance Tuning & Troubleshooting

### 18.1 Methodology
- [ ] USE method (Utilization, Saturation, Errors)
- [ ] Top-down troubleshooting flow

### 18.2 CPU
- [ ] Load average, run queue, context switches, steal time

### 18.3 Memory
- [ ] Swap thrashing, page cache, OOM killer, memory leaks, slab

### 18.4 Disk I/O
- [ ] Latency, IOPS, throughput, iowait, scheduler

### 18.5 Network
- [ ] Bandwidth, packet loss, retransmits, conntrack, port exhaustion

### 18.6 Tracing & Profiling
- [ ] `strace`, `perf`, `ltrace`, `lsof`, eBPF / `bpftrace` (intro), flame graphs

### 18.7 Common Failure Scenarios
- [ ] Disk full (space vs inodes), deleted file still held by a process
- [ ] High load / CPU 100%, memory exhaustion, OOM kills
- [ ] Service won't start (`systemctl status`, `journalctl`, config test)
- [ ] Port already in use, "Permission denied", "Too many open files"
- [ ] SSH lockout, wrong `fstab` (won't boot), broken package / dpkg lock
- [ ] DNS failures, time drift, zombie accumulation
- [ ] Recovering via rescue mode / EC2 volume attach

### 18.8 Tuning
- [ ] `sysctl` (`net.*`, `vm.*`, `fs.file-max`), limits, `tuned` profiles

---

## 19. Time, Locale & Misc Sysadmin

- [ ] **19.1 Time:** `timedatectl`, NTP, `chrony`, timezones, `hwclock`
- [ ] **19.2 Locale & encoding:** `locale`, UTF-8, `LANG` / `LC_*`
- [ ] **19.3 Hostname & identity:** `hostnamectl`, `/etc/hostname`, `machine-id`
- [ ] **19.4 Email & notifications:** `mailx`, `msmtp` (basic alerts)
- [ ] **19.5 Documentation & conventions:** man sections, changelogs, runbooks

---

## 20. Linux Under Containers & Cloud

### 20.1 Container Primitives
- [ ] Namespaces (pid, net, mnt, uts, ipc, user)
- [ ] cgroups v1 vs v2, resource limits
- [ ] `chroot`, `pivot_root`, overlayfs, capabilities, seccomp
- [ ] Build a "container" manually with `unshare` + `chroot`

### 20.2 Virtualization
- [ ] Hypervisors (Type 1/2), KVM/QEMU, libvirt
- [ ] VM vs container differences

### 20.3 Cloud-Specific Linux
- [ ] cloud-init (user-data, metadata service `169.254.169.254`)
- [ ] EC2: key pairs, EBS, instance store, ENA, AMIs
- [ ] AWS SSM Session Manager, SSM agent
- [ ] User-data scripts, bootstrapping, golden images

### 20.4 Config Management Bridge
- [ ] Idempotency, Ansible basics on Linux hosts

---

## 21. Capstones & Interview Prep

### 21.1 Hands-on Labs
- [ ] Build a hardened web server (Nginx + TLS + firewall + fail2ban)
- [ ] LVM + RAID + fstab + quota lab
- [ ] Break-and-fix: 10 deliberate failures, diagnose each
- [ ] Write a monitoring + alert script with cron / systemd timer
- [ ] Automated backup with rotation to S3

### 21.2 Interview Topics
- [ ] "What happens when you type a command / `curl` a URL?"
- [ ] Boot process, process states, zombie vs orphan
- [ ] Hard vs soft link, inode, permissions scenarios
- [ ] Troubleshooting: "server is slow", "disk is full", "can't SSH"
- [ ] Top 100 commands & one-liners (`awk` / `sed` / `find` / `grep`)

### 21.3 Certifications (Optional)
- [ ] RHCSA, LFCS, Linux+

---

## 🚀 What's Next

After Linux, continue in this order: **Networking → Git & CI/CD → AWS → Docker → Terraform & Ansible → Kubernetes → Monitoring & Security**.
