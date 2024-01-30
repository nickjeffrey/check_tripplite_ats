# check_tripplite_ats
nagios check for Tripp-Lite Automatic Transfer Switch (ATS)

# Requirements
perl and SNMP on nagios server, enable SNMP on Tripp-Lite Automatic Transfer Switch

# Configuration

You will need a section in the services.cfg file on the nagios server that looks similar to the following.
```
# Define a service to check the Tripp-Lite Automatic Transfer Switch (ATS)
# Parameters are SNMP community name
define service {
        use                             generic-service
        hostgroup_name                  all_tripplite_ats
        service_description             ATS health
        check_command                   check_tripplite_ats!public
        }
```

You will need a section in the commands.cfg file on the nagios server that looks similar to the following.
```
# 'check_tripplite_ats' command definition for ATS (Automatic Transfer Switch)
# parameters are -H hostname -C snmp_community
define command{
        command_name    check_tripplite_ats
        command_line    $USER1$/check_tripplite_ats -H $HOSTADDRESS$ -C $ARG1$
        }
```

On the Tripp-Lite ATS, enable SNMP protocol
<img src=images/ats_enable_snmp.png>

On the Tripp-Lite ATS, enable SNMP community string
<img src=images/ats_enable_snmp_users.png>

On the Tripp-Lite ATS, enable syslog and send to nagios server (not used by this check, but useful for troubleshooting)
<img src=images/ats_enable_syslog.png>

On the Tripp-Lite ATS, enable SMTP server for sending email alerts (not used by this check, but useful for troubleshooting)
<img src=images/ats_enable_smtp.png>

On the Tripp-Lite ATS, define email alert recipients (not used by this check, but useful for troubleshooting)
<img src=images/ats_enable_email_alerts.png>

# Output

You will see output similar to the following:
```
Tripp-Lite ATS OK - Model:TRIPP LITE PDUMH15HVAT,  Power input sources:2,  Alarm state:none
```




