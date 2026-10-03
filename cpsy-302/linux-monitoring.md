## Advanced Servers

## Linux Monitoring

---

### Why Linux Monitoring Matters

- **Performance:** Detect high CPU, memory, disk, or network usage before it affects users.
- **Security:** Identify unusual processes, failed logins, or suspicious behavior early.
- **Compliance:** Maintain audit trails and meet regulatory or industry-specific requirements.
- **Availability:** Prevent outages and reduce Mean Time to Recovery (MTTR).
- **Efficiency:** Optimize resources, avoid over-provisioning, and streamline operations.

Source: https://tuxcare.com/blog/linux-monitoring/

---

### System Performance Metrics

- **CPU Usage**: Load percentage, idle time, and context switching.

- **Memory Usage**: RAM consumption, swap utilization, and buffer/cache metrics.

- **Disk I/O**: Read/write speeds, latency, and disk queue length.

---

### Network Metrics

- **Bandwidth Usage**: Incoming and outgoing traffic statistics.

- **Latency & Packet Loss**: Connectivity health and round-trip time.

- **Open Ports & Connections**: Identifying unauthorized or excessive connections.

---

### System Health Metrics

- **Load Average**: A measure of CPU demand over time.

- **Disk Space Usage**: Preventing full partitions that could disrupt services.

- **System Temperature**: Avoiding hardware failures due to overheating.

---

### Security Metrics

- **Failed Login Attempts**: Signs of brute-force attacks.

- **Process Anomalies**: Detecting rogue or compromised processes.

- **Firewall Logs**: Monitoring for unauthorized access attempts.

---

### The Monitoring Mindset

- **Observe the Symptom:** Note the specific behavior, error, or slowdown occurring on the system.
- **Establish a Baseline:** Compare current behavior against normal operational metrics to confirm anomalies.
- **Narrow the Stressed Resource:** Pinpoint the constrained hardware or OS subsystem (CPU, memory, disk I/O, or network).

---

### The Monitoring Mindset

- **Identify the Responsible Process/Service:** Trace the bottleneck to the exact PID, application, or daemon causing the load.
- **Correlate Metrics with Logs:** Cross-reference resource spikes against system, application, and access logs for root-cause context.
- **Change One Thing & Measure:** Apply a single fix or tuning parameter, then re-measure to evaluate the impact.

---

![linux-obs-tools](./linux-monitoring.assets/linux-obs-tools.webp)

Credit: https://www.brendangregg.com/linuxperf.html

---

### `top` Command

- The Linux `top` command is an interactive utility that displays active processes alongside overall CPU, memory, and uptime metrics in real-time:

  - Displays a live list of running processes with resource consumption details

  - Shows overall CPU usage, memory usage, and load averages

  - Updates system statistics continuously without restarting the command

