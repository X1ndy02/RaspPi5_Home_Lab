UPS Shutdown Validation

Date:10/08/26
Shutdown threshold set to 20%

Test Scenario
AC power was manually disconnected pi is on UPS battery atm.

Observed Behaviour                           Results
- Power loss detected: Yes/No                  Yes
- Shutdown email sent: Yes/No                  Yes
- Battery percentage at shutdown:             19.8%
- Quick backup executed: Yes/No                Yes
- Docker stopped cleanly: Yes/No                
- System powered off cleanly: Yes/No           Yes

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
