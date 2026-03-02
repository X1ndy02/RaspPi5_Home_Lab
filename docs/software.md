Software and Services

The system runs on Raspberry Pi OS with Docker.

Core Services

Nextcloud Stack
- Nextcloud
- MariaDB
- Redis
- Nginx reverse proxy
- ClamAV antivirus scanning

Monitoring Stack
- Prometheus (collects system metrics)
- Node Exporter (exposes system metrics)
- Grafana (dashboard and visualization)
- Grafana Image Renderer (used for reports)

System-Level Services

Docker Engine and Docker Compose
Used to manage containers cleanly.

ZeroTier VPN
Allows secure remote access from anywhere using VN.

Fail2Ban
Blocks repeated failed login attempts.

Restic
Automated daily backups(snapshots) stored on the SATA SSD.

SMART Monitoring
Tracks disk health and reports issues.

Custom Services
- pi-monitor.service
- rp2350-stats.service
- UPS notification service
- UPS safe shutdown service

Email Alerts
- msmtp is used to send system and status emails to private seprate email created solely fro notifications from Pi5.

The system is designed so that if something fails,
I know immediately....