Read: [`top` Command with Examples](https://www.geeksforgeeks.org/linux-unix/top-command-in-linux-with-examples/)

---

### `top` Command

![linux-top-command](./linux-monitoring.assets/linux-top-command.webp)

---

### `htop` - Visual on CPU Metrics

![htop-cmd](./linux-monitoring.assets/htop-cmd.webp)

---

### `btop` - the Lamborghini of `top`s

![btop-cmd](./linux-monitoring.assets/btop-cmd.webp)

---

### `ps` (Process Status) command

- `ps`  in Linux is a built-in utility used to view a **snapshot of currently running processes** on your system.
- Unlike `top` or `htop`, which provide real-time updates, `ps` gives a static picture of the exact moment it is executed.

![ps-cmd](./linux-monitoring.assets/ps-cmd.webp)

Read: [`ps` Command](https://manpages.ubuntu.com/manpages/noble/man1/ps.1.html)

---

### `sysstat` Package - `mpstat`

- `mpstat` reports individual and overall processor (CPU) performance and utilization statistics

![mpstat-cmd](./linux-monitoring.assets/mpstat-cmd.webp)

---

### `sysstat` Package - `pidstat`

- `pidstat` reports detailed resource utilization statistics for individual tasks or processes managed by the kernel

![pidstat-cmd](./linux-monitoring.assets/pidstat-cmd.webp)

---

### `vmstat` - Pressure in One Screen

- `vmstat` reports real-time and average system performance data, including memory, processes, CPU, and disk input/output.

![vmstat-cmd](./linux-monitoring.assets/vmstat-cmd.webp)

Read: [Exploring virtual memory with `vmstat`](https://www.redhat.com/en/blog/linux-commands-vmstat)

---

###  `iotop` - Storage Performance

- `iotop` is a command-line utility in Linux that monitors disk input/output (I/O) usage in real time, similar to how the `top` command monitors CPU and memory.

![iotop-cmd](./linux-monitoring.assets/iotop-cmd.webp)

---

### `df` - Storage Capacity

- **`df` (disk free) command** displays the amount of available and used disk space on your mounted file systems.

![df-cmd](./linux-monitoring.assets/df-cmd.webp)

---

### `du` - Storage Consumption

- **`du` (disk usage) command** in Linux is a standard utility used to estimate and track the space consumed by files and directories. Learn [`du` and the options](https://www.redhat.com/en/blog/du-command-options).

![du-cmd](./linux-monitoring.assets/du-cmd.webp)

---

### `lsblk` - Block Device Information

- The `lsblk` command in Linux lists information about all available or specified block devices like hard drives, solid-state drives, and partitions in a tree-like format.

![lsblk-cmd](./linux-monitoring.assets/lsblk-cmd.webp)

---

### `iostat` - Storage Performance

- `iostat` is a tool used to monitor system input/output (I/O) performance and CPU utilization.

![iostat-cmd](./linux-monitoring.assets/iostat-cmd.webp)

---

### `ip -s link` - Network Monitoring

- **`ip` command** in Linux is a powerful command-line utility used to network configure, manage, and troubleshoot network interfaces, IP addresses, and routing tables.
- The `watch -n 2 'ip -s link'` command monitors network interface statistics (like packets transmitted, received, and errors) in real time.

![watch-ip-link](./linux-monitoring.assets/watch-ip-link.webp)

---

### `ss` - Sockets and Listening Services

- **`ss` command** (Socket Statistics) is a powerful Linux command-line utility used to dump socket statistics and display detailed network connection information. It serves as the modern, much faster replacement for the deprecated `netstat` command.

![ss-tlunp](./linux-monitoring.assets/ss-tlunp.webp)

---

### `iftop` - Who is Using the Network

- **`iftop` command** (Interface TOP) is a real-time network bandwidth monitoring tool for Linux.

![iftop-cmd](./linux-monitoring.assets/iftop-cmd.webp)

---

### `systemctl` for `systemd` Introspection

- `systemctl --failed` lists all systemd units (such as services, sockets, or timers) that have entered a **failed** state, making it quick to spot crashed or misconfigured system components.
- `systemctl show ssh -p ActiveState -p SubState -p MainPID` displays only the active state, sub-state, and main process ID (PID) of the SSH service.

---

### `journalctl` - Query and View logs

- **`journalctl` command** is a powerful Linux utility used to query and view logs generated by the **`systemd-journald`** service.

![journalctl-cmd](./linux-monitoring.assets/journalctl-cmd.webp)

---

### `witr` - Why is this Running

- [`witr`](https://github.com/pranshuparmar/witr) traces any process, port, container, or file back to the exact chain that started it —
  one command, machine-readable JSON, or an interactive TUI.

![witr](./linux-monitoring.assets/witr.webp)

---

### The `/proc` Pseudo-Filesystem

- `/proc` is a virtual filesystem (procfs) generated dynamically in memory by the Linux kernel.
- Reading files here acts as a read-only window directly into active kernel data structures, device configurations, and process memory maps.
- Numbered directories inside `/proc` (e.g., `/proc/1234/`) correspond to running Process IDs (PIDs), exposing that process's open file descriptors, environment variables, and status.
- Named entries at the root level (like `cpuinfo`, `sys/`, and `meminfo`) report global, host-wide system parameters.

---

### `/proc/meminfo`

- This file serves as the kernel's real-time ledger for system-wide memory utilization.
- Tools like `free`, `top`, and `vmstat` read `/proc/meminfo` rather than hardware directly to display memory metrics.

- `MemTotal`: Total usable RAM available to the kernel (physical RAM minus kernel code and reserved firmware space).
- `MemFree`: Memory with literally nothing in it.
- `MemAvailable`: Estimated RAM usable for new workloads without swapping, including reclaimable cache and buffers.

---

### Buffers vs. Cached

- `Buffers`: In-flight raw disk blocks waiting to be written or read (metadata and filesystem overhead).
- `Cached`: The page cache holding files read from disk. The kernel treats this as opportunistically held; if an application requests memory, these pages can be instantly evicted without a disk flush.
- Fields like `SwapTotal` and `SwapFree` track paging space on disk, while `Dirty` shows memory waiting to be synced to disk, giving immediate visibility into pending I/O pressure.

---

### Memory Allocation Strategy

- Both **Linux** and **Windows** use **virtual memory**. A process can reserve more address space than the amount of physical RAM currently available.
- **Windows commit accounting** treats committed private memory as a **promise** that must be backed by RAM or the page file. The system tracks current commit against a commit limit.
- **Linux can overcommit memory**. Depending on `vm.overcommit_memory`, the kernel may approve an allocation before it knows whether enough RAM and swap will be available when every page is actually used.
- The key difference is how strictly and aggressively each OS guarantees memory allocations.

---

### Linux Overcommit

- Applications often reserve more virtual memory than they actually touch.
- Forked processes can initially share pages through copy-on-write instead of immediately duplicating all memory.
- File-backed mappings can be reloaded from disk, so not every mapped page requires swap backing.
- Overcommit improves utilization, but it accepts risk: several processes may later demand their promised pages at the same time.
- Check the policy with:<br>`sysctl vm.overcommit_memory`

---

### Linux Overcommit Modes

- `0`: Heuristic overcommit. The kernel accepts reasonable requests and rejects obvious over-allocation. This is the typical default.
- `1`: Always overcommit. Allocations are accepted with minimal commit checking.
- `2`: Strict accounting. Commit is limited according to swap and the configured RAM ratio or limit.
- View system commitment with:<br>`grep -E 'CommitLimit|Committed_AS' /proc/meminfo`
- `Committed_AS` is promised virtual memory. It is not the same as memory currently resident in RAM.

---

### When Linux Runs Out of Memory

- Linux first tries normal recovery, including reclaiming cache and using swap when available.
- If the kernel still cannot satisfy a required allocation, it enters an **out-of-memory condition**.
- The OOM killer selects a process to terminate so the kernel can reclaim memory and keep the rest of the system operating.
- A killed service is the visible event. The real lesson is the pressure that developed before it happened.
- Useful evidence includes `MemAvailable`, swap use, page activity, per-process growth, and kernel log messages.

---

### Why Trigger OOM in the Lab

- The controlled workload turns memory exhaustion into an observable incident instead of an abstract concept.
- Students can compare **allocated memory**, **resident memory**, **available memory**, **swap**, and **commit accounting** as pressure increases.
- Students can identify the memory-consuming process using `top`, `htop`, `ps`, or `pidstat`.
- Students can correlate metrics with evidence from `journalctl -k`, `dmesg`, and `/proc`.
- The goal is not merely to watch a process die. The goal is to recognize warning signs, prove why it happened, and explain the kernel's recovery action.

---

### Observe Before, During, and After

- **Before:** Record `free -h`, `/proc/meminfo`, swap status, and the largest processes.
- **During:** Watch `MemAvailable`, swap activity, process RSS, and `vmstat` paging columns.
- **After:** Identify the terminated process and confirm the OOM event in the kernel journal.
- Ask: Did the system reclaim cache? Did it use swap? Which process grew? What evidence proves the kernel invoked OOM handling?

---

### Linux Troubleshooting Workflow

![linux-ts-workflow](./linux-monitoring.assets/linux-ts-workflow.webp)

---

### Open-Source Monitoring Solutions

- [**Nagios**](https://www.nagios.org/)

  - One of the most widely used monitoring tools for servers and applications.

  - Provides comprehensive alerting and logging capabilities.

  - Supports plugins to extend functionality.

---

### Open-Source Monitoring Solutions

- [**Zabbix**](https://www.zabbix.com/)

  - Enterprise-grade monitoring tool with automatic detection of network devices.

  - Offers visualization with dashboards and graphs.

  - Supports distributed monitoring for large-scale environments.

---

### Open-Source Monitoring Solutions

- **[Prometheus](https://prometheus.io/) & [Grafana](https://grafana.com/)**
  - **Prometheus**: Time-series database for collecting real-time metrics.
  - **Grafana**: Visualization tool that integrates with Prometheus for creating dashboards.
  - Highly scalable and commonly used for cloud monitoring.

---

### Open-Source Monitoring Solutions

- [**Netdata**](https://www.netdata.cloud/)
  - Lightweight monitoring tool for real-time performance tracking.
  - User-friendly web-based interface with detailed system insights.

---

### Resources

- [2026 Linux Monitoring: 10+ Ways To Monitor, Tools & More for Sysadmins](https://tuxcare.com/blog/linux-monitoring/)
- [Top 10 ways to monitor Linux in the console - Jeff Geerling](https://www.jeffgeerling.com/blog/2025/top-10-ways-monitor-linux-console/)
- [Video: Top 10 ways to monitor Linux in the console - Jeff Geerling](https://www.youtube.com/watch?v=4isEhE2rvmA)
- [Stay Ahead of the Game: Essential Tools and Techniques for Linux Server Monitoring | Linux Journal](https://www.linuxjournal.com/content/stay-ahead-game-essential-tools-and-techniques-linux-server-monitoring)
- [Linux Performance](https://www.brendangregg.com/linuxperf.html)

---

### Resources

- [`top` Command in Linux](https://www.geeksforgeeks.org/linux-unix/top-command-in-linux-with-examples/)
- [`ps` command](https://manpages.ubuntu.com/manpages/noble/man1/ps.1.html)
- [`ip` command](https://man7.org/linux/man-pages/man8/ip.8.html)
- [`systemctl` command](https://man7.org/linux/man-pages/man1/systemctl.1.html)
- [`journalctl` command](https://man7.org/linux/man-pages/man1/journalctl.1.html)
- https://github.com/pranshuparmar/witr
- [Linux kernel overcommit accounting](https://docs.kernel.org/mm/overcommit-accounting.html)
- [Microsoft memory and address-space limits](https://learn.microsoft.com/en-us/windows/win32/memory/memory-limits-for-windows-releases)