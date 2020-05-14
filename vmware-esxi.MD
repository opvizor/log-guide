## VMware ESXi

Return logs for all configured ESXi server
```
{ESXi=~".+"}
```

Return all logs collected for ESXi hosts in the selected cluster
```
{Cluster="clustername"}
```

Return only warn log entries for the selected ESXi
```
{ESXi="esxname",severity="warn"}
```

Match a certain string in the log file of the selected ESXi
```
{ESXi="esxname"} |= "exact match for content"
```

Count all error log entries within last 10 minutes for the selected ESXi
```
count_over_time({ESXi="esxname",severity="error"}[10m])
```

Count and sum all log entries within the timeframe for every minute 1 minute grouped by ESXi hosts
```
sum(count_over_time({ESXi=~".+", DataType="ESXi_Syslog"}[1m])) by (ESXi)
```

### Data Types specific for VMware ESXi

DataType

* ESXi_Syslog
* vSphereEvent
* vSphereTask

Query for specific datatypes for selected ESXi

Log:
```
{ESXi="esxname", DataType="ESXi_Syslog"}
```

Event:
```
{ESXi="esxname", DataType="vSphereEvent"}
```

Task:
```
{ESXi="esxname", DataType="vSphereEvent"}
```

### Storage related examples:

#### Performance
*Explore:*
```
{ESXi=~".+"}|="performance has"
```

*Dashboard:*
```
sum(count_over_time({ESXi=~".+"}|="performance has"[1m]))
```

#### SCSI Messages
*Explore:*
```
{ESXi=~".+"} |~ "SCSI|NMP|ScsiDeviceIO|scsiCorrelator|vmk-iscsi|iscsi|iscsiCorrelator" != "SNMP"
```

*Dashboard:*
```
sum(count_over_time({ESXi=~".+"} |~ "SCSI|NMP|ScsiDeviceIO|scsiCorrelator|vmk-iscsi|iscsi|iscsiCorrelator" != "SNMP"[1m]))
```

#### SCSI Sense Codes

*Explore:*
```
{ESXi=~".+"}|="Valid sense data"
```


*Dashboard:*
```
sum(count_over_time({ESXi=~".+"}|="Valid sense data"[1m]))
```
