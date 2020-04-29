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

Count all error log entries within the last 10 minutes for the selected ESXi
```
count_over_time({ESXi="esxname",severity="error"}[10m])
```

### Data Types specific for VMware ESXi

DataType

* vCSA_Syslog
* vSphereEvent
* vSphereTask

Query for specific datatypes for selected ESXi; currently only ESXi_Syslog
{ESXi="esxname", DataType="ESXi_Syslog"}


