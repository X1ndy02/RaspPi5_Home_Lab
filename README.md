# RaspPi5_Home_Lab
Self-hosted Raspberry Pi 5 homelab

##Overview

This is just simple backtracking on what I have build and done with my Pi5

## Purpose
To learn and experiment in enviroment that has been designed and build from scratech by me 

======================================================================================
======================================================================================

As of 27/02/26

## Hardware

## Core System
- Raspberry Pi 5 Model B (16GB RAM)
- 52Pi Ultra Thin ICE Tower Cooler

## Primary Storage (Boot Drive)
- Kingston 500GB NVMe SSD  
  - Connected via Geekworm X1001 PCIe to M.2 adapter  
  - Linked using Geekworm Raspberry Pi 5 PCIe FFC Cable (50mm)  
  - Mounted in an elevated position using M2.5 hex brass spacers (standoffs) to improve airflow and clearance
    
## Power Backup
- Geekworm X1201 2-Cell 18650 5.1V 5A UPS Shield  
  - 2 × Molicel M35A 18650 (3500mAh, 10A) batteries
## Secondary Storage
- Geekworm X1100 2.5" SATA HDD/SSD Shield  
- Kingston 240GB SATA SSD

## System Monitoring Display
- RP2350 1.47" Display Development Board (172×320, 262K color)
  - Based on RP2350 dual-core, dual-architecture microcontroller
  - Connected via USB
  - Displays real-time system statistics and `top` output
  - Visual status information including:
    - Current IP addresses
    - Running processes
    - CPU usage
    - RAM usage
    - Temperature
    - UPS battery status
    - Ping
    - Throttling state
      
======================================================================================
======================================================================================
# Sofwtare and Services Running

## Containerized Services (Docker)
## Nextcloud Stack
- Nextcloud (which is using  MariaDB, Redis Cache, Nginx Reverse Proxy)
- ClamAV Scanner 
## Monitoring Stack
- Prometheus (that Collects and stores system metircs)
- Node Exporter (Exposes system metrics from the host in readable format)
- Grafana (Dashboard UI to visualize metrics. It queries Prometheus and turns data into
    charts, alerts, and dashboards)
- Grafana Image Renderer (Renders Grafana panels/dashboards to images (for reports, alerts, sharing)

## Host-Level Services
## Container Runtime
- Docker Engine, Docker Compose
## Remote Access & Network
- ZeroTier VPN (Private virtual network so I can ssh in from any of my devices)
## Security & Protection
- Fail2Ban (Blocks IPs that repeatedly fail logins ( to prevent SSH brute force)
## Backup & Recovery
- Restic (Automated Daily backups (snapshots) that goes to local storage (240gb Kingston Sata ssd))
## Monitoring & Health
- SMART disk monitoring (Tracks disk health and alerts on
    issues)
- pi-monitor.service (Custom checks for Pi health/status)
- rp2350-stats.service (Sends system stats to your RP2350 LCD dashboard)
## Power Management
- x120x-ups-notify.service (Emails alerts when UPS switches to battery)
- x120x-ups-shutdown.service (Safely shuts down when UPS battery is low)

## Alerting
- msmtp / msmtp-mta (Lightweight mail sender used by alert scripts)

======================================================================================
======================================================================================

# Reporting & Monitoring via smtp 

Alerts are triggered on state changes and include:

- Nextcloud HTTPS availability
- SSH service status
- Ping
- CPU temperature
- System load average
- RAM and swap usage
- Disk usage
- Docker container exits
- Power throttling flags
- SMART disk health
- Failed SSH login attempts
- Filesystem errors
- SSL certificate expiration

## Restic Backup Reports  

Status emails include:
- SUCCESS
- FAILED
- WARNING (disk usage ≥ 80%)

Reports include:
- Full backup log (attachment)
- Summary report
- Warning events (if any)

## UPS Notifications  
Events monitored:

- Power loss (AC disconnected)
- Power restoration (AC restored)
- Low-battery shutdown events
- Monthly UPS battery health report

## Fail2Ban Ban Notifications  
Ban alerts for:
- sshd (Watches SSH login attempts. Bans IPs with repeated failed logins)
- nextcloud (Watches Nextcloud logs for failed logins or abuse patterns)
- nginx-http-auth (for repeated failed basic‑auth attempts)
- nginx-botsearch (for bots probing for common paths)
- recidive (Re‑bans IPs that were banned before (repeat offenders), usually with a much longer ban time)
