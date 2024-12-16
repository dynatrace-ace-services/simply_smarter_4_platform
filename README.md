# Simply smarter - Data Layer Overview 

Dashboard 
- [Download](https://raw.githubusercontent.com/dynatrace-ace-services/segment/refs/heads/main/_OverviewWithSegment-Web_Service_Process_Host_0.1.json)  v0.1
- [Demo live](https://guu84124.apps.dynatrace.com/ui/document/v0/#share=ae79d902-051f-427b-93cf-78938b0bddd8) (internal access)  
(for demo live there is no segment with web application entities, you can use this one `host_group` / `google_cloud`)

Based on segment, this dashboard displays 
- Application / Key User Action / Synthetic 
- Service
- K8s
- Process Group
- Host

![image](https://github.com/user-attachments/assets/3dba6418-a13b-465b-b3a2-4e8298b07371)


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


