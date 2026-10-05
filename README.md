# Windows-User-Account-Disable-Delete-Detection-Wazuh
Investigation --  Windows User Account Disable/Delete Detection


Windows User Account Disable/Delete Detection — Wazuh

Objective

Detect and investigate Windows user-account lifecycle events using Wazuh.

Test Activity

The temporary SOC-TestUser account was subsequently removed after completing the monitoring exercise.

Remove-LocalUser -Name "SOC-TestUser"

Wazuh Detection

* Rule ID: 60111
* Level: 8
* Event ID: 4726
* Description: User account disabled or deleted
* Target Account: SOC-TestUser
* MITRE ATT&CK: T1098 T1531
* MITRE TACTIC: Persistence, Impact
* MITRE TECHNIQUE : Account Manipulation, Account access removed

Investigation

The alert was correlated with the controlled removal of the temporary test account.

The event demonstrated that Wazuh can monitor account lifecycle activity, including account deletion or disabling.

SOC Analysis

An unexpected account deletion or disabling event may require investigation because it can affect access, persistence, or incident response.

The analyst should examine:

* Account involved
* Initiating user
* Timestamp
* Event ID
* Related account-management events
* Whether the action was authorized

Key Learning

Monitoring the complete account lifecycle provides better visibility than monitoring account creation alone.

Create → Modify → Group Change → Disable/Delete

Result: Wazuh detected the account lifecycle event generated during the controlled lab exercise.
