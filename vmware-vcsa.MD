## VMware ESXi

Return logs for all configured ESXi server
```
{ESXi=~".+"}
```

Return all logs collected for vCSA
```
{vCSA="myvCSA"}
```

Return only warn log entries for the selected vCSA
```
{vCSA="myvCSA",severity="warn"}
```

Match a certain string in the log file of the selected vCSA
```
vCSA="myvCSA" |= "exact match for content"
```

Count all error log entries within the last 10 minutes for the selected vCSA
```
count_over_time({vCSA="myvCSA",severity="error"}[10m])
```

### Data Types specific for vCSA

DataTypes:
* vCSA_Syslog
* vSphereEvent
* vSphereTask

Query for specific datatypes for selected vCSA
{vCSA="myvCSA", DataType="vCSA_Syslog"}


