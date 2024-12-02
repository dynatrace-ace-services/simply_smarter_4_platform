# Overview Dashboard with segment

## Legacy project

Dashboard 
- [Download](https://raw.githubusercontent.com/dynatrace-ace-services/segment/refs/heads/main/_OverviewWithSegment-Web_Service_Process_Host.json?token=GHSAT0AAAAAACWJKLTPDLOXFKR7ABJLQGT2Z2N5SWA)
- [Demo live](https://guu84124.apps.dynatrace.com/ui/document/v0/#share=fbf50a53-b913-4a32-980f-52488a9c8fc0)  
(for demo live there is no segment with web application entities, you can use this one `host_group` / `google_cloud`)

Based on segment, this dashboard displays 
- Application based only on the satus (Preview metric is coming soon ... ) 
- Service
- Process Group
- Host

![image](https://github.com/user-attachments/assets/d42d76ef-6536-4802-9768-3b5bd82ca9c9)


The status is 
- red if there is at least one problem is open
- orange if there is at least one problem closed - and no problem open
- green if there is no problem

Drilldown 
- on the entity (new app or classic view)
- on the most recent problem  

![image](https://github.com/user-attachments/assets/ed780cb7-9822-475f-8eb5-66e5a4685899)


Configure the segment,
- the variable based on the key `app` (need to be adapt to your context)

![image](https://github.com/user-attachments/assets/80c3e461-5af9-44c0-9c2b-0a19c02f101c)

```
fetch dt.entity.process_group
| expand  tags
| filter matchesPhrase(tags,"app")
| dedup tags
| fields tags
| sort tags asc
```


- the entities

![image](https://github.com/user-attachments/assets/e93af1b2-fb1b-4dbf-b58e-20f4ba920a7e)

## Cloud Native project

- coming soon
