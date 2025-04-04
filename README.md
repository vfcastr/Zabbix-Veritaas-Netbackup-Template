# Zabbix-Veritas-Netbackup-Template

## Description

Template created to collect failed jobs via Zabbix using the NetBackup API, without the need for external scripts.

## Overview

The data collection works as follows:
The master item is used to connect to the API using a script-type item that retrieves failed jobs from the last 12 hours. The script identifies the job name and, within the same execution, checks if there is a job of the same type that was executed successfully.

If not, the final JSON is populated with failure information. If a job with a later startTime than the endTime of the failed job is found, the JSON is updated with success information. This ensures that Zabbix is able to automatically resolve the problem that was previously triggered.
```
- Job failed
- Clear problem if a successful job run is detected
```

Another feature of the template is the collection of Disk Pool data:
```
- Available Space (Bytes)
- Name
- Raw Size (Bytes)
- Read-Only Status
- State
- Storage Server Name
- Type
- Usable Size
- Used Capacity
- Used Capacity (%)
```

## Diagram
![Template][def]


[def]: Image/Netbackup-diagram.jpg
