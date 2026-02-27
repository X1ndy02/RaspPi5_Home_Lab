# RaspPi5_Home_Lab
Self-hosted Raspberry Pi 5 homelab

##Overview
This is just simple backtraking on what I have build and done with my Pi5

## Purpose
To learn and experiment in enviroment that has been designed and build from scratech by me 

============================================================================================

As of 27/02/26

## Hardware

# Core System
- Raspberry Pi 5 Model B (16GB RAM)
- 52Pi Ultra Thin ICE Tower Cooler
# Primary Storage (Boot Drive)
- Kingston 500GB NVMe SSD  
  - Connected via Geekworm X1001 PCIe to M.2 adapter  
  - Linked using Geekworm Raspberry Pi 5 PCIe FFC Cable (50mm)  
  - Mounted in an elevated position using M2.5 hex brass spacers (standoffs) to improve airflow and clearance
# Power Backup
- Geekworm X1201 2-Cell 18650 5.1V 5A UPS Shield  
  - 2 × Molicel M35A 18650 (3500mAh, 10A) batteries
# Secondary Storage
- Geekworm X1100 2.5" SATA HDD/SSD Shield  
- Kingston 240GB SATA SSD

# System Monitoring Display
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
    - Network latency (ping)
    - Thermal throttling state
      
===========================================================================================================================
===========================================================================================================================

## Sofwtare and Services Running

## Containerized Services (Docker)
# Nextcloud Stack
- Nextcloud Application (nextcloud:29-apache)
- MariaDB Database (mariadb:11.4)
- Redis Cache (redis:7-alpine)
- Nginx Reverse Proxy (nginx:alpine)
- ClamAV Scanner (mkodockx/docker-clamav)
# Monitoring Stack
- Prometheus (prom/prometheus)
- Node Exporter (prom/node-exporter)
- Grafana (grafana/grafana-oss)
- Grafana Image Renderer (grafana/grafana-image-renderer)

# Host-Level Services (Manually Installed)
# Container Runtime
- Docker Engine (docker.io)
- Docker Compose
# Remote Access & Network
- SSH Server
- ZeroTier VPN
# Security & Protection
- Fail2Ban
- ClamAV mirror tooling (clamav-cvdupdate)
# Backup & Recovery
- Restic
- restic-backup.service
- Rsync
# Monitoring & Health
- SMART disk monitoring (smartmontools)
- pi-monitor.service
- rp2350-stats.service
# Power Management
- x120x-ups notification and shutdown services
# Alerting
- msmtp / msmtp-mta
- bsd-mailx
- rp2350-stats.service — Sends Raspberry Pi system statistics to RP2350 LCD dashboard.
# Power Management (UPS Integration)
- x120x-ups-notify.service — Sends email alerts on UPS power loss.
- x120x-ups-shutdown.service — Safely shuts down system when UPS battery is low.
