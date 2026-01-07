1. Physical security after an inventory revealed missing supplies.
    
2.  Access for remote or hybrid employees after suspected unauthorized access to Frothly's Customer Relationship Management (CRM) platform, SalesForce.
    
3. Increased alerts about file changes on Frothly workstations.

Insider Threat indicators

Login variations (increasing frequency, remote/local, odd times, etc)
<li>Logging in frequently during vacation times&nbsp;</li><li>Email and file transfers of sensitive information</li><li>Unusual outbound traffic</li><li>Increased printer usage</li><li>Export of large reports/downloads from internal systems</li>


Not all data sources may be accessible or available in Splunk, but that doesn't mean they can't provide additional context to an investigation.  

Non-technical data might be loaded into a local instance of Splunk on an investigator’s laptop for example. Correlating log data with non-technical data, like physical security violations, Acceptable Use Policy (AUP) violations, or credit card expense reports just to name a few, could provide clues that the logs alone would not.


reader_desc
This field identifies the specific badge reader the data came from. In our case, this field includes locations at Frothly headquarters, Thirsty Berner, and several other locations.

event_desc
Identifies the activity or status received from the scanning attempt. There are values for when access is granted, denied, and many other status-related values

Here's what we will start with:

|                                                                                                                                                                                                                                                                                                                                                                         |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| index=main sourcetype=st_frothly_events reader_desc=THIRSTY*  <br>```Searches for  badge activity from any of the physical readers at Thirsty Berner Brewing```  <br><br>\| stats count by reader_desc employee_first_name employee_job_title<br><br>```The "**stats count by**"creates counts of each reader + employee first name + employee job title combination``` |

index=main sourcetype=st_frothly_events reader_desc="THIRSTY_BERNER BREW SUPPLY" event_desc="Access Granted" employee_first_name="*"  
| timechart count by employee_first_name limit=10  
```The "**timechart count by**" command works like **stats**, but **timechart** will group the events into buckets of time designated by a time span.```


 To do that, we can look at an **event_desc** of "Access Denied Unauthorized Entry Level" or "Access Denied Unauthorized Time".

|                                                                                                                                                                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| index=main sourcetype=st_frothly_events event_desc="Access Denied Unauthorized Entry Level" OR event_desc="Access Denied Unauthorized Time" reader_desc="THIRSTY_BERNER BREW SUPPLY"  <br>\| stats count by reader_desc, employee_first_name employee_job_title |
|                                                                                                                                                                                                                                                                 |
