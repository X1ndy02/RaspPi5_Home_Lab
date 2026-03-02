Security Controls

Fail2Ban is configured with multiple protection rules:

- sshd
- nextcloud
- nginx-http-auth
- nginx-botsearch
- recidive

These rules help prevent brute force attacks
and repeated abuse attempts.

Security is layered and monitored continuously.

=================================================================
=================================================================


Backup Strategy

Backups are handled by Restic.

Daily snapshots are stored locally on the SATA SSD (for now only there planing to 
save  them localy transfer copy to my Mac and another copy to Cloud).

Backup reports include:

- SUCCESS
- FAILED
- WARNING if disk usage exceeds 80 percent

Each report contains:
- Full backup log
- Summary report
- Warning events if any
