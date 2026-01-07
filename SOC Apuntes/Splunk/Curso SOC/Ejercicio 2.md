index=main sourcetype="cp_log" user=richards

Suppose you have IP address data in your events. In that case, you can use iplocation to look up their location information in a third-party database and generate location fields in the search results

index=main sourcetype="cp_log" user="richards"  
| iplocation src  
| where City!=""  
```Using the iplocation command with the src field where the city is **not** (!=) empty helps us remove events with an empty city.```  
| table src City Region Country lat long _time  
```The search then builds a table and deduplicates logins from the same IP address.```  
| dedup src  
| sort _time  
```Finally, all that data is sorted by time. ```


need to include that authentication data to get a complete picture

|                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| index=main source="sfdc_streaming_api_events://login_events" Username="richard@yellowtalon.co"  <br>\| iplocation src  <br>\| where City!=""  <br>\| table _time Username SourceIp City  <br>\| dedup _time  <br>\| sort -_time |

 combine our sources of authentication data and visualize it on a map. I want to show the location and the frequency logged in from each location for Richard. The **geostats** command will help with this. If you haven’t done it before, we can also easily turn this data into a map with Splunk’s visualizations and count the logins from each city.

index=main (sourcetype="cp_log" OR source="sfdc_streaming_api_events:///login_events") (user=Richards OR Username="richard@yellowtalon.com")  
| iplocation src  
| where City!=""  
| geostats count by City latfield=lat longfield=lon


Combinando todo

index=main (source="sfdc_streaming_api_events://login_events" OR sourcetype="cp_log") (Username="richard@yellowtalon.co" OR user=richards)  
| eval src=coalesce(src,SourceIp)  
| eval user=coalesce(Username, user)  
| iplocation src  
| eval State=coalesce(Region, Subdivision)  
| where City!=""  
| table _time user src City State Country  
| dedup _time  
| sort -_time