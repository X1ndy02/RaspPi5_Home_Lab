Monitoring and Alerts

The system sends alerts when something changes or fails...

To be mroe specific:

- Nextcloud becomes unreachable
- SSH service stops
- Internet ping fails
- CPU temperature exceeds safe limits
- System load spikes
- Disk usage reaches warning levels
- Docker container exits unexpectedly
- SSL certificate approaches expiration
- Multiple failed SSH login attempts detected

The goal is early detection,
not reacting after damage

==========================================================
==========================================================

Power Management

The UPS monitors:

- Power loss
- Power restoration
- Low battery level
- Monthly battery health status

If the battery level becomes too low (in my case 20%),
the system performs quick backup save and close all running services sedn smtp email and then do safe shutdown

This prevents filesystem corruption
and data loss on power loss 
