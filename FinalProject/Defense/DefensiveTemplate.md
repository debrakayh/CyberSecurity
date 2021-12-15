# Blue Team: Summary of Operations

## Table of Contents
- Network Topology
- Description of Targets
- Monitoring the Targets
- Patterns of Traffic & Behavior
- Suggestions for Going Further

### Network Topology

![Topology](images\Topology.png)
The following machines were identified on the network:
- **Name of VM 1**: Capstone
  - **Operating System**: Linux
  - **Purpose**: will collect and forward filebeat and metricbeat logs to ELK
  - **IP Address**: 192.168.1.105
- **Name of VM 2**: ELK
  - **Operating System**: Linux
  - **Purpose**: Holds Kabana dashboards for analyzing filebeat and metricbeat data
  - **IP Address**: 192.168.1.100
- **Name of VM 3**: Kali
  - **Operating System**: Linux
  - **Purpose**: Attacking machine.  Will be used for Penetration testing
  - **IP Address**: 192.168.1.90
- **Name of VM 4**: Target 1
  - **Operating System**: Linux
  - **Purpose**: target machine will be the victim of the penetration attack
  - **IP Address**: 192.168.1.110

### Description of Targets

The target of this attack was: `Target 1` (192.168.1.110).

Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

#### Name of Alert 1
`Excessive HTTP Errors` 

Alert 1 is implemented as follows:
  - **Metric**: packetbeat
  - **Threshold**: 400 in 5 minutes
  - **Vulnerability Mitigated**: Brute force attack
  - **Reliability**: Does this alert generate lots of false positives/false negatives? *No* 
    - Rate as low, medium, or high reliability. *High*

#### Name of Alert 2
`HTTP Request Size Monitor`

Alert 2 is implemented as follows:
  - **Metric**: packetbeat
  - **Threshold**: 3500 in last 1 minute
  - **Vulnerability Mitigated**: Port scanning
  - **Reliability**: Does this alert generate lots of false positives/false negatives? Rate as low, medium, or high reliability.
    - second

#### Name of Alert 3
`CPU Usage Monitor`

Alert 3 is implemented as follows:
  - **Metric**: metricbeat
  - **Threshold**: 0.5 for last 5 minutes
  - **Vulnerability Mitigated**: Brute Force
  - **Reliability**: Does this alert generate lots of false positives/false negatives? *Yes*
    - Rate as low, medium, or high reliability. *Low*


### Suggestions for Going Further (Optional)
_TODO_: 
- Each alert above pertains to a specific vulnerability/exploit. Recall that alerts only detect malicious behavior, but do not stop it. For each vulnerability/exploit identified by the alerts above, suggest a patch. E.g., implementing a blocklist is an effective tactic against brute-force attacks. It is not necessary to explain _how_ to implement each patch.
  
The logs and alerts generated during the assessment suggest that this network is susceptible to several active threats, identified by the alerts above. In addition to watching for occurrences of such threats, the network should be hardened against them. The Blue Team suggests that IT implement the fixes below to protect the network:
- Vulnerability 1: Weak Passwords
  - **Patch**: Implement a strong password policy with a forced expiration date,
- Vulnerability 2: 
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
- Vulnerability 3
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
