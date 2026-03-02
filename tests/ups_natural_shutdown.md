UPS Shutdown Validation

Date:10/08/26
Shutdown threshold set to 20%

Test Scenario
AC power was manually disconnected pi is on UPS battery atm.

Observed Behaviour
- Power loss detected: Yes/No
- Shutdown email sent: Yes/No
- Battery percentage at shutdown:
- Quick backup executed: Yes/No
- Docker stopped cleanly: Yes/No
- System powered off cleanly: Yes/No

Post-Restore Validation
- System boot successful: Yes/No
- Filesystem errors observed: Yes/No
- MariaDB started normally: Yes/No
- Nextcloud accessible: Yes/No
- Monitoring resumed: Yes/No

Anomalies
(Only if something unexpected happened)

Conclusion
Pass / Fail
